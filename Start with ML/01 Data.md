![data](52.png)

+ The machine learning process starts with collecting and processing training data. Bad data is often called _garbage in, garbage out_
+ There are a several different types of data used in training an ML model. First, it's important to know the difference between labeled and unlabeled data.
#### Labeled data
+ It is a dataset where each instance or example is accompanied by a label or target variable that represents the desired output or classification
+ **Example**: In an image classification task, labeled data would consist of images along with their corresponding class labels (for example, cat, dog, car).
#### Unlabeled data
+ it is a dataset where the instances or examples do not have any associated labels or target variables.
+ **Example**: A collection of images without any labels or annotations
+ The main types of data used in training are structured and unstructured data. They come with various subtypes, which you can find by expanding the following categories.
#### Structured data
+ Structured data refers to data that is organized and formatted in a predefined manner, typically in the form of tables or databases with rows and columns. This type of data is suitable for traditional machine learning algorithms that require well-defined features and labels. The following are types of structured data.
+ **Tabular data**: This includes data stored in spreadsheets, databases, or CSV files, with rows representing instances and columns representing features or attributes.
+ **Time-series data**: This type of data consists of sequences of values measured at successive points in time, such as stock prices, sensor readings, or weather data.
#### Unstructured data 
+ Unstructured data
Unstructured data is data that lacks a predefined structure or format, such as text, images, audio, and video. This type of data requires more advanced machine learning techniques to extract meaningful patterns and insights.
+ **Text data**: This includes documents, articles, social media posts, and other textual data.
+ **Image data**: This includes digital images, photographs, and video frames.
+ The compiled training data is fed into machine learning algorithms. The ML learning process is traditionally divided into three broad categories: supervised learning, unsupervised learning, and reinforcement learning.
#### supervised learning
+ In supervised learning, the algorithms are trained on labeled data. The goal is to learn a mapping function that can predict the output for new, unseen input data.
#### Unsupervised learning
+ refers to algorithms that learn from unlabeled data. The goal is to discover inherent patterns, structures, or relationships within the input data.
#### reinforcement learning
+ In reinforcement learning, the machine is given only a performance score as guidance and semi-supervised learning, where only a portion of training data is labeled. Feedback is provided in the form of rewards or penalties for its actions, and the machine learns from this feedback to improve its decision-making over time.
### Inferencing
+ After the model has been trained, it is time to begin the process of using the information that a model has learned to make predictions or decisions. This is called inferencing.
+ There are two main types of inferencing in machine learning: batch inferencing and real-time inferencing.
#### Batch inferencing
+ Batch inferencing is when the computer takes a large amount of data, such as images or text, and analyzes it all at once to provide a set of results. This type of inferencing is often used for tasks like data analysis, where the speed of the decision-making process is not as crucial as the accuracy of the results.
#### Real-time inferencing
+ Real-time inferencing is when the computer has to make decisions quickly, in response to new information as it comes in. This is important for applications where immediate decision-making is critical, such as in chatbots or self-driving cars. The computer has to process the incoming data and make a decision almost instantaneously, without taking the time to analyze a large dataset.
