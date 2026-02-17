**Compute services**
<img width="597" height="251" alt="{D7DF7C10-16C3-4174-80C7-EB2424280E25}" src="https://github.com/user-attachments/assets/0d547353-5f5e-495f-9da0-f074f14c000e" />

**Virtual Machines & Scaling**
- **Amazon EC2:** Just virtual machines (servers) that I can resize whenever my needs change.
- **Amazon EC2 Auto Scaling:** Automatically spins up new EC2 instances or kills them off based on rules I set (like if CPU gets too high). Keeps the app alive during traffic spikes.
**Containers**
- **Amazon ECR (Elastic Container Registry):** The storage unit where I keep and pull my Docker images.
- **Amazon ECS (Elastic Container Service):** The manager that actually runs and orchestrates those Docker containers.
- **Amazon EKS (Elastic Kubernetes Service):** Same idea as ECS, but specifically for running and managing Kubernetes.
- **AWS Fargate:** Runs containers *serverless*. I don't have to manage the underlying EC2 servers or clusters at all, AWS just runs the container.
**Serverless**
- **AWS Lambda:** True serverless computing. I just upload my code and it runs. No servers to manage, and I *only* pay for the exact milliseconds the code is actually executing.
- **AWS Serverless Application Repository:** Basically an app store where I can discover, deploy, or publish serverless apps.
**Web Apps & Simple Hosting**
- **AWS Elastic Beanstalk:** The lazy way to deploy web apps. I just give it my code, and it provisions the servers, load balancers, and scaling automatically.
- **Amazon Lightsail:** Super simple, low-cost virtual private servers (VPS). Great for just throwing up a quick website or simple app without overthinking it.
**Specialized Compute**
- **AWS Batch:** Does exactly what it sounds like: runs heavy batch computing jobs at massive scale.
- **AWS Outposts:** Literally brings AWS physical server racks into my own physical, on-premises data center.
- **VMware Cloud on AWS:** Lets me easily build a hybrid cloud connecting my on-premise VMware setup to AWS without buying custom hardware.


**Categories of compute services**
1. Infrastructure as a Service: Instance based, Provides virtual machines Amazon EC2, flexibility and leaves many of the server management responsibilities to you
2. Serverless computing: Function based, low cost. AWS Lambda, zero administration compute platform, run code without managin or porovisioning servers
4. Container-based computing: Instance based. Amazon ECS, EKS, Fargate, ECR. sign up and execute jobs quickly
5. Platform as a Service: Web apps. AWS Elastic Beanstalk. Focus on code AWS provides with all the app services that you need

**Optimal compute service**
- Depend on the use case
  - What is your app design?
  - What are your usage patterns
  - Which configuration settings will you want to manage?

**Amazon EC2 Elastic Cloud Computing**

- Provides virtual machines (EC2 instances) where you can host the same kinds of apps you can run in traditional on premises server
- Common uses
  - App server
  - Web server
  - Database server
  - Game server
  - Mail server
  - Media server
  - Catalog server
  - File server
  - Computing server
  - Proxy server

- Full admin over the OS that runs in these VMs
- You can lunch any number of instances of any size into availability zones anywhere in the world
- Control traffic to and from instances
- - **AMI Amazon Machine Image**: Provides information that is required to launch an EC2 instance 
- Key decisions to make when launching an EC2 instance

  1. Which Amazon Machine Image (AMI) to launch from.
     - Quick start: linux and windows AMIs that are provided by AWS
     - My AMIs: AMis that you've created
     - AWS Marketplace: Preconfigured templates by third parties
     - Community AMIs: AMIs created by people all around the world (use at your own risk)
     - <img width="603" height="281" alt="image" src="https://github.com/user-attachments/assets/350466df-098c-476d-8691-72bff6287ee0" />

