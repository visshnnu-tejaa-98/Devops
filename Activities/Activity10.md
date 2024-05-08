# Activity 10

### Launch jenkins and explore creating projects and users

## Step 1: Install Jenkins in to EC2 Instance Server

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

## Step 2: Launch Jenkins

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

## Step 3: Creating a project

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

## Step 4: Creating users

1. Go to Dashboard > manage jenkins > Click on plugins > click on Available plugins

2. Search for **Role-based Authorization strategy** and install it

   ![alt text](/images/Activity10/plugin.png)

3. Go to Dashboard > manage jenkins > security > select **Role-based strategy** for Authorisation field in security section

   ![alt text](/images/Activity10/role-based-strategy.png)

4. Go to Dashboard > manage jenkins > click on **manage and assign roles**. Enter role name and click on add > select the required permessions for that role and click on **save**

   ![alt text](/images/Activity10/role.png)

5. Go to Dashboard > manage jenkins > click on **users** > click on **create** button > Fill the username, password, email and click on **create user** button

   ![alt text](/images/Activity10/user.png)

6. Go to Dashboard > manage jenkins > click on **manage and assign roles**. click on **Assign roles** > add the user and check the checkbox which permessions you wanted to > click on **save and apply**

   ![alt text](/images/Activity10/assign-user.png)

7. Now, if you open the jenkins in different browser > you will be seeing the login form > enter your **dev** user credentials and login to jenkins (http://100.25.119.120:8080/)

   - Here only read only permession is given to **dev** user, so we can not able to see the create option in the left side navbar

     ![alt text](/images/Activity10/read-only.png)

8. We can delete the user by navigating to Dashboard > manage jenkins > click on users > click on delete icon to delete the user

   ![alt text](/images/Activity10/delete-user.png)
