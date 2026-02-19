***Storage***

**Amazon Elastic Block Store (EBS)**

- CLoud based SSD/HDD that you attach to the virtual machine (EC2 instances)
- Basically is storing data in a SSD or HDD but in the cloud
- You can configure performance types and size
- Provides persistent block storage volumes for use with amazon EC2 instances
- Replicated within availability zone to protect from data lose
- Scale your usage up or down within minutes

- **Block storage**
  - enables you to change one block (piece of the file) that contains certain info
- **Object storage**
  - the entire file must be updated to change even just 1 character on it

- In EBS you can create individual sotorage volumes
- Offers block-level storage
- A backup of an amazon EBS volume is called a snapshot
  - The first snapshot is called the baseline snapshot
  - Every snapshot after the baseline one will only contain what is different from the previous snapshot
 
- Uses:
  - Boot volumes and sotrage for amazon EC2 instances
  - Data storage with a file system
  - Database hosts
  - Enterprise apps
 
<img width="545" height="248" alt="{8D0AF698-0FD3-4C88-B507-AC38D3D302BF}" src="https://github.com/user-attachments/assets/1b51f28c-3b67-457c-8c9b-315c05a5c231" />


Snapshots:
- Point-in-time snapshots
- Recreate a new volume at any time
- Added cost is per GB-month of data stored
Encryption
- No additional costs
- Encrypted amazon EBS volumes
Elasticity
- Increase capacity
- Change to different types
- Dinamically

Volumes: 

- **Persistent storage**: Volume lifetime is independent of any particular Amazon EC2 instance.
- **General purpose**: Amazon EBS volumes are raw, unformatted block devices that can be used from any operating system.
- **High performance**: Amazon EBS volumes are equal to or better than local Amazon EC2 drives.
- **High reliability**: Amazon EBS volumes have built-in redundancy within an Availability Zone.
- **Designed for resiliency**: The AFR (Annual Failure Rate) of Amazon EBS is between 0.1% and 1%.
- **Variable size**: Volume sizes range from 1 GB to 16 TB. 
- **Easy to use: **Amazon EBS volumes can be easily created, attached, backed up, restored, and deleted.


**Amazon Simple Storage Service (S3)**

- An an object-level storage, which means that if you need to make a single change in a file, you need to make tha change and then re upload the entire modified file
- S3 stores data as objects called buckets
- Virtually unlimited storage
- Designed for 11 9s of durability
- Not associated with any particular service
- No need to manage any server
- Objects can be almost any data type
- By default none of the data is shared publicly
- Event notifications when certain events occurs
- Can be sent to you or can trigger other events

Amaozn S3 storage classes
- S3 Standard: high durability, availability and performance, for frequently accessed data, cloud apps, content distribution and big data
- S3 Intelligent-tiering: optimizes costs without performance impact, long lived data with access patterns that are unknown or unpredictable
- S3 Standart-Infrequent Access (standard-IA): data accessed less frequent but requires a rapid access when needed, long term storage and backups
- S3 One-Zone_INfrequent Access (One Zone-IA): data accessesed less frequent but requires a rapid access when needed, but stores in a single availability zone (reduces costs), secondary backup copies storage data that is replicated from another region
- S3 Glacier: secure, durable and low cost storage class for data archiving
- S3 Glacier Deep Archive: lowest cost storage class, long term retention and digital preservation for that that might be accessed once or twice in a year
 
Amazon S3 bucket URLs

To upload your data:
1. Create a bucket in an AWS Region
2. Upload almost any number of objects to the bucket

- Bucket path style URL endpoint:
  - https://s3.<region-code>.amazonaws.com/<bucket-name>
- Bucket virtual-hosted-style URL endpoint:
  - https://<bucket-name>.s3-<region-code>.amazonaws.com

Access the data anywhere:
Console, CLI, SDK

Common scenarios:
- Backup and storage: provide data backup and storage for others
- Provide services that deploy, install and manage web apps
- Media hostingL Build a redundatn, scalable and highly availablee infrastructure that hosts video, photo or music uploads and downloads
- Software delivery: host your software apps that customers can download.

Pricing:
- Gbs per month
- Transfer OUT to other regions
- PUT, COPY, POST LIST and GET requests
Do not pay for:
- Transfers IN to amazon S3
- Transfers OUt from amazon S3 to amazon cloudFont or EC2 in the same region

Sotrage pricing:
1. Storage class type
2. Amount of storage
3. Requests
4. Data transfer

**Amazon Elastic File system**

- provides simple, scalable, elastic file storage for use with AWS services and on premises resources
- Fully managed file system
- You can mount multiple EC2 instances at the same time
- File storage in AWS Cloud
- Wroks well for big data and analytics
- Petabyte scale, low latency, automatically
- thousands of instances can access an EFS file system at any time
- highly durable and highly available
- <img width="913" height="446" alt="{FDDA543C-19E8-4AED-9AFA-510536525BE8}" src="https://github.com/user-attachments/assets/804dc715-9648-4525-af6c-795a5a5f8b2a" />


Set up an EFS
1. Create your amazon EC2 resources and launch your Amazon EC2
2. Create your Amazon EFS file system
3. Create your mount targets in the appropriate subnets
4. Connect your amazon EC2 instances to the mount targets
5. Verify the resources and protection of your AWS account


Resources:
- File system:
  - Mount target
    - Subnet ID
    - Security Groups
    - One or more per file system
    - Create in a VPC subnet
    - One per Availability Zone
    - Must be in the same VPC
  - Tags
    - Key-value pairs

**Amazon S3 Glacier**

- Secure, durable and low cost cloud storage service for data archiving and long term backup
- Terms
  - Archive: Any object that you store in Glacier
  - Vault: container for storing archives
  - Vault access policy: determine who can and cannot access the data that is stored in the vault
- Options for retriving data:
  1. Expedited: typically made available within 1 to 5 minutes (most expensive)
  2. Standard: 3 to 5 hours (less expensive than expedited but more than bulk)
  3. Bulk 5 to 12 hours (least expensive)
- Use cases:
  - Media asset archiving
  - Healthcare information archiving
  - Regulatory and compliance archiving
  - Scientific data archiving
  - Digital preservation
  - Magnetic tape replacement
- You can use the management console, however, the uses are limited
- Better to use REST apis, java or .net SDKs, lifecyles policies

Lifecycle policies
- Enable to delete or move objects based on age
- <img width="611" height="191" alt="image" src="https://github.com/user-attachments/assets/d654a170-3478-4561-9f1c-ea365b4a8435" />

Storage classes
- <img width="969" height="433" alt="image" src="https://github.com/user-attachments/assets/b336d9ce-ca8c-48d3-80c5-eb0d4c61c63d" />

Amazon S3 vs Amazon S3 Glacier\
\
Data volume: No limit | No limit\
Average latency: ms | minutes/hours\
Item size: 5tb max | 40 tb max\
Cost GB/Month: High | Low\
Billed requests: PUT, COPY, POST, LIST and GET | UPLOAD and retrieval\
Retrieval pricing: per request | per request and per GB

<img width="624" height="294" alt="image" src="https://github.com/user-attachments/assets/cf159484-c2c6-4131-868a-336cf7fd4f2d" />

- You can control access with IAM
- Amazon S3 Glacier encrypts your data with AES-256
- Manages your keys for you
