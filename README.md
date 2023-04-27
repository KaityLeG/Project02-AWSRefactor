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

***

<p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRFDiagram.drawio.png"  title="hover text">
  </p>
  
  ***
  
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
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF5.png" width="700"  title="hover text">
  </p>
  <p align="center">
  Now, to create the paramaters for the database subnet group. These parameters will apply to the database when you attach it.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF6.png" width="700"  title="hover text">
  </p>
  <p align="center">
  Here, we will now create the actual AWS RDS database. Create the name. The username login will be "admin" and the password will be auto-generated.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF7.png" width="700"  title="hover text">
  </p>
   <p align="center">
  Choose burstible classes with a t2.mirco size. This project will not need much storage.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF8.png" width="700"  title="hover text">
  </p>
   <p align="center">
  For stage I choose General Purpose SSD. This will serve a general web application. I allocated 20 GiB. Again, this will not need alot of storage for this particular project. I enabled autoscaling for the database so it can scale according to the read and writes the application recieves. So you will not need to worry about a crashing application.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF9.png" width="700"  title="hover text">
  </p>
  <p align="center">
  The connectivty settings, we will not connecft to an ec2 insatnce and keep the network type IPv4. Chose the default VPC once again. Select the DB subnet group we made earlier.
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF10.png" width="700"  title="hover text">
  </p>
  <p align="center">
  For this, we will not be allowing public access to the databse. Only other AWS services will be able to communicate with the DB. Choose an exiting VPC secrity group which is the security group for the backend services created earlier.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF11.png" width="700"  title="hover text">
  </p>
  <p align="center">
  Click "Password authentication" so there will be a security measure of authenticating using database passwords. For Monitoring, it will be enabled to take a closer look at the performance and metrics of the database.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF12.png" width="700"  title="hover text">
  </p>
  <p align="center">
  For the actual database, here it will be named "accounts". As in created accounts. Apply the DB parameter group that was created. Automated backups are enabled.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF13.png" width="700"  title="hover text">
  </p>
  <p align="center">
  Checking all the boxes to be able to log events to CloudWatch.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF14.png" width="700"  title="hover text">
  </p>
  <p align="center">
  Now Go to Elasticache and create a parameter group for the service.
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF15.png" width="700"  title="hover text">
  </p>
  <p align="center">
  Create the Elasticache subnet group just like we did the RDS database subnet group. Choose the default VPC again.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF16.png" width="700"  title="hover text">
  </p>
  <p align="center">
 Now to create the Elasticache cluster. It will be on the cloud of course, and we will name it.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF17.png" width="700"  title="hover text">
  </p>
  <p align="center">
  For the cluster settings I choose the version 1.4.5 for this. The port will be on 11211 the memcached port. Select the parameter group we created for memcached. Choose t2.micro for the Node. And there will be one node.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF18.png" width="700"  title="hover text">
  </p>
  <p align="center">
  The subnet settings, Choose the existing subnet group created for memcached. I choose the associate subnets with all the availibility zones in the east.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF20.png" width="700"  title="hover text">
  </p>
  <p align="center">
  In the advanced settings, go to Security and click "Manage" and add the security group for the backend services that was created earlier. If you have SNS notificationsenabled you can add it and recieve emails.
 </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF21.png" width="700"  title="hover text">
  </p>
  <p align="center">
  Now that Elasticache has been configured. Let's go to "Amazon MQ" and select RabbitMQ.
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF22.png" width="700"  title="hover text">
  </p>
  <p align="center">
  Select Single-instance broker. This project is small so we will not need cluster deployment. But for production purposes it is useful.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF23.png" width="700"  title="hover text">
  </p>
  <p align="center">
  In Configure Settings, confirm settings for the Broker.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF24.png" width="700"  title="hover text">
  </p>
  <p align="center">
  Create the username. I used "rabbit". Create a password.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF25.png" width="700"  title="hover text">
  </p>
  <p align="center">
  Choose the engine version, Allow only proivate access and use the default VPC and subnets. Select the existing security group. And choose the security group for the backend services created earlier.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF26.png" width="700"  title="hover text">
  </p>
  <p align="center">
  Choose the settings and allow maintenance upgrades. Choose AWS owned CMK.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF27.png" width="700"  title="hover text">
  </p>
  <p align="center">
  Go to the Amazon MQ broker just created and find the Endpoint of the broker. Copy it and keep it noted, it will we used later on.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF28.png" width="700"  title="hover text">
  </p>
  <p align="center">
  Now go to EC2 instances and create an EC2 instance to log in and intialize the RDS Database created earlier. I named it "my-sql-client". You can choose any OS but for this I chose Ubuntu. For any one you choose just make sure you understand how it works.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF29.png" width="700"  title="hover text">
  </p>
  <p align="center">
  Log into the EC2 instance created to intialize the database and run these commands to update packages first. Keep in mind this is for Ubuntu. Update according to the OS you used for this EC2 instance. Here I also installed mysql to the instance. For linux it will be different. it will be maria-db instead of mysql-client. 
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF30.png" width="700"  title="hover text">
  </p>
  <p align="center">
  Now, go back to the backend security group and add MySQL/Aurora port to the EC2 instance that was just created.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF31.png" width="700"  title="hover text">
  </p>
  <p align="center">
  Use the command above to log into the mysql database created. Use the user "admin" and the generated password RDS gave when we selected it and the RDS was created.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF32.png" width="700"  title="hover text">
  </p>
  <p align="center">
  Use the "show databases;" command to show the databases created. Here you should see the "accounts" database that was created in RDS.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF33.png" width="700"  title="hover text">
  </p>
  <p align="center">
  I took the the source code of the project and cloned it in the EC2 instance.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF34.png" width="700"  title="hover text">
  </p>
  <p align="center">
  I went to the project branch and selected AWSRefactor.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF35.png" width="700"  title="hover text">
  </p>
  <p align="center">
  CD into the main/resources/ directory and you should see db_back.sql file here.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF36.png" width="700"  title="hover text">
  </p>
  <p align="center">
  Get the endpoint URL of the RDS database. Run this command with the proper username and password of your database you created. This command will basically input the "accounts" database to this file.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF37.png" width="700"  title="hover text">
  </p>
   <p align="center">
  Now run this command which will log into the accounts database.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF38.png" width="700"  title="hover text">
  </p>
   <p align="center">
  run the command "show tables;" and the "Accounts" table will now be shown. The database is now working and intialized.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF39.png" width="700"  title="hover text">
  </p>
  <p align="center">
  Go to AmazonMQ and go to RabbitMQ that was created and grab the endpoint. It will be useful later on.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF40.png" width="700"  title="hover text">
  </p>
  <p align="center">
  Go to Elasticache and grab the endpoint for this as well. It will be useful late on.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF41.png" width="700"  title="hover text">
  </p>
  <p align="center">
  Go to Elastic Beanstalk and we will now create the container for the application.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF42.png" width="700"  title="hover text">
  </p>
  <p align="center">
  The platform that will be used is Tomcat for the java application we will be deploying. For now, choose Sample code and will uplaod the application code later.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF43.png" width="700"  title="hover text">
  </p>
  <p align="center">
  Go to Configuration settings before you save the changes. For the security group choose the security group for the backend services.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF44.png" width="700"  title="hover text">
  </p>
  <p align="center">
  For the auto-scaling component, Choose Load balanced and here I chose a Min of 2 and Max of 8 instances that will scale.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF45.png" width="700"  title="hover text">
  </p>
  <p align="center">
  For the instance type, choose t2.micro and choose Any for availibility zones.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF46.png" width="700"  title="hover text">
  </p>
  <p align="center">
  For the Scaling triggers, Choosing NetworkOut will scaling OUT depend on network traffic.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF47.png" width="700"  title="hover text">
  </p>
  <p align="center">
  For Application Deployments, choose Rolling. Rolling deployment will keep downtine to a minimum by rotating out instances as they are updated so a version of the application will always be up and running until all the latest changes to the application instances are applied. It will delete old instances and add new ones, completing the update cycle and the user will experience very minimum downtime if none at all. a 50% percentage will keep half of the instances up and leave the other half to be updated at a time.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF48.png" width="700"  title="hover text">
  </p>
  <p align="center">
  In Modify security, the service role of elastic beanstalk will be applied. Choose a keypair and if there is an elastic beanstalk IAM profile created for you choose it for the instance profile. If not, leave it blank.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF49.png" width="700"  title="hover text">
  </p>
  <p align="center">
  The Environment should now be up and running.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF50.png" width="700"  title="hover text">
  </p>
  <p align="center">
  Edit the inbound rules of the backend security group and connect the backend services to the elastic beanstalk security group created.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF51.png" width="700"  title="hover text">
  </p>
  <p align="center">
  Including Elasticache, RDS, Rabbit MQ ports.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF52.png" width="700"  title="hover text">
  </p>
  <p align="center">
  Go the the Configuration of the environment and created a listener of 443. and select an SSL certificiate you have created in Route 53. 
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF53.png" width="700"  title="hover text">
  </p>
  <p align="center">
  Go to the Processes, and edit port 80.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF54.png" width="700"  title="hover text">
  </p>
  <p align="center">
  For the health check, we will allow the Path to be /login. That is where the health check will take place on the application. Save.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF55.png" width="700"  title="hover text">
  </p>
  <p align="center">
  Enable stickiness that will allow caching and remember user data for each session the user create. 
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF56.png" width="700"  title="hover text">
  </p>
  <p align="center">
  Going back to the terminal and going back into the project source code by going back to the branch.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF57.png" width="700"  title="hover text">
  </p>
  <p align="center">
  Go back to the refactor project branch.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF58.png" width="700"  title="hover text">
  </p>
  <p align="center">
  CD back into the src/main/resources/ folder. Here is the applcation.properties. I went into vim editor to modify the details and insert the endpoints I grabbed for each service I created.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF59.png" width="700"  title="hover text">
  </p>
  <p align="center">
  I configured the details of the database connection and inserted my endpoints, and username and password for RabbitMQ for a proper connection. 
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF60.png" width="700"  title="hover text">
  </p>
  <p align="center">
  Here we will run "mvn install" to run a build test and create a .war file if all is successful. This will package the java application.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF61.png" width="700"  title="hover text">
  </p>
  <p align="center">
  Here the build was a success. I moved into the target folder and as seen here, the application was packaged into a .war file.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF62.png" width="700"  title="hover text">
  </p>
  <p align="center">
  I made my way back to Elastic Beanstalk, clicked the environment to upload a version. upload the .war file and now a new version of the application will be deployed.
 </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF63.png" width="700"  title="hover text">
  </p>
  <p align="center">
  The version is now uploaded. I now click Deploy.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF64.png" width="700"  title="hover text">
  </p>
  <p align="center">
  Here, this is an example of the Rolling deployment that took place on this application. You can see two Batches weere created. The first batch was the first batch of instances that recieved the update. After completed it took the second batch and performed the same application version update.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF65.png" width="700"  title="hover text">
  </p>
  <p align="center">
  Grab the elastic beanstalk URL. Here is the live website. It is no longer a sample code. This is the updated version and now an actual application using all the backend services we created.
 </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF66.png" width="700"  title="hover text">
  </p>
  <p align="center">
  Now, I will route it using a DNS name created with GoDaddy(ktdevops.com). I clicked Add New Record.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF67.png" width="700"  title="hover text">
  </p>
  <p align="center">
  The new record will be a CNAME, give it anyname you please, and insert the Elastic Beanstalk endpoint in the Value block.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF68.png" width="700"  title="hover text">
  </p>
  As you can see, I typed in the new CNAME record in the URL bar and it routed the website to it.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF69.png" width="700"  title="hover text">
  </p>
  <p align="center">
  Go back to Elastic Beanstalk and go into the configuration and go to Processes. Click Edit. Make sure that stickiness is enabled.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF75.png" width="700"  title="hover text">
  </p>
  <p align="center">
  Here, I created a CloudFront distribution. This will allow users to access the application in the fastest way possible. The reason that it will be helpful is that a CDN like CloudFront will send the info that is cached data from the nearest edge location. That way, users will not have to make its way back to the application completely. It will route to cloudfront first to recieve information thats has been accessed once before.
</p>
<p align="center">
  For Origin, choose the DNS record we created and just accessed.
  For Protocol, chose Match Viewer. So that which ever one the user accesses it will be able to serve. Whether its HTTP or HTTPS.
  Chose the SSL protocol.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF76.png" width="700"  title="hover text">
  </p>
  Dont need to edit Origin path because it will already route to /login. I created the name as the DNS name. Didnt enable Origin shield for this project. For the Default cache behavior, these are the settings.
  </p>
  <p align="center">
  <img src="https://raw.githubusercontent.com/KaityLeG/Project02-AWSRefactor/main/images/AWSRF77.png" width="700"  title="hover text">
  </p>
  <p align="center">
  For the Cache policy I chose CacheOptimized. This now created CloudFront will allow traffic to recieve the application in a much faster and improved way.
  
  <p align="center">
    This project is now completed and you can now see with the combination of PAAS and SAAS services from AWS this project remained the same but internally it behaves with better performance and easier to manage.
    </p>
  
