



## 1. Why move to the Cloud? (Cloud Computing Benefits)
First, we need to convince them to stop using physical servers.
- **Trade Capital Expense for Variable Expense:** Instead of investing heavily upfront (CapEx) in data centers and servers before knowing how they'll use them, they only pay for what they consume (Variable Expense).
- **Stop Guessing Capacity:** In the cloud, they can access as much or as little as they need, scaling up and down instantly. No more paying for idle resources.
- **Increase Speed and Agility:** IT resources are just a click away. They can reduce the time to make resources available from weeks to minutes.
- **Focus on Business:** Stop spending money on "undifferentiated heavy lifting" like racking, stacking, and powering servers. Focus on customers instead.

## 2. Service Models: How much control do they need?
Depending on how much the company wants to manage:
- **IaaS (Infrastructure as a Service):** We use **EC2**. Gives them basic building blocks (networking, computers, storage). Highest flexibility, but they manage the OS.
- **PaaS (Platform as a Service):** We use **Elastic Beanstalk**. AWS manages the underlying infrastructure (OS, patching), and the company just focuses on deploying their apps.
- **SaaS (Software as a Service):** Completed products run by the provider (like email or CRM). No infrastructure worries at all.



## 3. Security & Access (IAM & Organizations)
Security is the top priority.
- **IAM (Identity and Access Management):** We use this to control access. It is free.
  - **Users:** Create individual users (don't share accounts).
  - **Groups:** Organize users with identical authorization (e.g., "Developers").
  - **Roles:** For temporary access to services or users.
  - **MFA:** Enable Multi-Factor Authentication for extra security (password + unique code).
- **AWS Organizations:** If the company has multiple departments, we use this for consolidated billing and to group accounts into Organizational Units (OUs).

## 4. Networking (The Private Cloud)
- **Regions & AZs:** Choose a Region close to customers for low latency. Use multiple **Availability Zones (AZs)** so if one data center fails, the app stays online.
- **VPC (Virtual Private Cloud):** We provision a logically isolated section of the cloud for them.
  - **Subnets:** Public subnets for web servers (internet access), Private subnets for databases (security).
  - **Security Groups:** Act as a firewall at the **instance** level.
  - **NACLs:** Act as a firewall at the **subnet** level.
- **Gateways:**
  - **Internet Gateway:** To allow communication between the VPC and the internet.
  - **NAT Gateway:** To let private instances connect to the internet (for updates) without letting the internet connect to them.



## 5. Compute Services (Running the Apps)
To run their applications, we have 3 main options:
1.  **Amazon EC2 (Virtual Machines):**
    - Best if they need full control over the OS.
    - We can choose the right instance type (Memory, CPU, or Storage optimized).
    - **Cost Tip:** Use **Auto Scaling** to automatically add or remove instances based on demand.
2.  **AWS Lambda (Serverless):**
    - Run code without provisioning servers.
    - They only pay for the compute time used (if code isn't running, cost is zero).
3.  **Elastic Beanstalk:**
    - The easiest way to deploy web apps. They upload code, and AWS handles provisioning, load balancing, and scaling.

## 6. Storage 
- **Amazon S3:** For object storage (files, images, backups). It is virtually unlimited and durable.
- **Amazon EBS:** Block storage for use with EC2 instances (like a hard drive). It is persistent (data survives reboot).
- **Amazon EFS:** Scalable file storage if multiple EC2 instances need to access the same files at the same time.
- **S3 Glacier:** For long-term data archiving at a very low cost.

## 7. Databases
- **Amazon RDS:** For relational databases (SQL).
  - *Why:* It is a managed service. AWS handles patching, backups, and high availability.
- **Amazon DynamoDB:** For NoSQL (key-value) data.
  - *Why:* Single-digit millisecond latency at any scale. No server management.
- **Amazon Redshift:** If they need a data warehouse for analytics.
