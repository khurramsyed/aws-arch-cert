# Load Balancers
- Balances the load across servers or application
- Don’t have to be internet facing or public but in general they are.

## Three type

### Application Load Balancers:
- Best Suited for HTTP and HTTPS  Traffic, Operate at Layer 7 , are intelligent and can create advanced routing based are application for example you changed language to french it load balance across french servers.

### Network Load Balancers:
- Load Balancing TCP requests,
- Extremely performant
- Operate at layer 4. i.e. connection level.
- Maintain ultra load latency.

### Classic Load Balancers
- Legacy elastic load balancers.
- Basic load balancing at most cost effective rate.
- User layer 7 specific features such x-forwarded headers and sticky session.
- But are not intelligent
- Can be used to strict layer 4 balancing for applications that rely on tcp.
- Generally you should use Application Load balancers.
- when application times out ELB will give 504 error.
- When user request comes via classic load balancers the application gets LBs IP
  addresses rather than users IP address , you can use x-forwarded-for header to find users IP.



# Application Load balancers

### Target Group
Your load balancer routes requests to the targets in a target group using the target
group settings that you specify, and performs health checks on the targets using
the health check settings that you specify.

- In Target Group you can create Targets By Instance, IP( For webservers that are not inside AWS and you just do it by public IP        )
  or a lambda.

  # Auto Scaling
