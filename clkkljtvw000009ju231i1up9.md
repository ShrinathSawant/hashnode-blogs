---
title: ""Mastering AWS: A Step-by-Step Guide to Launching EC2 Instances and Connecting via SSM(Systems Manager)" 💻🚀"
datePublished: Thu Jul 27 2023 03:30:13 GMT+0000 (Coordinated Universal Time)
cuid: clkkljtvw000009ju231i1up9
slug: mastering-aws-a-step-by-step-guide-to-launching-ec2-instances-and-connecting-via-ssmsystems-manager
tags: aws, cloud-computing, devops

---

### **Step 1: Create an IAM Role for SSM**

Before we dive into launching an EC2 instance, we must first ensure that we have the appropriate IAM (Identity and Access Management) role in place. This role will allow SSM to interact with our EC2 instance.

* Navigate to the IAM dashboard in the AWS console and create an EC2 role.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690382737894/46d627e8-8126-4f7b-a44d-8992955dd7b8.png align="center")

* Select 'AWS service' as the type of trusted entity, then choose 'EC2'.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690382998929/994c03db-b2d1-489c-834e-a95b71ac5932.png align="center")

* When adding permissions, include the following AWS-managed policies.
    

**AmazonSSMManagedInstanceCore**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690383497503/470a47fe-ba76-4e3c-879e-60b5cb54007d.png align="center")

* Give your role a name, review and then click **Create Role**.
    

### **Step 2: Launch an EC2 Instance 🚀💻**

Now, let's launch our EC2 instance:

* Navigate to the EC2 dashboard in the AWS Management Console and click 'Launch Instance'.
    
* Choose your preferred Amazon Machine Image (AMI) and instance type based on your computing requirements.
    
* In the 'Configure Instance Details' section, choose the IAM role you created earlier from the IAM role dropdown menu.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690383850265/6e2ffd28-04a2-474c-a0af-e5827f49d3f5.png align="center")
    
* Continue through the wizard, setting up storage, adding tags, and configuring the security group as needed.
    
* Review and launch the instance.
    

### **Step 3: Connect to the EC2 Instance using SSM 🌐⚙️**

With our EC2 instance up and running, it's time to connect using SSM:

* Once you've selected your instance, click on the 'Connect' button.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690384350974/a66ee093-1e18-44a1-a3d9-75c08e7de129.png align="center")
    
* A new window will pop up. Here, choose 'Session Manager' in the 'Connect To Your Instance' section.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690384550175/cf025d0e-0724-4eb2-8a61-fabbd4951fb5.png align="center")
    

This process allows you to manage your instance directly from your browser, without the need for SSH keys or remote shell software. Happy managing! 🚀💼