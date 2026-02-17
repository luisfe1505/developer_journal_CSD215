## AWS Cloud Security

**AWS Shared Responsibility model**

- Security and compliance are a shared responsibility between AWS and the customer
- AWs is responsible for protecting the infrastructure that runs all the services offered. (hardware, software, networking...)
- the customer is responsible for the encryption of data at rest and the encryption of data in transit. 

- <img width="505" height="274" alt="{4EF61D4B-8289-486B-B780-F7C69F474DF0}" src="https://github.com/user-attachments/assets/f9b5c598-72d4-4da5-91c9-88ee50ea61a3" />

- AWS is in charge of the security of the cloud
- And AWS is responsible for the physical infrastructure that hosts your resources:
  - Physical security of data centers
  - Hardware infrastructure
  - Software infrastructure
  - Network infrastructure

- Customer
    - The customer is responsible for the security in the cloud
        - Securing any instance operating systems
        - Securing the apps and secure account management
        - Security group configuratinos
        - Firewall and network configurations

- 1. IaaS (Infrastructure as a Service)
     - Basically renting the hardware (server), but virtual. Like having the PC yourself.
     - You can do whatever you want with the machine.
     - I control EVERYTHING except the physical hardware.
     - I have to update Windows/Linux (OS).
     - Configure firewalls and networks.
     - Install security patches.

2. PaaS (Platform as a Service) 
   - Environment is ready for me to upload code. I don't see servers or cables.
   -  Zero maintenance. I don't deal with the "plumbing" (infrastructure).
   -   They patch the OS, fix database issues, and handle disaster recovery.
   -    I only worry about my code and my data.
   -  I code, AWS manages where it runs.

3. SaaS (Software as a Service)
   - Finished product. Log in via browser/app and go.
   - Zero worries.
   -  Usually subscription or pay-as-you-go.
   -  NOTHING technical. I don't touch code or servers. I just use the software.

