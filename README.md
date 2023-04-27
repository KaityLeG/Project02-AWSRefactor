# Project02-AWSRefactor

<p align="center">

This project focuses on the refactoring or re-architecting of Multi-tier web application.
Refactoring refers to when you reconstruct and improve a code’s internal structure without actually changing how the code behaves. The code will operate how it usually does, but in a more improved and agile way. You can add new features, scale effectively, have better performance for the application workload. This method aims to boost agility and improve business continuity.
</p>

**EXAMPLE:**
<p>
You have a project that has various services running on physical/virtual/ cloud machines.
And to manage all of it it many require multiple teams to handle it.
The problem with this would be too much operational overhead
Struggling with uptime and scaling.
Upfront Capital expenses and regular operational expenses,
Using local data centers which will be difficult to automate.
  </p>

**SOLUTION:**
* A cloud platform using PAAS and SAAS services from AWS. Flexible and elastic.
* Infrastructure as code
* Pay as you go

This gives ease of infrastructure management that will be easy to use and will not require so many teams.


 **OBJECTIVE:**

* FLEXIBLE INFRASTRUCTURE
* NO UPFRONT COST
* IAAC
* PAAS
* SAAS
</p>

**AWS Cloud services used:**
* Elastic Beanstalk
* AWS Relational Database
* Elasticache
* Route 53
* Amazon MQ
* CloudFront
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRFDiagram.drawio.png"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF1.png" width="700"  title="hover text">
  </p>
  <p align="center">
  First, create a security group for all the backend services. I chose the default VPC.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF2.png" width="700"  title="hover text">
  </p>
  <p align="center">
  The inbound rules for this security group will be SSH as a dummy rule. Then add All traffic and the source will be to intself. So that the traffic can route into itself.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF3.png" width="700"  title="hover text">
  </p>
  <p align="center">
  Now, to create the Database subnet group. Again choosing the default VPC.
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF4.png" width="700"  title="hover text">
  </p>
  <p align="center">
  Now, to create the paramaters for the database subnet group. These parameters will apply to the database when you attach it.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF5.png" width="700"  title="hover text">
  </p>
  <p align="center">
  Here, we will now create the actual AWS RDS database. Create the name. The username login will be "admin" and the password will be auto-generated.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF6.png" width="700"  title="hover text">
  </p>
  <p align="center">
  Choose burstible classes with a t2.mirco size. This project will not need much storage.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF7.png" width="700"  title="hover text">
  </p>
  <p align="center">
  For stage I choose General Purpose SSD. This will serve a general web application. I allocated 20 GiB. Again, this will not need alot of storage for this particular project. I enabled autoscaling for the database so it can scale according to the read and writes the application recieves. So you will not need to worry about a crashing application.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF8.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF9.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF10.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF11.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF12.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF13.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF14.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF15.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF16.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF17.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF18.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF19.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF20.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF21.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF22.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF23.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF24.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF25.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF26.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF27.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF28.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF29.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF30.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF31.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF32.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF33.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF34.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF35.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF36.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF37.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF38.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF39.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF40.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF41.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF42.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF43.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF44.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF45.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF46.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF47.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF48.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF49.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF50.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF51.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF52.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF53.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF54.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF55.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF56.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF57.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF58.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF59.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF60.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF61.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF62.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF63.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF64.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF65.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF66.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF67.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF68.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF69.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF75.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF76.png" width="700"  title="hover text">
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF77.png" width="700"  title="hover text">
  </p>
  
