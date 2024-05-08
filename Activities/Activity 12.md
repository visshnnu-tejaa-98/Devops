# Activity 12

### Create a windows Vm machine in AWS and connect with RDP open CMD in windows share the about system info

## Step 1: Creating an EC2 Instance

1. Login to AWS console
2. Go to EC2 Dashboard
3. Click on launch instance
4. Give Name of the instance in Name and tags section
5. Select Windows AMI
6. Select t2.micro as an instance type
7. Generate a new key pair
8. create a new security group
9. Click on launch instance

**Sample Screenshots**

![alt text](/images/Activity12/console-1.png)

![alt text](/images/Activity12/console-2.png)

![alt text](/images/Activity12/console-3.png)

![alt text](/images/Activity12/console-4.png)

## Step 2: connect to RDP

1. Once the server is initialized, select the server > click on connect > click on RDP Client > click on **download remote desktop file**

2. Click on **get password**

   ![alt text](/images/Activity12/connect-1.png)

3. upload our dowloaded **.pem** file > click on **Decrypt Password**

   ![alt text](/images/Activity12/connect-2.png)

4. Copy the decrypted password

   ![alt text](/images/Activity12/connect-3.png)

5. Go to your downloads folder and open windows server

   - click on connect

     ![alt text](/images/Activity12/vdi-1.png)

   - Enter copied password

     ![alt text](/images/Activity12/vdi-2.png)

   - Click on Yes

     ![alt text](/images/Activity12/vdi-3.png)

   - Now, A remote desktop will open

     ![alt text](/images/Activity12/vdi-4.png)

   - Here are the system info of Virtual Desktop

     ![alt text](/images/Activity12/system-info-1.png)

   - Getting system info from command prompt

     ![alt text](/images/Activity12/system-info-2.png)
