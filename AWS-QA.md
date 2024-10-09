# Q. Cmponents Required to Build Amazon VPC

## 1. VPC (Virtual Private Cloud)
- The primary virtual network in which you can launch AWS resources like EC2 instances.
- You define the IP range using a **CIDR block** (e.g., 10.0.0.0/16).

## 2. Subnets
- Sub-divisions of a VPC’s IP address range.
- Can be **public** or **private**:
  - **Public Subnets**: Associated with an **Internet Gateway** for internet access.
  - **Private Subnets**: Isolated from the internet but can communicate with other AWS services or internal networks.
- Each subnet resides in one **Availability Zone**.

## 3. Route Tables
- Contains rules (routes) that define the traffic routing between subnets and external networks.
- You can create different route tables for different subnets.
- For internet access, the route table should have a route to the **Internet Gateway**.

## 4. Internet Gateway (IGW)
- Enables resources in the public subnets (like EC2 instances) to access the internet.
- Must be attached to the VPC for internet access.

## 5. NAT Gateway / NAT Instance
- Allows instances in **private subnets** to access the internet (for software updates, etc.) without exposing them to incoming internet traffic.
- **NAT Gateway** is a managed service by AWS, whereas a **NAT instance** is a manually configured EC2 instance acting as a gateway.

## 6. Security Groups
- Act as virtual firewalls for EC2 instances, controlling inbound and outbound traffic at the instance level.
- Define rules for what traffic is allowed to or from instances.

## 7. Network ACLs (NACLs)
- Acts as a firewall for controlling traffic at the subnet level.
- Stateless rules for allowing or denying specific inbound and outbound traffic.

## 8. Elastic IP Addresses (EIP)
- Static public IP addresses associated with your VPC resources (usually EC2 instances or NAT Gateways) for consistent communication with the internet.

## 9. VPC Peering
- Enables communication between two VPCs in the same or different AWS regions.
- VPCs in a peering connection can route traffic between each other as if they are part of the same network.

## 10. Virtual Private Gateway (VGW)
- Used to connect your VPC to an external network over a **VPN**.
- Used in **Hybrid Cloud** setups where on-premise networks need to securely communicate with AWS resources.

## 11. Transit Gateway
- A central hub that simplifies connecting multiple VPCs, on-premises networks, and VPN connections.
- Provides efficient routing between all connected networks.

## 12. Endpoints
- **VPC Endpoints** enable private connections between your VPC and AWS services without using the internet.
- Types:
  - **Gateway Endpoints**: For services like S3 and DynamoDB.
  - **Interface Endpoints**: For connecting to other AWS services using private IPs.

## 13. Bastion Host (Optional)
- A secure EC2 instance used to access instances in private subnets via SSH or RDP.

## 14. Elastic Load Balancer (ELB)
- Distributes incoming application or network traffic across multiple targets, such as EC2 instances in different subnets.
- Can be configured for internet-facing or internal use.

## 15. DHCP Options Sets (Optional)
- Custom DHCP option sets can be used to specify domain name servers, domain names, and more for instances in your VPC.

## 16. VPC Flow Logs
- Captures information about the IP traffic going to and from network interfaces within your VPC for monitoring and troubleshooting purposes.
