### Reading File in Pyspark
+ Let's talk about different way to read csv file.
+ Assuming 'spark' is an active SparkSession
```
csv_file_path = "/path/to/your/data.csv"

df = spark.read.csv(
    path=csv_file_path,
    header=True,       # Treat the first line as column names
    inferSchema=True,  # Automatically determine column data types (use only for small files!)
    sep=','            # Specify the delimiter (e.g., ',' for CSV, '\t' for TSV)
)

df.printSchema()
df.show(5)
```
+ Anther method
```
df = spark.read.format("csv") \
    .option("header", "true") \
    .option("inferSchema", "true") \
    .load("/path/to/your/data.csv")
```
> [!Note]
> inferSchema = true means Spark will determine types automatically.
> you can use when dataset is small or when we don't want to wrtie schema for datafame.

### InferSchema? 
+ The inferSchema option (when set to True) tells Spark to perform the following two distinct passes over the data when reading a file (like a CSV or JSON):

1. First Pass (Schema Inference): Spark scans a sample of the data to guess the data type for each column (e.g., is this column an IntegerType, DoubleType, or StringType?).

2. Second Pass (Actual Data Reading): Spark reads the entire dataset again, using the schema determined in the first pass to load the data into the DataFrame.

> [!important]
> Setting inferSchema to False is a major optimization because it eliminates the first pass over the data.

```
from pyspark.sql.types import StructType, StructField, IntegerType, StringType

# Define the structure and data types
manual_schema = StructType([
    StructField("col1_name", StringType(), True),
    StructField("col2_name", IntegerType(), False), # e.g., Not nullable
])
# Assuming 'spark' is an active SparkSession
csv_file_path = "/path/to/your/large_data.csv"

df_optimized = spark.read.csv(
    path=csv_file_path,
    header=True,
    inferSchema=False, # We are NOT inferring...
    schema=manual_schema # ...because we are PROVIDING the schema here
)

# PySpark now performs only ONE read pass, using the manual_schema
df_optimized.printSchema()
```
### Why PySpark Doesn't Need the Second Pass

+ When you provide the schema via the schema option:

+ Preparation: Spark's Catalyst Optimizer receives the complete and verified blueprint (manual_schema) before starting I/O operations.
+ Single Pass: When the worker nodes start reading the raw CSV data, they immediately know:
  - Where each column starts and ends (based on the delimiter).
  - Exactly what data type to expect for that column (e.g., this is an Integer, this is a String).
  - How to correctly parse and encode the raw bytes into the internal, efficient binary format(Tungsten/UnsafeRow) for that specific data type.

### 1. File-Based Data Ingestion Methods

| **Data Type** | **Best Method (PySpark Code)** | **Key Best Practice & Rationale** |
| :--- | :--- | :--- |
| **Parquet / ORC** | `spark.read.parquet("path/")` | **Highest performance.** These formats are columnar and include schema, eliminating the need for `inferSchema`. |
| **CSV / TSV** | `spark.read.csv("path/", ...)` | **Crucial Optimization:** Set `inferSchema=False` and **provide an explicit schema** (`schema=StructType(...)`). This avoids the two-pass read. |
| **JSON (Newline)** | `spark.read.json("path/")` | Provide a manual schema to prevent slow inference, especially with complex nested JSON structures. |
| **Text Files** | `spark.read.text("path/")` | Loads files as a DataFrame with a single `value` column (string). Use only for unstructured text. |

# 2. External Database Ingestion Methods (JDBC/ODBC)
+ For relational databases, the Java Database Connectivity (JDBC) method is the standard way to parallelize the read operation.
```
df = spark.read.jdbc(
    url=jdbc_url,
    table=db_table_name,
    properties={"user": user, "password": password},
    partitionColumn="id", # Column to partition on
    numPartitions=10      # Number of parallel reads
)
```
| **Data Type** | **Best Method (PySpark Code)** | **Key Best Practice & Rationale** |
| :--- | :--- | :--- |
| **SQL Databases (Postgres, MySQL, etc.)** | `spark.read.jdbc(...)` | **Parallelize the read** using `partitionColumn`, `lowerBound`, `upperBound`, and `numPartitions` to distribute the load across multiple executors. |

# 3. Streaming Data Ingestion Methods

+ For data that arrives continuously (like from Kafka or Kinesis), you use the StructuredStreaming API.
| **Data Type** | **Best Method (PySpark Code)** | **Key Best Practice & Rationale** |
| :--- | :--- | :--- |
| **Kafka / Kinesis** | `spark.readStream.format("kafka").load()` | Use the dedicated `readStream` API. **Explicitly define the schema** for the message payload (the `value` column) for structured processing. |

# 4. Converting Existing In-Memory Data

+ These methods are used to convert non-Spark data structures into an optimized PySpark DataFrame.
| **Data Type** | **Best Method (PySpark Code)** | **Key Best Practice & Rationale** |
| :--- | :--- | :--- |
| **Pandas DataFrame** | `spark.createDataFrame(pandas_df)` | **Most efficient bridge.** Preferred for converting smaller data (that fits on the driver node) already loaded in memory. |
| **Python Lists/Dicts** | `spark.createDataFrame(data_list, schema=manual_schema)` | Best for small collections. Always define a schema for clean, predictable column typing. |