mazon EC2 Auto Scaling helps you ensure that you have the correct number of
Amazon EC2 instances available to handle the load for your application

  ![alt text](as-basic-diagram.png "Auto Scaling")

  ## Auto Scaling Components
  The following table describes the key components of Amazon EC2 Auto Scaling.

  | Component  	               |   	|
  |----------------------------|---	|
  |   Launch Configuration   	 |  template for its EC2 instances. You can specify information such as the AMI ID, instance type, key pair, security groups, and block device mapping for your instances See [Launch Configuration](https://docs.aws.amazon.com/autoscaling/ec2/userguide/LaunchConfiguration.html)  or [Launch Template](https://docs.aws.amazon.com/autoscaling/ec2/userguide/LaunchTemplates.html)  	|
  |   Auto Scaling Group   	   | Your EC2 instances are organized into groups so that they can be treated as a logical unit for the purposes of scaling and management. When you create a group, you can specify its minimum, maximum, and, desired number of EC2 instances. For more information, see [Auto Scaling Group](https://docs.aws.amazon.com/autoscaling/ec2/userguide/AutoScalingGroup.html)	|

                                                                              --->S3 (Mdeia)
                                                                             |
                                                                |---> AZ1-->EC2-->RDS
                                                                |          |
                                                                |            -->S3 (Mdeia)
                                                                |
User --> Route53 --> AWS --> VPC --> ELB --> Auto Scale Group --|
                                                                |              -->S3 (Mdeia)
                                                                |             |
                                                                |---> AZ1-->EC2-->RDS
                                                                              |
                                                                              -->S3 (Mdeia)


### Autoscaling - Default Termination Policy
The default termination policy is designed to help ensure that your network architecture spans Availability Zones evenly. With the default termination policy, the behavior of the Auto Scaling group is as follows:

1. If there are instances in multiple Availability Zones, **choose the Availability Zone with the most instances and at least one instance that is not protected from scale in**. If there is more than one Availability Zone with this number of instances, choose the Availability Zone with the instances that use the oldest launch configuration.

2. Determine which unprotected instances in the selected Availability Zone use the **oldest launch configuration**. If there is one such instance, terminate it.

3. If there are multiple instances to terminate based on the above criteria, **determine which unprotected instances are closest to the next billing hour**. (This helps you maximize the use of your EC2 instances and manage your Amazon EC2 usage costs.) If there is one such instance, terminate it.

4. **If there is more than one unprotected instance closest to the next billing hour, choose one of these instances at random.**

The following flow diagram illustrates how the default termination policy works:

![alt autoscaling-termintation-policy](images/autoscaling-termintation-policy.png)



## Cross-Zone Load balancing
If Availability Zones is not properly added to the Elastic load balancer. then Availability Zone will not receive any traffic.

By default, the load balancer routes requests evenly across its Availability Zones. To route requests evenly across the registered instances in the Availability Zones, enable cross-zone load balancing.


>You can set up your load balancer in EC2-Classic to distribute incoming requests across EC2 instances in a single Availability Zone or multiple Availability Zones. First, launch EC2 instances in all the Availability Zones that you plan to use. Next, register these instances with your load balancer. Finally, add the Availability Zones to your load balancer. After you add an Availability Zone, the load balancer starts routing requests to the registered instances in that Availability Zone. Note that you can modify the Availability Zones for your load balancer at any time.


### ELB Access Logs

Elastic Load Balancing provides access logs that capture detailed information about requests sent to your load balancer. Each log contains information such as the time the request was received, the client's IP address, latencies, request paths, and server responses. You can use these access logs to analyze traffic patterns and troubleshoot issues.

Access logging is an optional feature of Elastic Load Balancing that is disabled by default. After you enable access logging for your load balancer, Elastic Load Balancing captures the logs and stores them in the Amazon S3 bucket that you specify as compressed files. You can disable access logging at any time.

http://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-access-logs.htmls

# Example HA Architecture

![alt text](HAArchitecture.png "HA Architecture")


###Create HA application

- Create S3 Buckets
  - make them public
  - Create Cloud Front Distribution - For your media S3 buckets
- Create Security Groups Web DMZ
- Create RDS Security Group  to Access you Database (Add Rules in RDS sec group to allow WebDMZ group)
- Create RDS Database
    -use you RDS Sec Group
    - Ensure to see advance settings
- Create Roles to allow s3 to be accessed by EC2 instances


-- Configure EC2
  Backup to S3
  Ec2 instance behind LB
  Update Route53 to

## DR Scenarios

### Pilot Light
The term pilot light is often used to describe a DR scenario in which a minimal version of an environment is always running in the cloud. The idea of the pilot light is an analogy that comes from the gas heater. In a gas heater, a small flame that’s always on can quickly ignite the entire furnace to heat up a house. This scenario is similar to a backup-and-restore scenario.

For example, with AWS you can maintain a pilot light by configuring and running the most critical core elements of your system in AWS. When the time comes for recovery, you can rapidly provision a full-scale production environment around the critical core.

![alt p](images/PilotLight.jpg)


### Autoscaling, Loadbalancers and Health checks
n this scenario, the load balancer will route the incoming requests only to the healthy instances. When the load balancer determines that an instance is unhealthy, it stops routing requests to that instance. The load balancer resumes routing requests to the instance when it has been restored to a healthy state.

There are two ways of checking the status of your EC2 instances:

1. Via the Auto Scaling group
2. Via the ELB health checks



The default health checks for an Auto Scaling group are EC2 status checks only. If an instance fails these status checks, the Auto Scaling group considers the instance unhealthy and replaces. If you attached one or more load balancers or target groups to your Auto Scaling group, the group does not, by default, consider an instance unhealthy and replace it if it fails the load balancer health checks.

However, you can optionally configure the Auto Scaling group to use Elastic Load Balancing health checks. This ensures that the group can determine an instance's health based on additional tests provided by the load balancer. The load balancer periodically sends pings, attempts connections, or sends requests to test the EC2 instances. These tests are called health checks.

>If you configure the Auto Scaling group to use Elastic Load Balancing health checks, it considers the instance unhealthy if it fails either the EC2 status checks or the load balancer health checks. If you attach multiple load balancers to an Auto Scaling group, all of them must report that the instance is healthy in order for it to consider the instance healthy. If one load balancer reports an instance as unhealthy, the Auto Scaling group replaces the instance, even if other load balancers report it as healthy

![alt](images/asgs-and-healthchecks.png)





References:


https://docs.aws.amazon.com/elasticloadbalancing/latest/classic/elb-healthchecks.html

https://docs.aws.amazon.com/autoscaling/ec2/userguide/as-add-elb-healthcheck.html


Check out this AWS Elastic Load Balancing (ELB) Cheat Sheet:

https://tutorialsdojo.com/aws-cheat-sheet-aws-elastic-load-balancing-elb/

EC2 Instance Health Check vs ELB Health Check vs Auto Scaling and Custom Health Check:

https://tutorialsdojo.com/aws-cheat-sheet-ec2-instance-health-check-vs-elb-health-check-vs-auto-scaling-and-custom-health-check-2/


Here is an additional training material on why an Amazon EC2 Auto Scaling group terminates a healthy instance:

https://youtu.be/_ew-J3DQKZg


### Elastic Load Balancing

- A load balancer accepts incoming traffic from clients and routes requests to its registered targets (such as EC2 instances) in one or more Availability Zones

- When the load balancer detects an unhealthy target, it stops routing traffic to that target. It then resumes routing traffic to that target when it detects that the target is healthy again

- With Application Load Balancers and Network Load Balancers, you register targets in target groups, and route traffic to the target groups.

- With Classic Load Balancers, you register instances with the load balancer.

### Cross Zone Load Balancing

- The nodes for your load balancer distribute requests from clients to registered targets. When cross-zone load balancing is enabled, each load balancer node distributes traffic across the registered targets in all enabled Availability Zones. 
- When cross-zone load balancing is disabled, each load balancer node distributes traffic only across the registered targets in its Availability Zone.