2. Select an instance type
     - Consider your case
     - The instance type determines:
       - Memory (RAM)
       - Processing power (CPU)
       - Disk space and disk type (Storage)
       - Network performance
     - Instance type categories:
       - General purpose
       - Compute optimized
       - Memory optimized
       - Storage optimized
       - Accelerated computing
     -  Instance type naming:
       - t3.large
       - t family name
       - 3 generation number
       - large is the size
    - <img width="537" height="214" alt="image" src="https://github.com/user-attachments/assets/266caf9c-eb2c-4470-8cee-94af8b846749" />
    - Important to select also taking into account the networking needs of your development

**3. Network Settings**
- I have to pick my AWS Region *before* I even start the launch process.
- Once inside the region, I can drop the instance into an existing VPC and Subnet, or just build new ones on the fly.
- **Default behavior:** If I don't specify a VPC, AWS just throws the instance into the Default VPC and automatically hands it a public IP address.

**4. Attach an IAM Role (Optional)**
- I use this if the app running on my server needs to securely talk to other AWS services (like making API calls to a database or storage) without hardcoding any passwords.
- **Instance Profile:** This is literally just the "container" that passes the IAM role to the EC2 instance so it can use those permissions.

**5. User Data Script (Optional)**
- This is a startup script that runs automatically right after the instance boots up for the very first time.
- Super useful for automating the boring stuff (like installing web servers, downloading updates, or setting up the runtime environment).
- It has to be written in a format the server's OS understands (like a Bash script for Linux or PowerShell for Windows).

## 6. Storage Setup
- Need to configure the main "root" drive, and I can attach extra drives if I need to.
- For every drive, I have to choose:
  - Size (GBs)
  - Volume type
  - "Delete on termination" (Does the drive get destroyed when the instance is terminated?)
  - Encryption (Yes/No)

**Storage Options:**
- **EBS (Elastic Block Store):** Persistent block storage. If I stop the instance and start it later, my data is still safely there.
- **Instance Store:** Ephemeral (temporary) storage that is physically attached to the host computer. If the instance stops, the data is permanently WIPED.
- *(Note: I can also use EFS or S3, but NOT for the root boot drive).*

## 7. Adding Tags
- Literally just labels (metadata) I stick onto my EC2 instance.
- Why do I need them? It makes life easier for: filtering resources, automation scripts, figuring out my AWS bill (cost allocation), and security access control.

## 8. Security Group Settings
- The virtual firewall specifically for this instance.
- I create rules to dictate exactly *who* (source IPs) can connect and on *what ports*.
- If I skip this, AWS just slaps the default rules on it.

## 9. Key Pairs (How to log in)
- I can pick an existing key or tell AWS to generate a new one.
- It's a two-part lock: **Public key** (AWS holds onto this) and a **Private key** (I download this and guard it with my life).
- It's how I securely connect to the instance once it's running:
  - **Windows Instances:** I use my private key to decrypt and reveal the Administrator password so I can log in.
  - **Linux Instances:** I use my private key to SSH directly into the terminal.

**You can also lauunch an EC2 instance with the AWS Command Line Interface**
- Programmatically
- <img width="308" height="144" alt="image" src="https://github.com/user-attachments/assets/fe7835fd-77bc-433b-b13e-1d43d55d9ce4" />
- Successfully create the EC2 instance if the command is properly formatted, the resourses already exists, you have permissions to run the command, and you have sufficient capacity in AWS account
- If the command is successfull, the command responds with the instance ID and other information about it.
- <img width="520" height="263" alt="image" src="https://github.com/user-attachments/assets/2765304f-7310-4489-a08a-d5f51b565594" />

## Elastic IP Addresses (EIP)

- **Rebooting:** If I just reboot an instance, the IP address and DNS hostname stay exactly the same.
- **Stop & Start:** If I actually *stop* the instance and start it back up, AWS takes away my public IP and gives me a completely new one (and a new DNS hostname).
- **The fix:** If I need an IP address that is permanent and won't change when I stop the server, I have to use an **Elastic IP address**.

## EC2 Instance Metadata

