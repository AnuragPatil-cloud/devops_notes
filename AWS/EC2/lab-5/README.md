# purchesing Option 

https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instance-purchasing-options.html

Spot Requests :-
A Spot Instance is an instance that uses spare EC2 capacity that 
is available for less than the On-Demand price.
Use unused EC2 capacity at up to 90% cheaper than On-Demand.
Instance can be terminated anytime if capacity/price changes.
Kubernetes clusters , CI/CD pipelines

Savings Plans:-
for a 1 or 3 year term.
Savings Plans are a flexible pricing model that offer low prices on EC2
SaaS companies running steady workloads (web apps, APIs).
Startups that want cost savings.


Reserved Instances:-
Commit to specific instance type + region + tecost rm (1 or 3 years).
Up to 72% cheaper than On-Demand 
Databases , ERP/CRM applications that run 24/7 (jio,airtel,vi,bsnl)

(server racks)
Dedicated Hosts:-                                                                                  shared Host:?     (server racks)
Physical server fully allocated to you.
Highest cost but compliance & isolation benefits.
Banking/Finance 
Healthcare 

Capacity Reservations:-(capacity garenty) 
without resurving only for few days and perticular shedule 
Reserve EC2 capacity in a specific AZ for any duration.
Disaster Recovery setups 
Event-based apps (tikit booking apps)
