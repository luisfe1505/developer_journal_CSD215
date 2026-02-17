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
