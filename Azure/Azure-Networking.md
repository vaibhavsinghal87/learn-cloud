
# Azure Networking - 

4 networking related cloud services - 
- VNets
- SubNets
- Load Balancer
- Application Gateway


**VNets - Virtual Network**
- Automatically created when a cluster is created  
- In AWS it is called VPC  
- Resources in VNet can communicate with each other by default but cannot communicate with machines in another VNet. This is by default but can be modified  
- Scoped to a single region  
- Scoped to a single subscription only  
- VNets can connect using Peering. VMs in one VNet can connect to another VNets VM  
- VNets are segmented using Subnets  
- Protected using NSG  
- Each VNet has its own address range. IP address range expressed using CIDR notation  
- CIDR Notation - 109.186.149.240/16  


**Subnets -** 
- A logical segment in the VNet
- Shares a subset of the VNet’s IP range
- Used as a logical group of resources in the VNet
- Resources cannot be directly placed into a VNet. They have to be placed in a Subnet
- A default Subnet is created when we create a VNet
- Resources in a Subnet can talk to resources in other subnets in the same VNet. By default but can be customised
- Each Subnet gets a share of the parent Net’s IP range
- Subnets are free. Limit of 3000 subnets per VNet

VM in Subnet 1 can RDP into VM in Subnet 2
VM in VNet1 cannot RDP into VM in VNet2 by default


**NSG -** 
- A gatekeeper for Subnets
- Mini firewall
- Always attach NSG to Subnet
- NSG is free
- 5 tuples - Based on 5 tuples connection is either allowed or denied. This is called Security Rule. Each rule is assigned a number
- NSG is also attached to VM’s Network Interface


**Network Peering -** 
- To increase security we want to place resources in a completely different VNet
- Not to place non-public resources in a VNet that has public access
- Place sensitive resources in a different VNet
- Allows two VNets to connect to each other
- Peering can work across regions
- Peering is not free


**Network Topology -** 
- Network Watcher -> Topology - Provides high level view of networking elements
- Connection Troubleshoot


**Service Endpoint -** 
- A lot of managed services  expose public IP, sometimes these resources are only accessed by resources in the cloud and shouldn’t be accessed directly from the internet
- This security risk in handled by Service endpoint.
- Service Endpoint is free
- Traffic never leaves Azure backbone
- Enable Service Endpoint on the subnet from which you want to access the resource
- On the resource, set subnet as the source of traffic
- Can’t be used from on-prem network


**Private Link -** 
- Traffic doesn’t leaves the VNet
- Supports on Prem connectivity
- Setting up Private Link is complex
- Not free
- Service Endpoint is a legacy soln

VNet Integration - 


**Load Balancer -** 
- Azure Service that distributes load and checks health of VMs
- If any machine is not healthy, no traffic is transferred to it
- Can be public or private
- Load Balancer Types in Azure - Basic, Standard

**Configuring Load Balancer -** 
- Frontend IP Configuration - Public IP exposed by Load Balancer
- Backend Pools - VMs connected to Load Balancer
- Health Probes - Checks health of VM. Run in intervals(usually a few seconds)
- Load Balancing rules - A rule connecting FrontendIP to Backend Pool

**Application Gateway -**
- Load Balancer with improved web traffic capability 
- Functions as external endpoint for a web app
- Similar to load balancer with additional features/web related capability
- Usually App Gateway resides in its own Subnet and VNet

**Configuring App Gateway -** 
- Backend Pools - VMs, Scale Sets, App Services connected to the App Gateway
- HTTP Settings - Settings for the incoming HTTP Requests
- Frontend IP configurations - The public IP exposed by the App Gateway
- Listeners - Receives requests on a specific port  and protocol
- Rules - A rule connecting Listener with Backend Pool


- Application Gateway + App Service connection
- Application Gateway + VM connection
- Application Gateway + AKS connection - AGIC(Ingress Controller) is buggy. Use Third party soln
- Application Gateway + Function App(App Services) connection - 


