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

  




  
