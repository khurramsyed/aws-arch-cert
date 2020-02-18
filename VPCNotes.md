## Question
* Having just created a new VPC and launching an instance into its public subnet, you realise that you have forgotten to assign a public IP to the instance during creation. What is the simplest way to make your instance reachable from the outside world?*
 -

Although creating a new NIC & associating an EIP also results in your instance being accessible from the internet, it leaves your instance with 2 NICs & 2 private IPs as well as the public address and is therefore not the simplest solution. By default, any user-created VPC subnet WILL NOT automatically assign public IPv4 addresses to instances – the only subnet that does this is the “default” VPC subnets automatically created by AWS in your account.


In a custom VPC with new subnets in each AZ, there is a route that supports communication across all subnets/AZs. Plus a default SG with an allow rule 'All traffic, all protocols, all ports, from anythi

You may have only one internet gateway per VPC.ng using this default SG'.


By default, I am allowed 5 vpcs in each AWS region?

In a VPC an instance does not retain its private IP address.


0.0.0.0/0 would allow ANYONE from ANYWHERE to connect to your instances. This is generally a bad plan. The phrase 'web-facing subnets' does not mean just web servers. It would include any instances in that subnet some of which you may not strangers attacking. You would only allow 0.0.0.0/0 on port 80 or 443 to to connect to your public facing Web Servers, or preferably only to an ELB. Good security starts by limiting public access to only what the customer needs. *Please see the AWS Security whitepaper for complete details.*
