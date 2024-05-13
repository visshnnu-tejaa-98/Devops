# Activity 13

### Launch an EC2 instance (Linux and Windows) along with a web server. Then, create an EBS volume of 5 GB, attach it to an EC2 machine (Linux and Windows), and take a snapshot. Finally, create an EBS volume using the taken snapshot.

## Step 1: Launch an EC2 instance

- Login to AWS Application > search for EC2 in search bar > click on launch instance

- Give instance name > select Amazon linux as AMI > select key pair > selec security group > Give the below user data for user details (for web server) > click on launch instance

  ```bash
  #!/bin/bash
  yum update -y
  yum install -y httpd
  systemctl start httpd
  systemctl enable httpd
  echo "<h1>Hello World from $(hostname -f)</h1>" > /var/www/html/index.html
  ```

- copy the public ip of the instance and search in browser, you will be able to see the web page as below

  ![alt text](/images/Activity13/web-server.png)

## Step 2: Creating an EBS volume of 5 GB

- Select Volumes in sidebar > create volume > Give 5GB in size input field > select Availablility zone to **us-east-1b** click on create volume

  ![alt text](/images/Activity13/size.png)

  ![alt text](/images/Activity13/az.png)

* Now, go to volumes dashboard > you can notice that new volume is created.

  ![alt text](/images/Activity13/volumes.png)

## Step 3: Attach EBS to EC2 instance

- select the newly created **EBS** > click on Actions > Attach volume
  ![alt text](/images/Activity13/actions.png)

* select instance which you want to attach and select device name > click on **Attach volume**

  ![alt text](/images/Activity13/attach%20volume.png)

* To verify it > go to instances > select respective instance > go to storage tab
* Here you can see 2 EBS Volumes (in which one volume is created at the time of EC2 instance other is newly attached one)

  ![alt text](/images/Activity13/verify-ebs.png)

## Step 4: Creating a snapshot of volume

- Go to volumes dashboard > select the newly created volume > click on Actions > select **create snapshot**

  ![alt text](/images/Activity13/snapshot-options.png)

* Give the description name and ckick on **create snapshot** button

  ![alt text](/images/Activity13/create-snapshot.png)

* Now sapshot is created and you can see in snapshot dashboard

  ![alt text](/images/Activity13/snapshot-dashboard.png)

### Step 5: Create a volume from this snapshot

- basically we will create a snapshot to connect this EBS to another EC2 instance in different region

- In order to implement this, we can create an another EC2 instance in mumbai region

- Go to snapshots dashboard in verginia region > select the respective snapshot > click on actions > click on copy snapshot

  ![alt text](/images/Activity13/copy-snapshot-option.png)

- Select destination region and click on copy snapshot

  ![alt text](/images/Activity13/copy-snapshot.png)

- Now, go to mumbai region > go to snapshot dashboard, you will able to see the newly copied snapshot

  ![alt text](/images/Activity13/snapshot-mumbai.png)

- As a next step > go to snapshot dashboard > select the snapshot > actions > create volume

  ![alt text](/images/Activity13/volume-mumbai.png)
