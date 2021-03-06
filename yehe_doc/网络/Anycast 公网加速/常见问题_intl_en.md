## What is AIA?
Anycast Internet Acceleration (AIA) is a cross-region dynamic acceleration network that significantly enhances your businesses' access to public network. Different from other acceleration services at the application layer, AIA is capable of achieving IP transfer optimization and multi-entry nearby access, while reducing issues such as network jitter and packet loss, which can ultimately increase the service quality of your in-cloud applications, expand their service scope, and streamline backend deployment.

### What is the difference between an Anycast EIP and a public IP?
An Anycast EIP is published in multiple regions simultaneously, so that the access traffic can reach the nearest region for transfer over Tencent Cloud's private network. It works based on Anycast which is perceptible to your business, so the bandwidth price is higher.
An ordinary public IP or EIP is only published in the region to which it belongs, and generally, the access traffic reaches it over the public network.

| Item | Anycast EIP | Non-Anycast EIP |
|---------|---------|---------|
| Publishing method | Anycast | Unicast |
| IP publishing region | Multiple | Single |
| Network price | Higher unit price and billed by accelerated traffic | Cheaper and billed at the public network price |
| Unbinding | Supported | Supported |
| AIA | Available 	| Unavailable. The public network is used by default, and when it fails, temporary free traffic scheduling will be provided |

### Why are regions isolated?
Tencent Cloud services are completely isolated in different regions in order to guarantee the maximum cross-region stability and fault tolerance.

### What is an acceleration region?
An acceleration region is where an Anycast EIP is published.
More acceleration regions will be added as Tencent Cloud's infrastructure expands. Currently, transfers among Europe, the U.S., and Asia Pacific are accelerated.

### What is a service region?
A service region is the region to which an Anycast EIP belongs after it is created. The EIP can only be bound to resources in its region. Backend logic computing (such as CVM) is performed there.

### What is the difference between a private IP and a public IP of a CVM instance?
A private IP is a connection address that provides services for a client whose source IP is from the private network.
A public IP is a connection address that provides public network communication for a client whose source IP is from the public network.
They can be directly mapped to each other through network address translation.
CVM instances in the same region can communicate over the private network, while those in different regions can only communicate over the public network.

### How is AIA billed?
If you purchase an Anycast EIP for constant acceleration, the traffic generated will be billed as the accelerated traffic at a unit price higher than that of ordinary public network traffic.
If you purchase a non-Anycast EIP, when the public network fails, Tencent Cloud will provide temporary acceleration service to help you bypass the failure and avoid service interruption. This value-added service is free of charge and imperceptible to your business, and the network fees incurred will be charged at the price of ordinary public network traffic.

### How is accelerated traffic billed?
Accelerated traffic is generated by an Anycast EIP. The total accelerated traffic of an account is billed based on the 95th percentile of bandwidth usage.

### Is accelerated traffic billed by outbound traffic or inbound traffic?
Accelerated traffic is billed by either the outbound or inbound traffic, whichever is higher.
 
### Can an Anycast EIP be billed by traffic?
No. The traffic generated by an Anycast EIP is billed by bandwidth.

### How to limit the speed for an Anycast EIP?
If you set a bandwidth limit for an Anycast EIP, the limit will be on each regional egress instead of the total bandwidth.
For example, if you limit the bandwidth of an Anycast EIP to 100 Mbps, then the egress bandwidth limit on each publishing region will be 100 Mbps, so that the total bandwidth will be greater than 100 Mbps.