- It's basically data *about* my running instance.
- Super useful for writing scripts to configure or manage the server while it's running.
- **The Magic IP:** I can only access this info while I am connected *inside* the instance. It's always at this exact address: 
  `http://169.254.169.254/latest/meta-data/`
- **How to view it:** If I'm logged into the Linux terminal, I just run this command to see the data:
  `curl http://169.254.169.254/latest/meta-data/`

## Amazon CloudWatch (Monitoring)

- The tool that watches my EC2 instances. It grabs raw performance data and turns it into readable metrics in near real-time.
- It holds onto this historical data for a full **15 months**.

**Two Levels of Monitoring:**
1. **Basic Monitoring:**
   - It's totally **free**.
   - Sends data points every **5 minutes**.
2. **Detailed Monitoring:**
   - Costs a fixed monthly rate.
   - Sends data points every **1 minute** 

## EC2 Pricing Models (How to save money)


**1. On-Demand (The flexible one)**
- **What it is:** Pay by the hour (or second). No long-term contracts at all.
- **Pros/Cons:** Maximum flexibility and no upfront cost, but it's the most expensive per-hour option.
- **When to use:** Short experiments, dev environments, or when traffic is completely unpredictable.

**2. Reserved Instances / RIs (The long-term contract)**
- **What it is:** I commit to a 1-year or 3-year term. In exchange, I get a massive discount (30-70% off). I can pay all upfront, partial upfront, or no upfront (the more I pay upfront, the bigger the discount).
- **Types:**
  - *Standard RI:* Biggest discount, but I'm locked into my choice. Best for steady, predictable apps.
  - *Convertible RI:* Slightly lower discount, but it lets me change the instance size or OS later if my needs change.
- **When to use:** Production servers that run 24/7 (like databases or main web servers). I buy these to cover my steady "baseline" usage.

**3. Scheduled Reserved Instances**
- **What it is:** A 1-year commitment, but I only reserve the server for fixed, recurring time blocks (like every weekday from 8 AM to 6 PM).
- **When to use:** Predictable recurring work, like daily batch jobs or apps that only run during business hours.

**4. Spot Instances (The clearance rack)**
- **What it is:** Using spare, unused AWS servers for huge discounts (70-90% off).
- **The Catch:** AWS can pull the plug and take the server back with only a **2-minute warning** if they need the capacity.
- **When to use:** Fault-tolerant work like big data processing, background jobs, or anything that can be easily paused and restarted without breaking. *Never* use this for a critical single server!

**5. Dedicated Instances vs. Dedicated Hosts**
- **Dedicated Instance:** Runs on hardware dedicated solely to my AWS account, but AWS still manages the specific sockets and placement.
- **Dedicated Host:** I rent the *entire* physical server box and control exactly which sockets/CPUs are used.
- **When to use:** I only ever need these if I have strict regulatory compliance rules, or if I'm bringing my own software licenses (BYOL) that are legally tied to physical CPU cores (like Windows Server or Oracle). It's very expensive.

**6. Per-Second Billing**
- **What it is:** AWS literally charges by the second (with a 60-second minimum).
- **The rule:** This only applies to On-demand, Reserved, and Spot instances if they are running **Amazon Linux** or **Ubuntu**.
- **Why it matters:** Saves money for super quick tasks so I don't pay for a full hour if a script only takes 3 minutes to run.

 - <img width="759" height="313" alt="{FC1BD4D1-03FA-4F70-9A09-D6C65E21737A}" src="https://github.com/user-attachments/assets/9ba1ea45-9d5c-4718-af5a-7286d80d3358" />


## Cost Optimization (How not to go broke on AWS)

