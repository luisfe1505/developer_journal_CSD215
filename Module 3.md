 AWS Global Infrastructure Overview

  22 current AWS regions
  
  Physical geographical area one or more availability zones in turn to consist of one or more data centers
  
  Regions are isolated from each other
  
  When you store data in one region, it is not replicated in others
  
  It is your responsibility to replicate data across regions if your buusiness needs require it
  
  With AWS management Console to enable or disable regions

ZONES
  Currentyl 69 availability zones
  
  Consist of discrete data centers
  
  Designated for fault isolation
  
  Every availability zone contains multiple data centre (typically 3)
  
  Have their own power infrastructure
  
  Physically separated by several kms (all availability zones are within 100kms of each other)

DATA CENTERS 


  Location of where the actual data resides
  
  Customers do not specify a data center for the deployment of their resources

  designed for security
  
  Failures can occur that affect the availability of instances in the same location.

BENEFITS PROVIDED BY THE INFRASTRUCTURE

  Elasticity and scalability: resources can rapidly adjust dynamically
  Fault tolerance: component redundancy
  High availability: minimal to no human interversion, minimized downtime
<img width="832" height="400" alt="image" src="https://github.com/user-attachments/assets/91cbd5b6-6f7a-423b-8a8f-20e2bcd50032" />


  
