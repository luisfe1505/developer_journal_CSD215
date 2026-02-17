**What is a Network?**
- It's literally just 2 or more computers connected so they can share stuff.
- **Subnets:** Splitting a giant network into smaller chunks so it's not a huge mess.
- **Hardware:** To make them talk, you need a middleman like a **Router** or a **Switch**.

**IP Addresses (The Computer's Phone Number)**
Every device needs a unique number to be found on the internet.
- **IPv4:** The old-school one. It has 32 bits (looks like `192.168.1.1`).
- **IPv6:** The new, massive one. It has 128 bits. We had to make this because we literally ran out of IPv4 numbers!

**How to read an IP Address**
It's always split into two pieces:
1. **Network ID:** The *fixed* part. Think of it as the "street name".
2. **Host ID:** The *flexible* part. Think of it as the specific "house number" on that street.

**That weird Slash thing (like `/24`)**
If you see a slash and a number, it's just a cheat code telling you how many addresses you have left to use.
- `/24` means the first **24 bits are locked** for the street name (Network ID).
- Since IPv4 has 32 bits total: `32 - 24 = 8`.
- That means you have **8 bits left** to use for your actual computers (Host ID).
- 8 bits gives you exactly 256 possible addresses (ranging from `0` to `255`).


  - <img width="351" height="189" alt="{214F3DD2-ACE7-4A78-BA39-CBFF6E02726A}" src="https://github.com/user-attachments/assets/eba3a4e3-870b-45b9-9690-ee449a950719" />

  **What is a VPC?**
- Think of it as your own **private, walled garden** inside the massive AWS cloud.
- You get to build the network exactly how you want it (you choose the IP addresses, subnets, and security rules).



**VPC Golden Rules (How they are built)**
- **Isolation:** Your VPC is completely separated from everyone else's.
- **Regions:** 1 VPC = 1 Region. It cannot stretch across multiple regions.
- **Availability Zones (AZs):** A VPC can cover *multiple* AZs, but a **Subnet** can only live inside *one* AZ.
- **Subnet Types:** They are usually split into **Public** (has internet access) or **Private** (hidden from the outside world).

**IP Addressing (The CIDR Math)**
- You get to pick the size of your network using CIDR blocks.
- **Max size:** `/16` (Gives you a massive 65,536 IP addresses).
- **Min size:** `/28` (Gives you just 16 IP addresses).
- **No overlapping:** If you make multiple subnets, their IP ranges CANNOT overlap.

** The "Minus 5" Rule **
AWS is greedy and reserves **5 IP addresses** from *every single subnet* you create. You cannot use them! They are used for:
1. Network address
2. VPC local router
3. DNS (Domain Name System)
4. Saved for future use
5. Network broadcast

**Types of Public IPs**
- **Auto-assigned Public IP:** AWS just hands you a random IP when you launch a server. (If you stop the server, you lose the IP).
- **Elastic IP (EIP):** A **static** public IP that belongs to your account. You can move it between servers. 


**Elastic Network Interface (ENI)**
- It's literally just a **virtual network card**.
- You can unplug it from one virtual server and plug it into another. When you do, the network traffic (and IP) goes to the new server instantly.
- Every server you launch comes with a default one of these.


**Route Tables (The Network's GPS)**
- A set of rules that tells your network traffic exactly where to go.
- **The Local Route:** Every route table automatically has a rule that says "allow everything inside this VPC to talk to each other." You can't delete this rule.
- **The Subnet Rule:** Every single subnet MUST be connected to **one (and only one)** route table.


**VPC NETWORKING**

- Internet gateway:
  - VPC component that allows communication between instances in your VPS and the internet
  - provide a target in the route tables
  - perform network address translation for instances that were assigned public IPv4 addresses
  - <img width="471" height="206" alt="image" src="https://github.com/user-attachments/assets/3b1abcff-9532-4435-9276-51cb68f8e719" />
- Network address translation (NAT) gateway
  - Enables instances in a private subnet to connect with the internet or other services
  - But also prevents the internet from initiating a connection with those instances
  -  <img width="558" height="264" alt="image" src="https://github.com/user-attachments/assets/8bfc6a33-b3ca-4a65-8d03-b8da96685613" />

## VPC Networking & Connections

**Internet Gateway (IGW)**
- The door between my VPC and the outside internet.
- It gives my route tables a target to send internet traffic to.
- It also does the NAT (Network Address Translation) for any instances that have a public IPv4 address.



**VPC Sharing**
- Lets me share my VPC with other AWS accounts, as long as we are in the same AWS Organization.
- Basically, the account that owns the VPC shares specific subnets, and the other accounts can just launch their apps inside them.

**VPC Peering**
- A private network connection directly between two VPCs. Traffic never hits the public internet.
- Works across the same account, different accounts, or even completely different AWS Regions.
- **Important rule:** It's strictly 1-to-1 (non-transitive). If VPC A connects to VPC B, and VPC B connects to VPC C... VPC A *cannot* talk to VPC C. I would have to make a direct A-to-C connection.



**AWS Site-to-Site VPN**
- A secure, encrypted tunnel between my own network (like an office building) and AWS over the internet.
- **Setup steps:**
  1. Create a Virtual Private Gateway (the AWS side).
  2. Set up the Customer Gateway (my physical VPN device configuration).
  3. Make a custom route table.
  4. Establish the actual Site-to-Site VPN connection.
  5. Configure routing so traffic knows to go through the tunnel.



**AWS Direct Connect (DX)**
- For when a standard internet connection is too slow or inconsistent.
- It's a dedicated, *private* physical network line straight from my network to an AWS Direct Connect location.
- Fixes network performance issues caused by distance and regular internet traffic.

**VPC endpoints**
- Virtual device that enables to privately connect your VPC to supported AWS services
- Gateway endpoints
- Interface endpoints

**AWS Transit gateway**
<img width="675" height="317" alt="image" src="https://github.com/user-attachments/assets/fb8c9db1-abbb-4e73-9549-f2f2c6e9b6e0" />

## VPC Security


**Security Groups**
- Act as a virtual firewall directly at the **instance** level (e.g., attached to an EC2 server).
- Filters traffic going in and out of the instance.
- **Default rules:**
  - Inbound traffic is completely sealed shut (denied) until I explicitly add a rule to allow it.
  - Outbound traffic is always allowed by default.

**Network Access Control Lists (NACLs)**
- Work at the **subnet** level (acts as a firewall for the entire subnet).
- Every subnet *must* be associated with an ACL.
- 1-to-1 relationship between an ACL and a subnet.
- Has separate rules for inbound and outbound traffic. I can explicitly set rules to either *allow* or *deny* specific traffic.
- **Default ACL:** If I don't create a custom one, the default ACL automatically allows ALL inbound and outbound IPv4 traffic.
- **Stateless:** It doesn't remember traffic. If a request is allowed in, the response going back out still needs to be explicitly allowed by the outbound rules.

  Differences
<img width="443" height="170" alt="image" src="https://github.com/user-attachments/assets/12977e22-8590-49b1-9af4-18247f677c63" />

## Amazon Route 53

- Basically the phonebook of the internet (a Domain Name System or DNS web service).
- Translates human-friendly domain names (like `www.example.com`) into computer-friendly IP addresses.
- I can use it to register new domain names.
- Works perfectly with both IPv4 and IPv6.


**Routing Policies (How it decides where to send traffic)**
- **Simple:** The basic setup. Just points a domain to a single server environment.
- **Weighted:** Splits traffic based on a ratio I set (like sending 80% of traffic to one server and 20% to another).
- **Latency:** Sends users to the server that gives them the fastest response time (great for global apps).
- **Geolocation:** Routes users based on *their* physical location (e.g., sending European users to a European server).
- **Geoproximity:** Routes traffic based on the geographic location of my *AWS resources*.
- **Failover:** If my main server crashes, it automatically sends traffic to a backup site. Note: I have to configure a "health check" for this to work.
- **Multivalue Answer:** Returns multiple IP addresses to the user, acting like a simple load balancer (can be combined with health checks).


**DNS Failover & Health Checks**
- The whole point of this is to keep my apps highly available.
- Lets me configure automatic backup and failover scenarios.
- Crucial for building multi-region architectures (if an entire AWS region goes down, Route 53 just redirects my users to a working region).
- It constantly runs health checks to make sure the servers are actually alive before sending people there.


<img width="573" height="300" alt="image" src="https://github.com/user-attachments/assets/41c8ce6e-4ff6-409e-aa68-4ae39f7cfbfa" />

**Amazon CloudFront**

- Network performance latency
- the distance significantly affects performance, that is why is necessary a content delivery network
- CloudFront is a fast, global and secure Content Delivery Network service
- High transfer speeds
- Pay as you go pricing
- Self service offering
- Relies on route 53 geo location routing
- Edge location: network of data centers that CloudFront uses to serve popular content quickly to customers

NAT gateway: Network Address Translation gateway

