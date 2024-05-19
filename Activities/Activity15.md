# Activity 15

1. Create a S3 bucket, with no public access and upload files to the bucket & view the logs for the uploaded files.
2. Launch two ec2-instances and connect it to a application load balancer, where the output traffic from the server must be an load balancer IP address

## Step 1: Creating 2 S3 Buckets (src and destination buckets)

1. Go to S3 Dashboard
2. Click on **create bucket** button
3. Select **General Purpose** as Bucket type
4. Give Bucket name
5. Click on **create bucket** button

   ![alt text](/images/Activity15/src-create.png)

6. Similarly create a destination bucket

   ![alt text](/images/Activity15/dest-create.png)

## Step 2: Enabling the logs in src bucket

1. Go to **src** bucket
2. Click on **properties** tab
3. Go to server **access logging** section and enable it

   ![alt text](/images/Activity15/access-server-logging.png)

## Step 3: Uploading files in src bucket

1. Go to **src** bucket
2. click on **upload** button and upload couple of files

   ![alt text](/images/Activity15/upload-files.png)

## Step 4: checking logs in destination bucket

1. Go to **destination** bucket
2. you are able to see the logs file in the destiation bucket
3. Note that this will take some time to get the logs for the first time.

   ![alt text](/images/Activity15/logs.png)

### Load balancer Implementation

## Step 1: Create 2 EC2 instances

1. Go to EC2 Dashboard
2. Click on Launch instance
3. select Ubuntu as AMI
4. Select Key Pair and security Group
5. Click on launch instance
6. Add the following User Data in **Additional Details** sections
   ```bash
   #!/bin/bash
   apt update -y
   apt install -y apache2
   systemctl start apache2
   systemctl enable apache2
   echo "<div><h1>Hello World from server 1</h1> <p><strong>Hostname: </strong> $(hostname -f)</p></div>" > /var/www/html/index.html
   ```
7. Create a second instance similar specifications (change the servern number in the above code)
8. Copy the Publick Ip of both the instances and search in browser, you will able to see the web page

   **Sample Image for server 1:**

   ![alt text](/images/Activity15/server1.png)

   **Sample Image for server 2:**

   ![alt text](/images/Activity15/server2.png)

## Step 2: Create Target Group

1. Go to **Target Groups** Dashbord
2. click on **create Target Gorup** button
3. Give Target Group name > click on **Next** button
4. Select required instances which are for load balancing and **click on inclue as pending below** button
5. click on create **Target Group** button

   ![alt text](/images/Activity15/inlucde-inst.png)

   ![alt text](/images/Activity15/target-group.png)

## Step 3: Creating load balancer

1. Go to load balancer Dahboard
2. Click on create **Load Balancer** button
3. Select Application Load balancer
4. Give load balancer name
5. Select all subnets
6. Select security group
7. select newly created target group
8. click on create **load balancer** button

   ![alt text](/images/Activity15/load-balancer.png)

## Step 4: Validating the Load balancer functionality

1. Go to load balancer dashboard
2. Open the load balancer
3. copy the DNS Name and search in the browser

   ![alt text](/images/Activity15/dns.png)

4. In Browser, you can refresh the page multiple times, and you can notice that the server and host name info is changing based on load for every request

   ![alt text](/images/Activity15/validation.png)
