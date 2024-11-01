---
title: "A Beginner's Guide to Creating an Amazon EC2 Instance"
seoTitle: "Create an Amazon EC2 Instance: A Beginner's Guide"
seoDescription: "Learn to create an Amazon EC2 instance with this step-by-step beginner's guide, perfect for exploring AWS cloud capabilities"
datePublished: Fri Nov 01 2024 18:29:27 GMT+0000 (Coordinated Universal Time)
cuid: cm2z2jnnr000009lb2axhhqbn
slug: a-beginners-guide-to-creating-an-amazon-ec2-instance
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1730485723158/f9009103-ecf9-4b01-8a5c-d0e93a6eaffb.jpeg
tags: ec2, linux, aws, devops

---

Amazon Elastic Compute Cloud (EC2) is a web service that provides resizable compute capacity in the cloud. It allows you to run virtual servers and is ideal for hosting applications, running websites, or conducting research. This guide will walk you through the steps to create an EC2 instance, perfect for beginners looking to explore AWS.

## Step 1: Sign Up for AWS

1. **Visit the AWS Website**: Go to the [AWS homepage](https://aws.amazon.com/).
    
2. **Create an Account**: Click on “Create a Free Account” and follow the prompts. You’ll need to provide an email address, a password, and some basic information.
    
3. **Select a Support Plan**: For beginners, the free tier plan is sufficient, which allows you to experiment without incurring charges.
    
4. **Enter Payment Information**: Even for the free tier, AWS requires a credit card for verification.
    
5. **Complete the Sign-Up Process**: Verify your identity through a phone call or SMS, and finalize your account setup.
    

## Step 2: Access the AWS Management Console

1. **Log In to AWS**: Use your credentials to log in to the AWS Management Console.
    
2. **Navigate to EC2**: From the console, type “EC2” in the search bar or find it under the “Services” menu. Click on “EC2” to open the EC2 Dashboard.
    

## Step 3: Launch an EC2 Instance

1. **Click on “Launch Instance”**: This button is usually prominently displayed on the EC2 Dashboard.
    
2. **Choose an Amazon Machine Image (AMI)**:
    
    * An AMI is a pre-configured template for your instance. For beginners, selecting the Amazon Linux 2 AMI or Ubuntu Server 20.04 LTS is a good choice. Click “Select” next to your preferred AMI.
        
3. **Choose an Instance Type**:
    
    * Instance types define the hardware of your instance. For general use, the “t2.micro” instance type is eligible for the free tier. Click “Next: Configure Instance Details” after selecting.
        
4. **Configure Instance Details**:
    
    * Keep the default settings unless you have specific requirements. Click “Next: Add Storage.”
        
5. **Add Storage**:
    
    * The default storage (8 GB) is typically sufficient for basic tasks. Adjust if needed, then click “Next: Add Tags.”
        
6. **Add Tags**:
    
    * Tags help you identify your instances. Click “Add Tag,” set a key (e.g., "Name") and a value (e.g., "MyFirstInstance"). Click “Next: Configure Security Group.”
        
7. **Configure Security Group**:
    
    * Security groups act as a firewall for your instance. Create a new security group and add rules to allow traffic. For beginners, allow SSH (port 22) from your IP address and HTTP (port 80) for web traffic. Click “Review and Launch.”
        
8. **Review Your Configuration**: Check all settings to ensure everything is correct. Click “Launch.”
    

## Step 4: Key Pair Creation

1. **Create a Key Pair**:
    
    * A key pair is necessary for securely connecting to your instance. Choose “Create a new key pair,” name it, and click “Download Key Pair.” **Save this** `.pem` file securely; you won’t be able to download it again.
        
2. **Launch the Instance**: Click “Launch Instances” to start your instance.
    

## Step 5: Access Your EC2 Instance

1. **Find Your Instance**: Once the instance is running, go back to the EC2 Dashboard and click “Instances.” Your new instance will appear in the list.
    
2. **Connect to Your Instance**:
    
    * Select your instance and click the “Connect” button.
        
    * Follow the instructions provided in the Connect dialog. You will generally use SSH (for Linux) to connect:
        
        * Open a terminal (or use PuTTY on Windows).
            
        * Navigate to the directory where you saved your `.pem` file.
            
        * Use the following command to connect:
            

> You will need to convert the `pem to ppk` if using the `Putty` for SSH.
> 
> You can also use other terminals like `MobaXterm` & `Git Bash`

```bash
ssh -i /path/to/your-key-pair.pem ec2-user@your-instance-public-dns
```

* Replace `/path/to/your-key-pair.pem` with the path to your key file, and `your-instance-public-dns` with the public DNS address of your instance.
    

## Step 6: Explore Your Instance

Once connected, you can start exploring your EC2 instance:

* **Update the Package Index**:
    
    ```bash
    sudo yum update -y   # For Amazon Linux
    sudo apt update -y   # For Ubuntu
    ```
    
* **Install Software**: Use package managers like `yum` or `apt` to install applications. For example:
    
    ```bash
    sudo yum install httpd -y   # Install Apache on Amazon Linux
    sudo apt install apache2 -y  # Install Apache on Ubuntu
    ```
    

## Step 7: Terminate Your Instance

After you’ve finished exploring:

1. **Go back to the EC2 Dashboard**: Select your instance.
    
2. **Click “Instance State”**: Choose “Terminate Instance” to stop billing. Confirm your action.
    

> If you keep your Instance in stop state, then also AWS will charge you minimal amount for the IP and storage.

## Conclusion

Congratulations! You have successfully created and accessed your first EC2 instance. This guide has introduced you to the basics of AWS EC2, and you can now explore further by deploying applications, creating additional instances, or learning about advanced features like Elastic Load Balancing or Auto Scaling. AWS offers a wealth of services and resources to help you grow your cloud computing skills. Happy exploring!