***Cloud architecture***

**AWS Well-Architected Framework**

Architecture is the art and science of designing and building large structures.
- Cloud architects
- Engage with tdesision makers
- Ensure alignment between tech delverables of a solution and the business goals
- work with delivery teams that are implementing the solution to ensure that the tech features are appropriate

**Well-Architected Framework:**

- Guide designed to help you build the most secure, high-performing, efficent infrastructure for your cloud apps
- Provides a set of foundational questions and best practices that can help evaluate a cloud architecture
- Divided in:
  - Operational excellence:
    - Ability to run and monitor systems to deliver business value
    - Key topics: Automating changes, REsponding to events, defining standards to manage daily operations
    - Design principles
      1. Perform operations as code, (define your entire workload)
      2. Annotate documentation, (automating the creating of documentation after every build)
      3. Make frequen, small, reversible changes, (design workloads to update components regularly)
      4. Anticipate failure, (identify potential sources of failure)
      5. Learn from all operatoinal events and failures, (share what is learn accross teams or the organization)
    - Foundational questions fall under:
      -  Organization
      -  Prepare
      -  Operate and Evolve
  - Security:
    - Focuses on the ability to protect information, systems and assets
    - Key topics: Identifying and managing who can do what, Protecting systems, Establishing controls to detect security events
    - Design principles:
      1. Implementing strong identity foundation, (principle of least privileges, and enforce separation of duties)
      2. Enable traceability, (monitor, alert and audit actions and changes to your environment)
      3. Apply security at all layers, (defense in depth and security controls to all layers in your architecture)
      4. Autoamte security best practices, security mechanisms to improve your ability to secure scale more rapidly and cost effective)
      5. Protect data in transit and at rest, (classify data into sensitivity levels)
      6. Keep people away from data, (reduce the risk of loss or modification due to human error)
      7. Prepare for security events, (incident management process)
    - Foundational questions fall under:
      - Identity and access management
      - Detectivecontrols
      - Infrastructure protection
      - Data protection
      - Incident response
  - Reliability:
    - Ability of a system to recover from failures to meet business and customer demand
    - Key topics: setting up, cross-project requirements, recovery planning, handling change
    - Design principles:
      1. Test recovery pricedures, (test how your system fails, and validate recovery procedures)
      2. Automatically recover from change, (monitore systems and configure them to trigger an automaed recovery when a treshold is breached)
      3. Scale horizontally to increase aggregate workload availability, (replace one large resource with multiple smaller resources)
      4. Stop guessing capacity, (automate the addition or removal or resources)
      5. Manage change in automation, (use automation to make changes to infrastructure and manage changes in automation)
    - Foundational questions fall under:
      - Foundations
      - Failure management
      - Change management
  - Performance efficency:
    - Ability to use It and computing resources efficiently to meet system requirements
    - Key topics: selecting the right resource types and sizes based on workload requirements, monitoring performance, making informed decisions to maintain efficiency as business needs to evolve
    - Design principles:
      1. Democratize advanced technologies, (consume technologies as a service)
      2. Go global in minutes, (deploy systems in multiple regions)
      3. Use serverlessarchitectures, (serverless architectures to remove the opreational burden of running and maintaining servers)
      4. Experiment more often, (perform comparative testing of different types of instances, storages or configurations)
      5. Have mechanical sympathy, (use the technology approach that align best tto what you need)
    - Foundational questions fall under:
      - Selection
      - Review
      - Monitoring
      - Tradeoffs
  - Cost optimization:
    - Avoid unnecessary costs
    - Key topics: Understanding and controlling where money is being spent, selecting te most appropriate and right number of resource types, analyzing spending over time, scaling to meet business needs without overspending.
    - Design principles:
      1. Implement Cloud foundational financial management, (to achieve financial success and accelerate business value realization)
      2. Addopt a consumption model, (pay only for the computing resources that you require)
      3. Measure overall efficency,( measure the business output of the system and the costs associated with delivering it)
      4. Stop spending money on data center operations, (AWS does the heavylifting of racking, stacking and powering servers)
      5. Analyze and attribute expenditure, (the cloud make it easier to accurately idenity system usage and costs)
      6. Use managed and app-level services to reduce cost of ownership, (reduce the operation burden of maintaining servers)
    - Foundational questions fall under:
      - Expenditure awareness
      - Cost-effective resources
      - Matching supply and demand
      - Optimizing over time 
  - Sustainability:
    - Focuses on minimizing the environmental impacts of running cloud workloads
    - key topics: shared responsibility mdel for sustainability, understanding impact, maximizing utilization to minimize required resources and reduce downstream impacts

**Reliability and Availability**
One of the best practices on the well architected framework is to plan for failure or, application/workflow downtime
Reliability: 
- Measure of your system's ability to provide functionality when desired by the user
- You should think of reliability in statistical terms:
  - **Probability that an entire system will function as intended for a period of time**
- Failure of system components impact on the availability of the system
- Statistical measurements:
  - Mean time between failures (MTBF) = total time in service/number of failures
  - Mean Time to Repair (MTTR) = total time bringing back online a system, repairing failures
  - Mean Time Between Failures (MTBF) = MTTF + MTTR
 
Availability:
- Percentage of time that a system is operating normally or correctly performing the operations expected of it.
- Also defined as the percentage of uptime (lenght of time that the system is online between failures)
- Availability is reduced anytime tha app isn't operating normally, including scheduled and unscheduled.
- Common shorthand when referring to availability is the number of 9s: (5 9s = 99.999%)
- Highly available system is the one that can withstand some measure of degradation while still remaining available
- In a highly available system downtime is minimized as much as possible and minimal human intervention is required
- In highly available systems failures are recovered fast (often less than 1 minute)
- <img width="355" height="205" alt="image" src="https://github.com/user-attachments/assets/4104cba9-35f0-4ac0-9b34-f6b267bbb249" />
- Factors that influence availability:
  - Fault tolerance: The built in redundancy of an app component's and it's ability to remain operational
  - Scalability: the ability of your app to accomodate increases in capacity needs without changing design
  - Recoverability: The process, policies and proceures that are related to restoring service after a catastrophic event
 
**AWS Trusted Advisor**

- Online tool that provides real time guidance to help you proovision your resources following AWS best practices
- You can use this tool to design and review your architectures in AWS
- Looks at your entire AWS environment and gives you real time recommendations in five categories:
  - Cost optimization: makes recommendations to optimize cost based on your resource usage, such as eliminating unused resources, or making commits to reserve capacity.
  - Performance: checking your service limits, looking at your provisioned throughput and monitoring overused instances
  - Security: Identifying gaps that you need to close, and examins your permissions
  - Fault tolerance: Increase availability and redundancy of your app, by taking advantage of automatic scaling, health checks, Multi-AZ deployment, and backup capabilities
  - Service limits: Checks for service usage that is more than 80% of the usage limit.
