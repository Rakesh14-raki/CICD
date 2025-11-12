# CICD
https://youtu.be/KzvW0bTqDkA?si=Z5HPLbrRzK8zxuSu
Step 1: Login to AWS Management Console
Open https://aws.amazon.com.
Click Sign in to the Console.
Enter your Email / IAM user and Password.
Once logged in, you’ll see the AWS Management Console Dashboard.


Step 2: Create a Virtual Private Cloud (VPC)
Go to VPC → Your VPCs → Create VPC.
Choose VPC only option.
Set:
Name: MyVPC
IPv4 CIDR: 10.0.0.0/16
Click Create VPC.

Step 3: Create a Public Subnet
Go to Subnets → Create Subnet.
Select the VPC created earlier (MyVPC).
Add:
Subnet Name: PublicSubnet
IPv4 CIDR block: 10.0.1.0/24
Availability Zone:  ap-south-1a
Click Create Subnet.

Step 4: Create and Attach Internet Gateway
Go to Internet Gateways → Create Internet Gateway.
Name it MyIGW and click Create.
Select Actions → Attach to VPC → MyVPC.

Step 5: Configure Route Table
Go to Route Tables.
Select the default route table linked with your VPC.
Go to Routes → Edit routes → Add route:
Destination: 0.0.0.0/0
Target: Internet Gateway (MyIGW)
Save the route.
Go to Subnet Associations → Edit Subnet Associations → select PublicSubnet → Save.

Step 6: Launch Windows Server EC2 Instance
Go to EC2 → Launch Instance.
Enter name: WindowsServer-Lab.
Choose Windows Server 2022 Base AMI.
Select t2.micro instance type (free tier).
Under Network Settings:
Select MyVPC.
Select PublicSubnet.
Enable Auto-assign Public IP.
Create a new Security Group:
Allow RDP (TCP 3389) from My IP.
Choose or create a Key Pair (download .pem file).
Click Launch Instance.


Step 7: Verify the Instance
Go to EC2 → Instances → Running Instances.
Wait until Status = Running.
Note down the Public IPv4 address.




Step 9: Verify Connectivity
Open Command Prompt or Browser inside the server.
Try pinging any website (e.g., ping google.com) or open a browser to verify internet access.
