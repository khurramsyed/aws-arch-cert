# AWS Direct Connect
`AWS Direct Connect links your internal network to an AWS Direct Connect location over a standard Ethernet fiber-optic cable`.

One end of the cable is connected to your router, the other to an AWS Direct Connect router. With this connection, you can create virtual interfaces directly to public AWS services (for example, to Amazon S3) or to Amazon VPC, bypassing internet service providers in your network path. An AWS Direct Connect location provides access to AWS in the Region with which it is associated.

![alt](images/direct_connect_overview.png)

### AWS Direct Connect Components

The following are the key components that you use for AWS Direct Connect:

#### Connections
Create a connection in an AWS Direct Connect location to establish a network connection from your premises to an AWS Region. For more information, see AWS Direct Connect Connections.
#### Virtual interfaces
Create a virtual interface to enable access to AWS services. A public virtual interface enables access to public services, such as Amazon S3. A private virtual interface enables access to your VPC. For more information, see AWS Direct Connect Virtual Interfaces and Prerequisites for Virtual Interfaces.
