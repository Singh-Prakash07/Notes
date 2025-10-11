### Installing Locally

+ To install spark you must first install JDK(Java Development kit). 
+ Apache Spark 4 is only compatible with Java 17 or 21.
> [!NOTE]
> + if You have multiple java installed in your system
> + `sudo update-alternatives --config java` in cmd print index wise all java version
> + write index in number and press enter to choose which java version you want to default.

+ Furthermore, Spark is not compatible with Python 3.12 or newer as of this writing.
+ Now create an python virtual environment and install pyspark `pip install pyspark`.
+ Now you are ready to go. 

### Spark offers
1. Spark Database and SQL
2. Spark DataFrame and API

> [!Note]
> A DataFrame and a Table are two distinct ways to interact with structured data in a data processing system like Apache Spark.

### Apache Spark's Data and SQL Offerings

Apache Spark is a unified analytics engine designed for large-scale data processing. It provides powerful APIs for interacting with structured and unstructured data, with a strong focus on performance and ease of use.

### 1. Spark SQL and the Database Interface

Spark SQL is a Spark module for working with structured data. It provides two primary ways to interact with data:

1 **DataFrame and Dataset APIs:** These are high-level, language-integrated APIs that allow you to programmatically build data transformations. They are the most common way to use Spark for data processing.
2 **SQL Interface:** Spark SQL allows you to write standard SQL queries against your data. It supports a wide range of SQL features, including joins, aggregations, and subqueries.

### Key Concepts:

* **SparkSession:** This is the entry point to all Spark SQL functionality. It is used to create DataFrames, execute SQL queries, and manage the Spark application.
* **Catalyst Optimizer:** This is the core of Spark SQL's performance. It is a query optimizer that automatically generates a highly efficient execution plan for your code and SQL queries. This is why Spark's DataFrame API and SQL interface are so fast.
* **Schema Inference:** Spark can automatically infer the schema of a dataset (e.g., column names and data types) from a variety of data sources like Parquet, JSON, and CSV.

### 2. DataFrames

A **DataFrame** is a distributed collection of data organized into named columns. Conceptually, it is similar to a table in a relational database or a DataFrame in R/Python, but with optimizations for working with massive datasets across a cluster.

### Key Features:

* **Distributed:** DataFrames are spread across multiple nodes in a cluster, allowing for parallel processing.
* **Lazy Evaluation:** Operations on DataFrames are not executed immediately. Instead, Spark builds a logical plan (a Directed Acyclic Graph or DAG) of the transformations. The actual computation only happens when an action (e.g., `show()`, `count()`, `collect()`) is called.
* **Optimized Performance:** The Catalyst Optimizer analyzes the DataFrame's logical plan and optimizes it for performance, a process known as "query optimization."

### Common DataFrame Operations:

* **Transformations:** These are operations that create a new DataFrame from an existing one. They are lazy and do not trigger computation.
    * `select()`: Selects a set of columns.
    * `filter()`/`where()`: Filters rows based on a condition.
    * `groupBy()`: Groups rows by one or more columns for aggregation.
    * `join()`: Combines two DataFrames based on a shared key.
* **Actions:** These are operations that trigger computation and return a result to the driver program.
    * `show()`: Displays the contents of the DataFrame.
    * `count()`: Returns the number of rows.
    * `collect()`: Returns all the rows as a list of `Row` objects to the driver program. (Use with caution on large datasets).
    * `write()`: Writes the DataFrame to a file or database.

## 3. The APIs: DataFrame vs. RDD

Spark offers different APIs, but for most use cases, the **DataFrame API** is the recommended choice.

### DataFrame API

* **Structured and Schema-Aware:** DataFrames have a defined schema, which allows Spark to optimize performance and perform type-checking.
* **High-Level:** The API is more declarative and easier to use, abstracting away low-level details.
* **More Efficient:** The Catalyst Optimizer can perform significant optimizations on DataFrames that are not possible with RDDs.

### RDD (Resilient Distributed Dataset) API

