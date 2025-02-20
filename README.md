 +-------------------------+
 | Private Subnet Instance |
 +-------------------------+
             |
             v
 +-------------------------+
 | Private Route Table     | 
 | (Routes traffic to      |
 | NAT Gateway)            |
 +-------------------------+
             |
             v
 +-------------------------+
 | NAT Gateway (in Public  |
 | Subnet)                 |
 +-------------------------+
             |
             v
 +-------------------------+
 | Internet Gateway (in    |
 | Public Subnet)          |
 +-------------------------+
             |
             v
 +-------------------------+
 | Internet                |
 +-------------------------+






Detailed Explanation:
Private Subnet Instance:

The instance in the private subnet tries to access the internet (e.g., for software updates).
Private Route Table:

The private route table in the private subnet routes all internet-bound traffic (0.0.0.0/0) to the NAT Gateway.
NAT Gateway (in Public Subnet):

The NAT Gateway resides in the public subnet. It has an Elastic IP (public IP), which allows it to access the internet on behalf of private subnet instances.
The NAT Gateway forwards the traffic to the Internet Gateway.
Internet Gateway (in Public Subnet):

The Internet Gateway (IGW) is attached to the public subnet and is responsible for routing traffic to and from the internet.
Internet:

The Internet Gateway sends the request to the internet, and once the response is back, it is routed through the NAT Gateway and sent back to the private instance.
