### AWS Compute Offerings
+ **Different Compute services offered by AWS.**
+ **Amazon EC2** - Virtual Servers in the Cloud
+ **Amazon EC2** Container Service - Run and Manage Docker Containers
+ **AWS Lambda** - Run Code in Response to Events
+ **Amazon EC2 Container Registry** - Store and Retrieve Docker Images
+ **Amazon Lightsail** - Launch and Manage Virtual Private Servers
+ **Amazon VPC** - Isolated Cloud Resources
+ **AWS Batch** - Run Batch Jobs at Any Scale
+ **AWS Elastic Beanstalk** - Run and Manage Web Apps
+ **Auto Scaling** - Automatic Elasticity

AWS offers a diverse range of compute services, each optimized for different workloads, operational models, and levels of control. The primary services can be categorized into **Virtual Servers**, **Containers**, and **Serverless Computing**.

***

### 1. Virtual Servers (IaaS)

#### **Amazon Elastic Compute Cloud (EC2)**

**What it is:** A web service providing secure, resizable compute capacity (virtual servers, called instances) in the cloud. It's the foundational Infrastructure as a Service (IaaS) offering.

**Distinguishing Points:**
* **Maximum Control:** You have **full administrative control** over the operating system (OS) and all installed software. You manage patching, security, and scaling logic.
* **Persistent & Customizable:** Ideal for applications requiring **long-running, persistent instances**, specific OS configurations (Windows, Linux, macOS), or specialized hardware (GPU, HPC).
* **Billing:** You pay by the second/hour for the instance while it's running. Offers various pricing models: **On-Demand**, **Reserved Instances** (RI), and **Spot Instances** (for cost savings on interruptible workloads).

##### Applications
+ Big data - e.g. Hadoop
+ Database software - e.g. Aurora, DynamoDB
+ Enterprise applications - e.g. SAP, Oracle
+ Migrations from on-premises environments
+ Open-source cluster management

---

#### **Amazon Lightsail**

**What it is:** An easy-to-use cloud platform providing everything needed to launch a simple application or website, including virtual servers, storage, and networking, for a low, predictable monthly price.

**Distinguishing Points:**
* **Simplicity & Predictability:** Designed for users who want a **simple, all-in-one Virtual Private Server (VPS)** experience with **fixed pricing**.
* **Low Management:** Less complex than EC2; good for basic websites, blogs, and simple web applications.
* **Use Case:** Excellent choice for personal projects, small businesses, and developers who need a quick, affordable, and easy-to-manage virtual machine.

***

### 2. Container Services

#### **Amazon Elastic Container Service (ECS)**

**What it is:** A fully managed container orchestration service that makes it easy to deploy, manage, and scale Docker container applications.

**Distinguishing Points:**
* **AWS-Native Orchestration:** It's an **AWS-proprietary** orchestrator. Simpler to set up than EKS if you are already invested in the AWS ecosystem and don't require Kubernetes portability.
* **Flexible Compute Options:** You can run containers on **EC2 instances** (managing the instances yourself) or on **AWS Fargate** (serverless containers).

#### Applications
+ Web applications
+ Microservices
+ Batch jobs
+ Docker workloads
---

#### **Amazon Elastic Kubernetes Service (EKS)**

**What it is:** A fully managed service that allows you to run Kubernetes on AWS without needing to install, operate, and maintain your own Kubernetes control plane.

**Distinguishing Points:**
* **Managed Kubernetes:** Provides a managed control plane for the **industry-standard Kubernetes** orchestration tool, offering portability and a large community.
* **Kubernetes Compatibility:** Best choice if your application requires **Kubernetes features** or you need to maintain consistency with on-premises or other cloud Kubernetes deployments.
* **Flexible Compute Options:** Also runs containers on **EC2 instances** or **AWS Fargate** (serverless containers).

---

#### **AWS Fargate**

**What it is:** A serverless compute engine for containers that works with both **ECS** and **EKS**. It removes the need to provision, configure, or scale clusters of virtual machines to run containers.

**Distinguishing Points:**
* **Serverless Containers:** The key difference is the **elimination of server/cluster management**. You define your container's CPU and memory needs, and Fargate runs it.
* **Operational Overhead:** **Lowest operational overhead** for containers; you only focus on the container image and task definitions.
* **Pricing:** Pay for the compute resources (vCPU and memory) consumed by your containerized application.

***

### 3. Serverless Computing (FaaS & PaaS)

#### **AWS Lambda**

