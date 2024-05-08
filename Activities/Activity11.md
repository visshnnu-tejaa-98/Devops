# Activity 11

### Create a simple project with Jenkins connected to your GitHub repository. When a commit is made to your repo, automatically build must get triggered from Jenkins and the output must be shared via email."

## Step 1: Add a webhook for your git repository

1. Open your repository > settings > webhook > add webhook

   - Give payload UR as below format
     ```bash
     http://<your_public_ip>:8080/github-webhook/
     ```

   ![alt text](/images/Activity11/webhook.png)

## Step 2: Create a new app password for your google account

1. Go to google account > click on manage account > enable 2-setp verifcation

2. search app password in search bar > enter your email id > create your app password > copy the password

## Step 3: Install Jenkins in to EC2 Instance Server

1. Create an EC2 instance with min of 2GB Storage
2. Install the following commands to install jenkins

   ```bash
   # This is the Debian package repository of Jenkins to automate installation and upgrade
   sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
   https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key

   # Then add a Jenkins apt repository entry

    echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
    https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
    /etc/apt/sources.list.d/jenkins.list > /dev/null

    # Update your local package index, then finally install Jenkins:

    sudo apt-get update
    sudo apt-get install fontconfig openjdk-17-jre
    sudo apt-get install jenkins
   ```

3. To check the jenkins is installed or not

   ```bash
   jenkins --version
   ```

   ![alt text](/images/Activity10/jenkins-version.png)

## Step 4: Launch Jenkins

1. Copy tour public_ip and open 8080 in browser

   ```bash
   http://100.25.119.120:8080/
   ```

2. You will be seeing the below screen to unlock jenkins when we launch for the first time
   ![alt text](/images/Activity10/unlock%20jenkins.png)

3. Cat that file which is given in the above screenshot in the terminal, you will be seeing the password, enter theat passwork and ckick on **continue** button

   ![alt text](/images/Activity10/copy-password.png)

4. As a next step, you will be seeing the below image, please select **Install suggested plugins**

   ![alt text](/images/Activity10/install-pluggins.png)

5. Post that all the suggested pluggins will be installed and after completing the installation, click on **next** button

6. As a next step, the below screen will be displayed where you can create your account by providing username, password, email

   ![alt text](/images/Activity10/create-user.png)

7. Next, it will ask for confirmation for jenkins path, click on **save and finish** button

   ![alt text](/images/Activity10/instance-config.png)

8. Click on **Start using jenkins** button in next screen, Here you will be navigated to dash board of jenkins

## Step 5: Creating a project

1. Click on **new item** in left side panel

   ![alt text](/images/Activity10/new.png)

2. Give the project name and select **freestyle project** and click on **ok** button

   ![alt text](/images/Activity10/project%20name.png)

3. Perform the below process

   - In General section --> Give the description of the project
   - In Source management section --> select Git
     - Give Our github repository URL
     - Add black for the nranch specifier field
   - Click on **apply** and **save** buttons

     ![alt text](/images/Activity10/description.png)

     ![alt text](/images/Activity10/add-src.png)

     ![alt text](/images/Activity10/branch.png)

4. This will navigate to the dashboard of jenkins

   ![alt text](/images/Activity10/dashboard.png)

5. There ia a play buttion right side to each project, if you click it will trigger the build. Post build the below one is the screenshot
   ![alt text](/images/Activity10/build.png)

## Step 6: Configuring Email

1. Go to Dashboard > manage jenkins > system > Scrool bottom > go to Email Notification section

   - SMTP Server --> smtp.gmail.com
   - Select use SMTP Authentication
   - user name --> your email
   - password --> your app password
   - Select use SSL
   - SMTP Port --> 465
   - select test configuration by sending e-mail
   - Test e-mail recipient --> your email
   - Click on test configuration (you will get an email)
   - Click on **save** and **apply**

   ![alt text](/images/Activity11/email-config1.png)

   ![alt text](/images/Activity11/email-config2.png)

   ![alt text](/images/Activity11/test-email.png)

2. Go to dashboard > open project > click on configure

   - Navigate to **Build triggers** section
   - Select **GitHub hook trigger for GITScm polling**
   - Navigate to **Post-build Actions** section > click on **add post-build action** button > select Email Notification
   - Recipients --> Enter your email
   - Again click on **add post-build action** button > select **Editable Email Notification**
   - Scroll to bottom of **Editable Email Notification** section > click on **advanced settings** button
   - Again Scroll to bottom of **Editable Email Notification** section > click on **Add Trigger** button > select **Always**
   - Click on **save** and **apply** buttons

     ![alt text](/images/Activity11/email-config-3.png)

     ![alt text](/images/Activity11/email-config-4.png)

     ![alt text](/images/Activity11/email-config-5.png)

## Step 7: To make build Failure

1. Go to Dashboard > Build Steps > Add build step > select execute shell

2. Add the following data in the command input and click on save and apply

   ```bash
   exit 1
   ls -lrt
   pwd
   ```

3. Go to your github repo > open readme file > modify content > commit changes

   ![alt text](/images/Activity11/commit.png)

4. Notice here, the build was failed

   ![alt text](/images/Activity11/build-fail.png)

5. Also observe the email which is automatically sent by jenkins about the failure

   ![alt text](/images/Activity11/email-failed.png)

## Step 8: To amke build sucess

1. Go to Dashboard > Build Steps > remove the **exit** command in the shell commands > save and apply

2. Go to the github and make a commit again

   ![alt text](/images/Activity11/commit.png)

3. Notice here, the build was Succeded

   ![alt text](/images/Activity11/build-sucess.png)

4. Observe the email which is triggered after build sucess

   ![alt text](/images/Activity11/email-sucess.png)
