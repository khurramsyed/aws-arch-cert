# VPC
Amazon `Virtual Private Cloud (Amazon VPC)` lets you provision a logically isolated section of the AWS Cloud where you can launch AWS resources in a virtual network that you define.

You have `complete control over your virtual networking environment`, including selection of your own `IP address range`, `creation of subnets`, and configuration of `route tables` and `network gateways`. You can use both IPv4 and IPv6 in your VPC for secure and easy access to resources and applications.

### Route Table
`Route Table` contains a set of rules called routes that are used to Determine where the network traffic is routed.



- To Create a private subnet we need to create a route table that is not connected to internet gateway.
- [Good Video on Subnets and how to make a subnet private/public](https://www.youtube.com/watch?v=KNT463WSjjY&t=49s)


### Network ACL

- [Network Access Control List - Good Video](https://www.youtube.com/watch?v=vJzHn24TNQE)
- Works at **`SUBNET LEVEL`**.
- `Lower Number Rule is executed First`, This means lower number order is executed first whatever it allows or denies takes precedence.
- In bound and outbound rules are separately executed
- In Default ACL everything is **`ALLOWED`**
- However when you create `new  NACL` everything is **`DENIED`**
- You specify in your `inbound rules` source `IPs or CIDR range` from where traffic is `ALLOWED to flow in`.
- You specify in your `outbound rules` source `IPs or CIDR range` to where traffic is `ALLOWED to flow out`.


### Security group
- **`Controls the traffic`** for one or `more instances`
- Changes to security groups are automatically applied instantly to all instance attached to that security group.
- **`In case of security groups all the rules are evaluated`** and then decide what to do.
- In the `default security group` all inbound and outboud traffic is **`ALLOWED`** Just like default NACL.
- When you create a new `security group all inbound traffic is DENIED` just in like when you create new NACL. **However** all outbound traffic is allowed.
- At security group level everything is DENIED, unless you specify ALLOW rule.
- **`There are not DENY RULES AT SECURITY GROUP LEVEL only ALLOW RULES`** So I can only explicitly allow something  in security group rule

##### Questions

* Having just created a new VPC and launching an instance into its public subnet, you realise that you have forgotten to assign a public IP to the instance during creation. What is the simplest way to make your instance reachable from the outside world?*
 -

Although creating a new NIC & associating an EIP also results in your instance being accessible from the internet, it leaves your instance with 2 NICs & 2 private IPs as well as the public address and is therefore not the simplest solution. By default, any user-created VPC subnet WILL NOT automatically assign public IPv4 addresses to instances – the only subnet that does this is the “default” VPC subnets automatically created by AWS in your account.


In a custom VPC with new subnets in each AZ, there is a route that supports communication across all subnets/AZs. Plus a default SG with an allow rule 'All traffic, all protocols, all ports, from anythi

You may have only one internet gateway per VPC.ng using this default SG'.


By default, I am allowed 5 vpcs in each AWS region?

In a VPC an instance does not retain its private IP address.


0.0.0.0/0 would allow ANYONE from ANYWHERE to connect to your instances. This is generally a bad plan. The phrase 'web-facing subnets' does not mean just web servers. It would include any instances in that subnet some of which you may not strangers attacking. You would only allow 0.0.0.0/0 on port 80 or 443 to to connect to your public facing Web Servers, or preferably only to an ELB. Good security starts by limiting public access to only what the customer needs. *Please see the AWS Security whitepaper for complete details.*