**What it is:** A **serverless compute service** that lets you run code without provisioning or managing servers. It executes your code only when needed and scales automatically.

**Distinguishing Points:**
* **Function as a Service (FaaS):** Ideal for **event-driven workloads** and **short-running functions** (max 15 minutes). You upload your code, and Lambda runs it in response to events (e.g., S3 object upload, API Gateway request).
* **Pay-per-Execution:** Billed based on the number of requests and the **compute time consumed in milliseconds**. Zero cost when the code isn't running.
* **No Server Management:** **Highest level of abstraction**—you manage only the code; AWS manages all infrastructure, OS, and scaling.

---

#### **AWS Elastic Beanstalk**

**What it is:** An easy-to-use Platform as a Service (PaaS) for deploying and scaling web applications and services developed with popular languages and frameworks.

**Distinguishing Points:**
* **Simplified Deployment (PaaS):** It handles the infrastructure provisioning (EC2, Load Balancing, Auto Scaling) for your application automatically. You **upload your code**, and it manages the rest.
* **Focus on Code:** Great for developers who want to **deploy full web applications quickly** without getting into the complexities of configuring EC2 or the other components.
* **Underlying Resources:** Uses **EC2 instances** under the hood, but the management of those instances is highly automated by Beanstalk.

---

#### **AWS App Runner**

**What it is:** A fully managed service for developers to quickly deploy containerized web applications and APIs, at scale and with minimal infrastructure experience.

**Distinguishing Points:**
* **Simplified Container PaaS:** A fully managed, **container-aware PaaS** that is simpler than EKS or ECS/Fargate for pure web applications/APIs.
* **Source Code or Container Image:** Can start from **source code** (it builds the image) or an **existing container image**.
* **Automatic Deployment & Scaling:** Provides built-in load balancing, automatic scaling, and continuous deployment from a code repository. **Ideal for simple web services.**

***

### 4. Specialized Compute Services

#### **AWS Batch**

**What it is:** A service that enables developers, scientists, and engineers to easily and efficiently run **hundreds of thousands of batch computing jobs** on AWS.

**Distinguishing Points:**
* **Batch Workloads:** Specifically for **high-volume, often parallelizable, offline processing** jobs (e.g., ETL, financial modeling, machine learning inference).
* **Managed Job Scheduling:** Handles capacity provisioning, job scheduling, resource dependency resolution, and scaling of compute resources (EC2 or Fargate).
* **Difference:** Unlike EC2/Lambda/Containers for continuous or event-driven tasks, AWS Batch is for **discrete, queue-based jobs** that run to completion.

---

#### **AWS Outposts**

**What it is:** A family of fully managed solutions that extend AWS infrastructure, AWS services, APIs, and tools to virtually any customer data center, co-location space, or on-premises facility.

**Distinguishing Points:**
* **Hybrid Cloud/On-Premises:** This is for customers who need to run compute **on-premises** due to low-latency requirements or local data processing needs, while using the same AWS tools and APIs.
* **Physical Hardware:** AWS ships and installs **physical hardware racks** in your facility.
* **Difference:** All other services run *in* AWS Regions; Outposts runs *in your data center* but is managed *by* AWS as part of the AWS Region.

***

#### Compute Service Comparison at a Glance

| Service | Abstraction/Control | Workload Type | Key Differentiator |
| :--- | :--- | :--- | :--- |
| **Amazon EC2** | Low (High Control) | Persistent, traditional applications, custom OS/hardware. | **Full control** over OS, instance type, and infrastructure. |
| **AWS Lambda** | Very High (Low Control) | Event-driven functions, ephemeral tasks. | **Serverless FaaS**; pay-per-millisecond; no server management. |
| **AWS Fargate** | High (Low Control) | Containerized applications. | **Serverless container engine**; runs containers without managing EC2 instances. |
| **Amazon ECS** | Medium | Container orchestration (AWS-native). | Managed container orchestrator, good for deep AWS integration. |
| **Amazon EKS** | Medium | Container orchestration (Kubernetes). | Managed **Kubernetes** control plane; industry standard, portable. |
| **Elastic Beanstalk** | Medium (PaaS) | Web applications/APIs. | **Automates full-stack deployment** of popular application environments (PaaS). |
| **AWS Batch** | Medium | Large-scale batch jobs. | **Managed job scheduling** and resource provisioning for compute-intensive tasks. |
| **Amazon Lightsail** | Low-Medium (VPS) | Simple websites, basic applications. | **Simplified, fixed-price VPS**; easy start for simple needs. |
