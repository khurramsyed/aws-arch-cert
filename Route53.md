# Route 53

Amazon Route 53 is a highly available and scalable cloud Domain Name System (DNS) web service. It is designed to give developers and businesses an extremely reliable and cost effective way to route end users to Internet applications by translating names like www.example.com into the numeric IP addresses like 192.0.2.1 that computers use to connect to each other. Amazon Route 53 is fully compliant with IPv6 as well.

What Does it do ?
- connects user requests to infrastructure running in AWS
  - For example EC2 instances, Elastic Load Balancing load balancers, or Amazon S3 buckets
- can also be used to route users to infrastructure outside of AWS
- You can use Amazon Route 53 to configure DNS health checks to route traffic to healthy endpoints or to independently monitor the health of your application and its endpoints

## Routing Types
Amazon Route 53 Traffic Flow makes it easy for you to `manage traffic globally` through a variety of routing types, including:
- Simple Routing
- Latency Based Routing
- Geo DNS, Geoproximity
- Weighted Round Robin

  All of which can be combined with DNS Failover in order to enable a variety of low-latency, fault-tolerant architectures

## Traffic Flow
  Using Amazon Route 53 Traffic Flow’s simple visual editor, you can easily manage how your end-users are routed to your application’s endpoints

## What is the difference between a Domain and a Hosted Zone?
