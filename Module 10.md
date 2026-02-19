 ***Auto Scaling and Monitoring***
 
**Elastic Load Balancing** 

AWS Service that distributes incoming app or network traffic across multiple targets.
- In a single AZ or across multiple
- 3 Types of elastic load balancers
- <img width="655" height="262" alt="image" src="https://github.com/user-attachments/assets/86bc7104-4090-419a-b06f-0afd47d71b10" />

How ELastic Load Balancing Works:
- Accepts incomming traffic from clients and routes requests to its registered targets
- Configure it to accept one or more listener:
  - A listener is a process that checks for connection requests
  - A listener is configured with:
    - Protocol
    - Port number for connections from the load balancer to the targets
   
- Also to perform health checks:
  - Monitor the health of registered targets
  - So that the load balancer only sends requests to the healthy instances

**Note:** With application and network load balancers, you register targets in target groups, and route traffic to the target groups\
But with classic load balancers, you register instances with the load balancer\

**Use cases**

- High availability and better fault tolerance
- Containerized apps
- Elasticity and scalability
- VPCs
- Hybrid environment
- Invoke Lambda functions over HTTP(s)

**Load balancer monitoring**

- Amazon CloudWatch metrics: publishes data points, used to verify that the system is performing as expected, and creates an alarm to initiata an action if a metric goes outside an acceptable range
- Access Logs: Capture detailed information about requests sent to your load balancer
- AWS CLoudTrail logs: to capture the who, what, when, and where of API interactions in AWS Services


**Amazon CloudWatch**

Monitoring and observability service used built for devoOps engineers, developers, site reliability and IT managers\
- **Monitors** your AWS resources in real time
- **Collects and tracks**, standard and custom metrics
- Send **Alarms** to an amazon SNS topic, or to perform EC2 autoscaling or EC2 actions
- **Events** to define rules to match changes in AWS environment and rouute these events to one or more target functions or streams for processing


CloudWatch alarms\

- You can create alarms based on:
  - Static threshold: you choose a metric for that threshold and the alarm goes on when the metric breaches the threshold for a specific number of evaluation periods
  - Anomaly detection
  - Metric math expression
 
- Specify:
  - Namespice
  - Metric
  - Statistic
  - Period
  - Conditions
  - Additional configurations
  - Actions

**Amazon EC2 Autoscaling**

- Scaling is the ability to increase or decrease compute capacity of your app
- Useful for workload with varying capacity requirements during a period of time
- Without scaling, your app could under perform, or become unavailable for users
- Or spend a lot of money on unused resources
- Computing power is a programatic resource, this means that you can take a flexible approach to scaling

- EC2 autoscaling is a service that helps your maintain app availability and enables you to automatically add or remove EC2 instances according to conditions you define
- Several ways to adjust scaling to meet the needs of your app
- Dynamic scaling or predictive scaling

**Autoscaling groups**
- Collection of EC2 instances that are treated as logicsl grouping for the purposes of automatic scaling and management
- the size of a group depends on the number of instances you set as the desired capacity
- you can adjust the size to meet demands
- you can specify the minumum/maximum number of instances, amazon will automatically prevent to go over or under that limit
- If you specify the desired capacity, amazon will adjust the size of the group
- <img width="251" height="217" alt="image" src="https://github.com/user-attachments/assets/6028588c-157e-4ba1-ba89-01517a4f764f" />

**Scaling out** is when Amazon EC2 instances are launched\
And **Scaling in** is when amazon EC2 instances are terminated\
**<img width="542" height="234" alt="image" src="https://github.com/user-attachments/assets/9a74f1cd-3c4c-4911-bab1-4766bd09a126" />**

Launch configuration is an instance configuration template with:
- AMI
- Instance type
- IAM role
- Security groups
- EBS volumes

Next, you specify where you want the scale, specifying:
- Minimum and maximum of your instances
- launch it into a subnet with a VPC
- Attach the load balancer

Finally, you specify when to scale your event
- Maintain a specify number of instances runnning at all time
- Manual scalling
- Scheduled scaling
- Dynamic scaling
- Predictive scaling

Implementng dynamic scaling\
<img width="734" height="333" alt="image" src="https://github.com/user-attachments/assets/3fb7fa23-65e7-4d2b-9c42-3e8e7a7b9d80" />

**AWS Auto Scaling**

- Monitors your apps and automatically adjusts capacity to maintain steady, predictable performance at the lowes possible cost
- Provides a simple, powerful user interface that enables you to build scaling plans for resources
