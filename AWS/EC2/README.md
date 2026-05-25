## EC2 --> Elastic Compute Cloud 
https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/concepts.html

Instances:- Virtual servers that run applications on the Amazon Web Services (AWS) infrastructure.

Amazon Machine Images (AMIs):- Preconfigured templates for your instances that package the components you need for your server (including the operating system and additional software).

Instance types:- Various configurations of CPU, memory, storage, networking capacity, and graphics hardware for your instances.

Amazon EBS volumes:- Persistent storage volumes for your data using Amazon Elastic Block Store (Amazon EBS).

Instance store volumes:- Storage volumes for temporary data that is deleted when you stop, hibernate, or terminate your instance.

Key pairs:- Secure login information for your instances. AWS stores the public key and you store the private key in a secure place.

Security groups:- A virtual firewall that allows you to specify the protocols, ports, and source IP ranges that can reach your instances, and the destination IP ranges to which your instances can connect.

region vs AZ:-(https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-regions-availability-zones.html)

Regions are separate geographic areas.
Availability Zones are multiple, isolated locations within each Region.

https://docs.aws.amazon.com/ebs/latest/userguide/ebs-volumes.html
##ebs volume:
An Amazon EBS volume is a durable, block-level storage device that you can attach to your instances. 
After you attach a volume to an instance, you can use it as you would use a physical hard drive. EBS volumes are flexible.

Amazon Machine Image:https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AMIs.html
An Amazon Machine Image (AMI) is an image that provides the software that is required to set up and boot an Amazon EC2 instance.


key pair: https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-key-pairs.html
A key pair, consisting of a public key and a private key, is a set of security credentials that you use to prove your identity when connecting to an Amazon EC2 instance.

security group:https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-security-groups.html
A security group acts as a virtual firewall for your EC2 instances to control incoming and outgoing traffic. Inbound rules control the incoming traffic to your instance, and outbound rules control the outgoing traffic from your instance. 