* **Low-Level:** RDDs are the fundamental data structure in Spark, representing a low-level collection of elements.
* **Type-Agnostic:** RDDs do not have a schema. This makes them less efficient for structured data but flexible for unstructured data.
* **No Built-in Optimizer:** Spark cannot optimize RDD transformations as efficiently as it can for DataFrames.

**Conclusion:** For most modern Spark applications, especially with structured data, the **DataFrame API** and **Spark SQL** are the go-to tools. They offer the best balance of performance, ease of use, and readability. The RDD API is reserved for highly specialized use cases that require manual control over the data distribution and processing.

# Apache Spark Data Structures: DataFrame vs. Spark Table

This note provides a comprehensive comparison between **Spark DataFrames** and **Spark Tables**, which are two fundamental ways to work with structured data in Apache Spark and Spark SQL. While they represent the same data, their functionality and primary use cases differ.

---

## 1. Spark DataFrame

A **DataFrame** is the primary programming abstraction in Spark SQL. It is an **in-memory, code-centric** representation of structured data.

* **Nature:** A distributed collection of data organized into named columns, analogous to a table in a relational database or a DataFrame in R/Python.
* **Storage:** Does **not** store data; it only holds the **schema** and the **plan** (the sequence of transformations) needed to compute the data when an action is called.
* **Focus:** **Programming and Transformation**. DataFrames are manipulated using code-based APIs (Scala, Python/PySpark, R, Java).

### Key Characteristics:

| Characteristic | Description |
| :--- | :--- |
| **Persistence** | **Non-Persistent (Temporary).** It exists only for the duration of the Spark application or the session in which it was created. |
| **Access** | Accessed via code API variables (e.g., `df_orders.select(...)`). |
| **Scope** | **Local (Session-Scoped).** Only available within the single `SparkSession` that created it. |
| **Optimization** | Fully optimized by the **Catalyst Optimizer** and the **Tungsten execution engine**. |

---

## 2. Spark Table

A **Spark Table** (also known as a **Managed Table** or **External Table**) is a **persistent, metadata-centric** representation of structured data.

* **Nature:** A registered entity within Spark's **Metastore** (a service like Hive Metastore or a managed service like AWS Glue). It is an abstract layer over data files stored in a location (like HDFS or S3).
* **Storage:** The table's data files (Parquet, ORC, etc.) are stored permanently on disk/cloud storage. The **Metastore** stores the table's **metadata** (schema, location, partitioning information).
* **Focus:** **Data Organization and Querying**. Tables are queried using declarative SQL.

### Key Characteristics:

| Characteristic | Description |
| :--- | :--- |
| **Persistence** | **Persistent.** The table metadata and the underlying data files remain after the Spark application ends. |
| **Access** | Accessed via SQL (e.g., `SELECT * FROM sales_data`). |
| **Scope** | **Global (Cluster-Scoped).** Can be accessed by any Spark application that connects to the same Metastore. |
| **Types** | **Managed:** Spark controls the data and metadata. **External:** Spark only controls the metadata; a user/external process controls the data location. |

---

## 3. Comparison Table

| Feature | Spark DataFrame | Spark Table(SQL Table) |
| :--- | :--- | :--- |
| **Primary Use**| Data transformation, ETL/ELT pipelines, programmatic data analysis. | Persistent data storage, SQL querying, sharing data across applications. |
| **Nature** | **In-memory** abstraction. | **Persistent** metadata abstraction over stored files. |
| **Creation Method** | Via programmatic code (e.g., `spark.read.csv()`, `df.groupBy()`). | Via **SQL** (`CREATE TABLE ...`) or DataFrame action (`df.write.saveAsTable()`). |
| **Persistence** | **Temporary**. Exists only in the `SparkSession`. | **Permanent**. Metadata and data persist across sessions. |
| **Access Method** | Variables and programmatic API calls. | SQL queries (`SELECT`, `INSERT`, `UPDATE`). |
| **Scope** | **Local** to the specific `SparkSession`. | **Global** across the cluster/environment (via Metastore). |
| **Metastore Entry** | No entry (unless registered as a *Temporary View*). | **Required** entry (Metadata stored here). |
| **Analogy** | A temporary **view** or computed result in a database. | A fundamental, persistent **table** in a database. |