- AWS IAM (Identity & Access Management)
  - The Basics;
  - What is it: The "Bouncer" of AWS. Controls who can get in and what they can touch (servers, databases, etc.).
  - Cost: Free (Global service, doesn't matter which region you are in).
  - Main Job: Handles the "Who, What, and How."
  - Authentication: Who are you?
  - Authorization: What are you allowed to do?

- The 4 Key Components
  - User:Specific person or application and has permanent login info (password or keys).
  - Group: A bundle of users. Use this to give permissions to many people at once (e.g., "Admins").
  - You can't put a group inside another group (No nesting).
  - Policy:
  - The "Rulebook."It's a document (JSON format) that explicitly says "Allow" or "Deny" for specific services.
  - You attach these to Users, Groups, or Roles.
  - Role:Temporary access.
  - Like a security badge you put on for a few hours.
  - Not for one specific person; anyone (or any AWS service) who needs it can "assume" the role to get short-term permissions.

- Authentication & MFA
  - 1. Authentication
       - Simple security. The system asks: "Prove you are who you say you are."
       -  When creating a user, you pick 1 of 2 ways to enter:
   - A.Programmatic Access (For Developers/Machines):
     - Used for: AWS CLI (Command Line) or SDK (Code).
     - Needs: Access Key ID + Secret Access Key.
     - You don't use a standard password here.
   - B. Console Access (For Humans):
     - Used for: Logging into the website (AWS Management Console).
     - Needs: Username + Password.
     - If MFA is on, you need the code too.
    
- IAM Authorization
    - IAM users do not have access to anything and you need to explicitly grant access to each service
    - Only the minimal privilege needed for the users

  <img width="631" height="280" alt="image" src="https://github.com/user-attachments/assets/4f863371-3ef5-48b2-b607-aab31d237f94" />
  **IAM Policies**

- Document using JSON
- Two types: 
  1. Identity based policies: Attach policy to any IAM identity (user, group, role), actions that may or may not be performed
  2. Resource based policies: attached to a resource (what actions a specified principal can perform on that resource under what conditions.
 
- <img width="766" height="338" alt="image" src="https://github.com/user-attachments/assets/55c21720-ae37-49f1-8303-ccf79b623bc4" />
- The deny statements are the default ones, and if there is a conflict between an allow and a deny statement, the deny will allways win.

**IAM Permissions**
<img width="483" height="165" alt="image" src="https://github.com/user-attachments/assets/211a603f-8514-455b-9ac9-06cb72145cfe" />

**Securing a new AWS account**

- When you first create an AWS account, you begin with a single sign in identity that has complete access to all services **AWS account root user** 
- Best practice is to not use this account for day to day interaction
- Use IAM to create users, asign permissions to these users, following the principle of least privilege
1. Stop using the root account as soon as possible:
  1. while signed in the root account, create an IAM user for yourself 
  2. Create an IAM group, give it full administrator permissions and add the IAM user to the group
  3. Disable and remove your account root user access keys
  4. Enable a password policy for users
  5. Sign in with your new IAM user credentials
  6. Store your account root users credentials in a safe place
 
 2. Enable multi factor authentication (MFA)
    - Require MFA for your account root user and for all IAM users
    - Control access to AWS service APIs
   
 3. Use AWS CLoudTrail
    - Service that logs all API requests to resources in your account
    - Enables operational auditing on your account
   
 4. Enable a billing report, such as the AWS cost and USage report
    - Billing reports provide infromation aboutyour use of AWS resources and estimated costs for that use
    - AWS delivers the reportas to an amazon S3 bucked that you specify
    - AWS Cost and Usage Report tracks your AWS usage and provides estimated charges associated with your AWS account, either by the hour or by the day
   

**AWS Organizations service**

- Group AWS accounts into Organizational Units (OUs)
- Integration and support for IAM
- Use service control policies to establish control over the AWS services and aPI actions that each account can access
- Service control policies feature:
  - Centralized control over accounts
  - Ensures that accounts comply with access control guidelines
  - SCPs are similar to IAM permissions policies (similar syntax, SCP never grants permissinos, specify the maximum permissions for an organizations)
 
**AWS Key Management Service (KMS)**
- Manage encryption keys
- ENables to control the use of encryption across AWS services and in your apps
- Integrates CloudTrain to log all key usage

**Amazon cognito**
- Adds users sign up sign in and access control to your web and mobile app
- Sclaes to milliosn of users
- Suports with social identity providers such as facebook, google and amazon

**AWS shield**
- Managed distributed delial of Service (DDoS) protection service
- Safeguards apps running on AWS
- Provides always on detection and automatic inline mitigations
- AWS Shield standard enabled for no additional cost
- Use it to minimize app downtime and latency

**SECURING DATA**

- Data encryption is an essential tool to use when your objective is to protect digital data
- Take data that is legible and encodes it so that it is unreadable to anyone who does not have access to the secret key that can be used to decode it
- Data at rest is data that is physically stored on a disk or on tape
- AWS KMS encryption and decryption are handled automatically
- Data in transit is data moving accross a network
- Encryptino of data in transit is accomplished using Transport Layer Security (TLS) with an open standar cipher (AES-256) formerly called Secure Sockets Layer (SSL)
- AWS certificate manager is a service that enables to manage, provision and deploy SSL and TSL certificates for use with AWS services
- Web traffic that runs over HTTP is not secured, however web traffic that runs over Secure HTTP or HTTPS is encrypted using TSL or SSL certificates
- AWS services support data in transit encryption

**SECURING AMAZON S3 BUCKETS AND OBJECTS**

- By default, all buckets and objects are private and protected, and only accounts with explicit access can access it
- Tools to control access to amazon S3 buckets and objects:
  - Amazon S3 Block Public access (these settings override any other policies or permissions)
  - IAM policies (specify users or roles that can access specific buckets or objects)
  - Bucket policies (define access to specific buckets or objects, usually when a user cannot authenticate with IAM)
  - Access Control Lists (ACLs) (not commonly used because predates IAM)
  - AWS Trusted Advisor (bucket permission check feature useful for discovering if any buckets in your account have permissions)
 
**WORKING TO ENSURE COMPLIANCE**

- Compliance programs
  - external certifying bodies and independent auditors to provide customers with information about policies, processes and controls that are established and operated by AWS
  - requirements for stablishing, implementin, maintaining and continuinly improving an Information Security Management sysytem
  - Laws, regulations and privacy
  - Alignments and frameworks
 
- AWS Config
  - Service that enables you to assess audit and evaluate tha configuratinos of AWS resources
  - Maintains a history of your configuration
  - automatically evaluate recorded configurations
  - review changes
  - review deatiled config histories
  - Simplify compliance auditing and secure analysis
  - REgional service, you need to enable it in each region that you need
 
- AWS Artifact
  - Resource for compliance-related information
  - Provides access to security and compliance reports and select online agreements
  - Can access example downloads
  - Access AWS artifact directly from the AWS Management console

  




  
