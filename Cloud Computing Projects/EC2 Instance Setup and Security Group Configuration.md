### **Project Analysis: EC2 Instance Setup and Security Group Configuration**

**By Ekeoma Miracle**

#### **Objective:**

The goal of this project was to create and configure an EC2 instance using Amazon Linux 2, specifically selecting the **t3.micro** instance type, and configuring a **security group** with no inbound rules, blocking all incoming traffic, including SSH. The objective was also to test the connectivity using **PuTTY**, **Command Prompt**, and **Git Bash**, with a private key (`.ppk`), to verify access restrictions.

#### 

#### **1\. Instance Setup:**

* **AMI (Amazon Machine Image):** Amazon Linux 2

  * Chosen for its lightweight nature and compatibility with AWS infrastructure.

* **Instance Type:** t3.micro

  * The **t3.micro** instance type was selected, which is ideal for low-traffic applications and is eligible for the AWS Free Tier.

#### **2\. Security Group Configuration:**

* A **custom security group** was created with **no inbound rules**.

  * **No inbound traffic allowed**: This means that no external connections are permitted to reach the instance, including SSH (port 22).

  * **No outbound traffic restrictions**: The instance is allowed to initiate outbound connections.

#### **3\. Access Method:**

* **Private Key (.ppk):**

  * A private key was generated and downloaded in `.ppk` format (compatible with PuTTY) for SSH authentication.

  * This key was used for testing access through different methods (PuTTY, Command Prompt, and Git Bash).

#### **4\. Testing Access:**

Testing was done with the following tools:

* **PuTTY:**

  * PuTTY is a popular SSH client for Windows. Using the `.ppk` file, an attempt was made to connect to the EC2 instance.

  * **Result:** Since no inbound rules were configured in the security group, the connection attempt was blocked, as expected.

* **Command Prompt (Windows):**

  * The `ssh` command was attempted from the Windows Command Prompt, using the private key to access the EC2 instance.

  * **Result:** The connection attempt failed due to the security group blocking inbound SSH traffic.

* **Git Bash:**

  * Git Bash, which supports SSH, was used to attempt a connection with the private key.

  * **Result:** The connection attempt failed because the security group blocked SSH traffic.

#### **5\. Observations and Analysis:**

* **Security Group Effectiveness:**

  * The security group configuration with no inbound rules effectively blocked all incoming traffic, as evidenced by the failed connection attempts.

  * This demonstrated the critical role that security groups play in controlling access to EC2 instances and validating AWS best practices for securing resources.

* **SSH Authentication:**

  * Despite the use of correct authentication keys, access was not possible because the security group blocked SSH access (even though the key was valid).

  * This emphasizes the importance of both security group configurations and correct key management in ensuring access to EC2 instances.

#### **6\. Conclusion and Next Steps:**

* **Current Status:**

  * The project successfully validated that **no inbound traffic** (including SSH) could access the EC2 instance due to the restrictive security group configuration.

* **Next Steps:**

  * **Update Security Group:** For proper access, inbound rules for port 22 (SSH) should be configured to allow SSH connections from specific IP addresses.

  * **Test SSH Access Again:** After adjusting the security group, test SSH connectivity using the same tools (PuTTY, Command Prompt, Git Bash) to ensure access is functional.

#### **Lessons Learned:**

* **Security Group Configurations:** Properly configuring inbound and outbound rules is essential to ensure that an EC2 instance is properly secured and only accessible by authorized users.

* **Access Methods:** Understanding different tools for SSH access (like PuTTY, Command Prompt, and Git Bash) and their respective configurations (private key handling) is key to troubleshooting and verifying access.

This project serves as a reminder of the importance of correct security configurations in cloud environments, particularly when dealing with access to sensitive instances like EC2.

[AWS](https://github.com/orjimiracle/Cybersecurity/blob/99076b8c084084a7828c7185f8cd73e733045a64/images/users.jpg)

