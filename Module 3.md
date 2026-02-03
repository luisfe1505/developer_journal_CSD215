**AWS Global Infrastructure Overview**

-22 current AWS regions
  
-Physical geographical area one or more availability zones in turn to consist of one or more data centers
  
-Regions are isolated from each other
  
-When you store data in one region, it is not replicated in others
  
-It is your responsibility to replicate data across regions if your buusiness needs require it
  
-With AWS management Console to enable or disable regions

**ZONES**
-Currentyl 69 availability zones
  
-Consist of discrete data centers
  
-Designated for fault isolation
  
-Every availability zone contains multiple data centre (typically 3)
  
-Have their own power infrastructure

-Physically separated by several kms (all availability zones are within 100kms of each other)

**DATA CENTERS**


-Location of where the actual data resides
  
-Customers do not specify a data center for the deployment of their resources

-designed for security
 
-Failures can occur that affect the availability of instances in the same location.

**BENEFITS PROVIDED BY THE INFRASTRUCTURE**

 -  Elasticity and scalability: resources can rapidly adjust dynamically
   
  - Fault tolerance: component redundancy
  
 - High availability: minimal to no human interversion, minimized downtime
   
<img width="832" height="400" alt="image" src="https://github.com/user-attachments/assets/91cbd5b6-6f7a-423b-8a8f-20e2bcd50032" />


**Security, identity and compliance services**

- AWS Identity and Access Management: manage access to AWS services ad resources securely.
- AWS Organizations: restrict what services and actions are allowedd in your accounts.
- Amazon Cognito: lets you add user sign in, sign up and access control to your web and mobile apps
- AWS Artifact provides on demand access to AWS security and compliance reports and select online agreements
- AWS Key Management Service (KMS): create and manage encryption keys
- AWS SHield: managed Distributed Denial of Service (DDoS) protection service that safeguards apps running on AWS.

 **AWS Cost Management Services**

- AWS Cost and Usage Report: AWs cost and usage data available, and additional metadata about services pricng and reservations
- AWS Budgets: set budgets that alert when your costs or usages exceed
- AWS Cost Explorer: visualize understand and manage your AWS costs and usage over time

**Management and governance services**

- AWS Management console: interface for accessing your account
- AWS Config: track resource inventory and changes
- Amazon CloudWatch: monitor resources and apps
- AWS Auto Scaling: scale multiple resources to meet demand
- AWS Command Line interface: unified tool to manage services
- AWS Trusted Advisor: optimize performance and security
- AWS Well-Architected Tool reviewing and improving your workloads
- AWS CloudTrail: tracks user activity and API usage.


  
