***Databases***

Unmanaged Services: Scaling, fault tolerance and availability are managed by you
Managed services: Scaling fault tolerance and availability are managed by the service

**Challenges on Relational databases**

- Server maintenance and energy footprint
- Software installation and patches
- Database backups and high availability
- Limits on scalability
- OS installation and patches

**Amazon RDS Relational Database Service**
- Managed service that sets up and operates a relational database in the cloud
- Primary focus is the data and optimizing the app
- AWS manages:
  - OS installation and patches
  - Database software installation
  - DB backups
  - High availability
  - Scaling
  - Power and racking stacking servers
  - Server maintenance
 
Amazon RDS instances
- DB instance class
  - CPU
  - Memory
  - Network performance
 
- DB instance storage
  - Magnetic
  - General Purpose
  - Provisioned IOPS
 
- You select which database engine to run


Amazon RDS in a VPC
- <img width="543" height="295" alt="{480DD345-86AC-4D27-AA28-1D92BF94681B}" src="https://github.com/user-attachments/assets/4eadf796-b090-4e4b-90d2-b26801f4712d" />

- There is also an option to deploy a database in multiple Availability zones
- AWS automatically creates a stand by copy which will deploy in the extras AZs

**Read replicas**

- Updates that are made to the source database instance are asynchronously copied to the read replica instance
- Can be promoted to be primary if needed
- Used for read-heavy database workloads
- Offload read queries

Billed on the amount of time that the service is running
No additional charge for backup storage


**Amazon DynamoDB**

Realtional DBs: 
- Structured data
- Organized by tables, records and columns
- RElationships between tables
- SWL
- Difficulties scaling out horizontally or working with semistructured data
- many joins for normalized data

Non relational DBS:
- Any DB that does not follow the relational model
- Designed to overcoe the limitations of relational DBs
- Handle demands of variable structured data
- They can work with unstructured and semistructured data

**DynamoDB**
- Fast and flexible NoSQL database service for all apps that need consistend single digit millisecond latency at any scale
- Amazon manages all the underlying data for these services
- Create tables and then add items to a table
- No practical limit for the amounts of items in a table
- Items in the same table can have tdifferent attributes
- You can make changes without the need to migrate your schema, as you would in a RDB
- Provision the amounts of read write, scalable
- Global tables, enable replicate your choise across regions
- TABLES: Collections of data
- ITEMS: Group of attributes that is uniquely identifiables
- ATTRIBUTES: Fundamental data element in the table
- Primary keys:
  - Simple: Partition key
  - Composite: Partition key + Sort key
 

**Amazon RedShift**

Fast fully managed data warehouse
- Standard SQL
- Existing business intelligence

- Simple and cost effective to set up, use and scale
- Sophiscticated query optimization
- Most results come back in seconds
- An implementatino consist of leader and compute nodes:
  - Leader:
    - Manages communication with client programs ad all communication with compute nodes
    - Parses and develops plans to carry out database operations
    - Series of steps needed to obtain results for complex queries
  - Compute nodes:
    - Run the compiled code and send intermediate results back to the leader node for final aggregation
   
- Only pay for what you use
- Enables to focus on data and business
- Can scale up and down as needed
- Security is high priority (Built in)
- Both at rest and in trnasit
- Compatible with a lot of known tools


**Amazon Aurora**

- MySQL and PostgreSQL compatible relational database that is built for the cloud
- Combines the performance and availability of commercial databases
- Fully managed service
- reduce time consuming tasks like provisioning, patching, backup, recovery, failure detection and repair

- Dont have to do anything to configure high availability
- suport standard SQL
- pay as you go
- With AWS DMS and AWS Schema Conversion tool, you can move your dataset into Amazon Aurora
- High availability, stores multiple copies of your data into multiple AZs