**1. Right-Sizing (Don't overbuy)**
- Basically, don't rent a massive server for a tiny app.
- Check the actual metrics of what the app is using, shrink the instance to match that exact need, and *then* lock it in with a Reserved Instance. 

**2. Increase Elasticity (Turn it off when not using it!)**
- If an EBS-backed EC2 instance is just sitting there doing nothing, stop it or hibernate it.
- Use Auto Scaling so the system automatically adds or removes servers based on actual traffic. I shouldn't be paying for maximum capacity 24/7.

**3. Optimal Pricing Model**
- Don't just use On-Demand for everything. Mix and match!
- Put my steady, 24/7 databases on Reserved Instances. Put my flexible background jobs on Spot Instances. 
- *Pro-tip:* Use Serverless (like AWS Lambda) whenever possible so I literally only pay when the code is running.

**4. Optimal Storage Choices (Clean up the junk)**
- Shrink EBS volumes if they are mostly empty, or switch to a cheaper volume type if I don't need crazy fast performance.
- Delete old EBS snapshots that are just sitting there costing me money.
- Put data in the right place (e.g., don't put rarely-accessed archive files on an expensive, high-speed SSD).

**General Cost Habits:**
- Turn on **Cost Allocation Tags** so my monthly AWS bill is actually readable and I know exactly which project is burning money.
- Always architect with cost in mind from day one.
- Set budget targets, define my metrics, and actually review them regularly. Continuously measure and analyze the system to find new ways to save.

**Container services**

**Containers**: method of operating system virtualization, enables you to run an app and dependencies in resource-isolated processes
<img width="168" height="212" alt="image" src="https://github.com/user-attachments/assets/11535bf8-9755-4a25-a5d0-d58da59583ef" />


## Containers & Docker

**Why are Containers so good? (The Benefits)**
- **Self-contained:** Everything the app needs to run is packed inside one box.
- **Repeatable & Consistent:** The software runs the exact same way on my laptop as it does in the AWS cloud. No more "it works on my machine" excuses.
- **Super Fast:** They launch, stop, and terminate way faster than bulky Virtual Machines (VMs).

**Docker 101**
- It's the actual software platform that packages my code into these containers.
- I just install Docker on a server, and it runs the containers for me.
- **Docker Images:** Think of these as the read-only templates or blueprints. A container is just a running instance of an image.

**Containers vs. VMs (The big difference)**
- **VMs:** Heavy. They run directly on a hypervisor and each one needs its own full, heavy Operating System (like installing Windows 3 times for 3 apps).
- **Containers:** Lightweight. They run on top of the Docker engine and just share the host server's Operating System, as long as the OS supports Docker features.


<img width="796" height="360" alt="image" src="https://github.com/user-attachments/assets/866662d6-8991-4b5d-b443-f83ae6e92e0b" />

**Amazon ECS (Elastic Container Service)**

- Scalable high performance container management service
- Orcherstrates the running of docker containers
- Removing the complexing of managing the infrastructure yourself
- Familiar set of features as the EC2 services
- **Task definition** to prepare your application to run, specifies things like which containers deploy to run the task
  - Is a text file that describes one or more containers, up to 10 that form your app
  - You define which tasks you want to run in within a cluster, and Amazon is responsible for placing tasks within the cluster
- A task is the instantiation of a task definition within a cluster
- <img width="557" height="248" alt="image" src="https://github.com/user-attachments/assets/57ae8421-f420-49e9-8fe9-b1c23564412c" />

## Kubernetes (K8s)

- Containers are great for packaging an app, but they don't know how to run themselves at a massive scale. That's where Kubernetes comes in.
- It's an open-source tool for **container orchestration** (basically, it's the manager).
- **What it automates:**
  - **Deployment:** Starts the containers up.
  - **Scaling:** Creates more copies if traffic spikes, or kills them if it's quiet.
  - **Networking:** Figures out how the containers talk to each other.
  - **Storage:** Attaches persistent data drives to them.
  - **Self-healing:** If a container crashes, K8s instantly restarts or replaces it so the app doesn't go down.


## Amazon EKS (Elastic Kubernetes Service)

- Setting up Kubernetes from scratch is a headache. EKS is just AWS doing the heavy lifting for me.
- It's a managed service that lets me run Kubernetes on AWS without having to install the main control plane myself.
- Supports both Linux and Windows containers.
- It manages a cluster of EC2 instances and runs my K8s-orchestrated containers right on top of them.

## Amazon ECR (Elastic Container Registry)

- Think of this like my own private GitHub or Dropbox, but specifically for Docker images.
- It's a fully managed registry where I store, manage, and deploy my container images.
- Integrates perfectly with AWS compute services (like ECS and EKS).
- Transfers my container images back and forth securely over HTTPS.

**AWS Lambda**
<img width="765" height="290" alt="image" src="https://github.com/user-attachments/assets/07051f5d-db7d-4803-befe-6286b03af64e" />


## AWS Lambda (The Ultimate Serverless Compute)

- **The Concept:** I just upload my code (which becomes a "Lambda function") and AWS runs it. I don't have to provision, manage, or even think about servers.
- **Pricing Magic:** It only runs when it's triggered. I pay strictly for the compute time I actually use. If my code isn't running, my bill is literally $0.
- **Features:** - Completely automated administration.
  - Built-in fault tolerance (if it fails, it can automatically retry).
  - Supports tons of programming languages (Python, Node.js, Java, Go, etc.).
  - I can orchestrate multiple functions to work together in a sequence.

**Event Sources (How it wakes up)**
- A Lambda function just sits there asleep until an "Event" triggers it to run.
- **Triggers can be:**
  - Another AWS service (e.g., somebody uploads a photo to an S3 bucket, which triggers the code to resize the image).
  - A custom application I built.
  - Manual invocation directly from the AWS Console, SDK, or CLI.

**Lambda Configuration (The Setup)**
When I create a new Lambda function, I have to set up:
- **Function Name:** What I want to call it.
- **Runtime Environment:** The language I wrote the code in.
- **Execution Role:** The IAM permissions. (Basically, giving my code the security badge it needs to talk to other AWS services).
- **The Trigger:** What specifically will wake the function up.
- **The Code:** The actual script I wrote.
- **Memory:** How much RAM (in MBs) to give it. 
- **Optional Stuff:** Timeout limits (how long the code is allowed to run before AWS kills it), VPC settings, etc.

- <img width="752" height="334" alt="image" src="https://github.com/user-attachments/assets/5bc7f42a-ad68-4c0c-b9b0-7d84be5d53f2" />

## AWS Lambda Limits (The Quotas)

- I can trigger these functions based on an event or just put them on a schedule (like a daily timer).

**Soft Limits (I can ask AWS to increase these via a support ticket):**
- **Concurrency:** 1,000 executions running at the exact same time (per Region).
- **Storage:** 75 GB of storage for all my functions and layers combined (per Region).

**Hard Limits (Cannot be changed, period):**
- **Timeout:** The absolute maximum time a Lambda function can run is **15 minutes**. If my code takes longer than that, it just gets killed.
- **Package Size:** The deployment package can't be bigger than 250 MB (unzipped). 
- **Container Size:** If I'm deploying the code as a container image, the max size is 10 GB.
- **Memory:** There is a hard cap on how much RAM I can allocate to a single function.

---

## AWS Elastic Beanstalk 

**What is it?**
- Literally the easiest and fastest way to get a web app up and running on AWS. 
- I just upload my code, and Beanstalk handles the entire deployment across multiple servers.

**What it does for me automatically:**
- Provisions and configures the infrastructure (EC2 servers).
- Sets up the Load Balancer.
- Configures Auto Scaling (so it handles traffic spikes).
- Monitors the health of the app.
- Handles logging, analysis, and debugging.

**The Best Parts:**
- **Cost:** Elastic Beanstalk itself is **100% FREE**. I only pay for the actual underlying resources it creates (like the EC2 instances and databases).
- **Productivity:** I don't have to play system admin. I can just focus on writing my code in whatever language I prefer (Java, Node.js, Python, etc.).
- **Control:** Even though it automates everything, I still have complete control over the resources. If I need to go in and tweak a specific server setting, I can. 
- **Scalability:** It's very difficult to outgrow because it just scales the underlying AWS infrastructure as my app gets bigger.
