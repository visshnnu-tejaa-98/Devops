# Activity 14

set up a VPC with an Internet gateway, create a public subnet, a private subnet make a route table connecting the Internet gateway and the subnets, and launch a Linux EC2 instance by using the above vpc and public subnet.

## Step 1: Creating VPC

- Open VPC Dashboard
- Click on **Create VPC** button

  ![alt text](/images/Activity14/create-vpc-btn.png)

* Select **VPC Only** > Give name of VPC > give IPv4 CIDR Value as **10.0.0.0/16** > click on **Create VPC** button

  ![alt text](/images/Activity14/create-vpc.png)

## Step 2: Creating Subnets

- Here we are going to create 3 subnets one as public and remaining 2 as private subnet

* Go to Subnets dashboard > click on **create subnts** button

  ![alt text](/images/Activity14/create-subnets-btn.png)

* Give the VPC name (whixh is newly created)
* Give subnet name (my-subnet-1) > select the CIDR range as **10.0.1.0/24**
* Select Availability zone as **us-east-1a**
* click on **create subnet** button
* similarly you can reeate other 2 subnets

  ![alt text](/images/Activity14/subnets-list.png)

## Step 3: Create Security Group

- Go to security dashboard > click on **create security group** button
  ![alt text](/images/Activity14/security-group-btn.png)

- Give Security group name > Allow all tcp from all ipv4 address in inbound and outbound rules
- click on **create security** group button

  ![alt text](/images/Activity14/security%20groups.png)

## Step 4: Create internet gateway and attaching to VPC

- Go to internet gateway dashboard > click on create **internet gateway** button

  ![alt text](/images/Activity14/igw-btn.png)

- Give igw name > click on **create Internet gateway** button

- Here a popup will come to **Attach to VPC** > click on it and attach to VPC

  ![alt text](/images/Activity14/igw-vpc.png)

## Step 5: Creating route table and associate to subnet 1

- Go to route table dashboard > click on **create route table** button

  ![alt text](/images/Activity14/route-table-btn.png)

- Give Name of the route table
- Select our VPC > click on **create route table** button

- Open that route table > click on subnet associations > edit the subnet associations > select **subnet 1** and click on **Save associations** button

  ![alt text](/images/Activity14/associations.png)

* Click on **routes** > edit **routes** > add route

* give **0.0.0.0/0** for destination field and give **internet gatway** as a target
* click on **save changes** button

  ![alt text](/images/Activity14/routs.png)

## Step 6: Creating NAT gateway

- Go to NAT gateway dashboard > click on create **NAT gateway** button

  ![alt text](/images/Activity14/nat-gateway-btn.png)

- Give NAT gateway name > select subnet (publicsubnet - subnet 1)
- This can help to get internet from public subnet and give internet to private subnet
- click on **Allocate Elastic ip** (this is chargable)
- click on **create NAt Gateway** button

  ![alt text](/images/Activity14/nat-gateway.png)

## Step 7: Create a connection between nat gateway to private subnet

- Go to route table dashboard > click on **create route table** button

  ![alt text](/images/Activity14/route-table-btn.png)

- Give route table name > select our vpc
- click on **create route table** button
- Open that route table > click on subnet associations > edit the subnet associations > select **subnet 2** and click on **Save associations** button
- Click on **routes** > edit **routes** > add route

- give **0.0.0.0/0** for destination field and give **NAT gateway** as a target
- click on **save changes** button

  ![alt text](/images/Activity14/associate-nat-gateway.png)

## Step 8: Create NACL

- Go to NACL dashboard > click on **create Nacl** button
- Give NACL name > select your vpc > click on **Create NACL** button
- Here inbound and outbound rules are denyed > allow both rules for all traffic

## Step 9: Create an EC2 instance and connecting to private subnet

- Go to EC2 Dashboard > click on **Launch instance** button

  ![alt text](/images/Activity14/launch-instance-btn.png)

- Launch ec2 intance with ubuntu image by selecting newly created vpc with public subnet (subnet-1)
- Also enable public ip in network section (Auto assign public ip), select subnet1
  ![alt text](/images/Activity14/enable-public-ip.png)

* connect the ec2 server using instance connect and perform the below commands

```bash
    # Open
    vi key.pem
    # Copy the content in key key.pem file to here
    # Change permessions to 400
    chmod 400 key.pem
    # Connecting to private subnet ec2 instance
    ssh -i key.pem ubuntu@<private_ip>
```

- Now, try to access the internet from private instance using **ping** command

  ![alt text](/images/Activity14/connecting-to-private.png)

- hecking the internet in private server

  ![alt text](/images/Activity14/ping.png)

Now, You are able to access the internet from an ec2 instance which is present in private subnet
