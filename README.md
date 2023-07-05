# Deploy-a-high-availability-web-app-using-CloudFormation

The 2nd project of Udacity Cloud DevOps Engineer nanodegree

# Problem scenario
Assuming a company is creating an Instagram clone called Udagram
Developers wanted to deploy a new application to the AWS infrastructure.\
My task was to create a high availability infrastructure and deploy it throug AWS using CloudFormation.

## Projoct diagram
![N|Solid](https://github.com/yousefdotpy/Deploy-high-availability-web-app-using-cloud-formation-Udagram/blob/main/Udagram.png?raw=true)

## Project Requirements
## Server specs

- You'll need to create a Launch Configuration for your application servers in order to deploy four servers, two located in each of your private subnets. The launch configuration will be used by an auto-scaling group.

- You'll need two vCPUs and at least 4GB of RAM. The Operating System to be used is Ubuntu 18. So, choose an Instance size and Machine Image (AMI) that best fits this spec.

- Be sure to allocate at least 10GB of disk space so that you don't run into issues. 

## Security Groups and Roles

- Since you will be downloading the application archive from an S3 Bucket, you'll need to create an IAM Role that allows your instances to use the S3 Service.

- Udagram communicates on the default HTTP Port: 80, so your servers will need this inbound port open since you will use it with the Load Balancer and the Load Balancer Health Check. As for outbound, the servers will need unrestricted internet access to be able to download and update their software.

- The load balancer should allow all public traffic (0.0.0.0/0) on port 80 inbound, which is the default HTTP port. Outbound, it will only be using port 80 to reach the internal servers.

- The application needs to be deployed into private subnets with a Load Balancer located in a public subnet.

- One of the output exports of the CloudFormation script should be the public URL of the LoadBalancer. Bonus points if you add http:// in front of the load balancer DNS Name in the output, for convenience.

## Other Considerations

- You can deploy your servers with an SSH Key into Public subnets while you are creating the script. This helps with troubleshooting. Once done, move them to your private subnets and remove the SSH Key from your Launch Configuration.

- It also helps to test directly, without the load balancer. Once you are confident that your server is behaving correctly, increase the instance count and add the load balancer to your script.

- While your instances are in public subnets, you'll also need the SSH port open (port 22) for your access, in case you need to troubleshoot your instances.

- Log information for UserData scripts is located in this file: cloud-init-output.log under the folder: /var/log.

- The provided UserData script should help you install all the required dependencies. Bear in mind that this process takes several minutes to complete. Also, the application takes a few seconds to load. This information is crucial for the settings of your load balancer health check.
