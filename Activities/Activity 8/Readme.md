# Activity 8

## Create a custom docker image for nginx and deploy it using docker compose, where the volume bind mount should be at /var/opt/nginx location. Push the created custom docker image to your docker-hub.

### Step 1: Start EC2 instance server

1. Go to EC2 console and click on **Launch instance** button
2. Give Instance name like **My Server**
3. Select **Ubuntu** as AMI (Amazon Machine Image)
4. Select Instance type as **t2.micro**
5. Generate a Key pair and select it
6. Create an security group and click on **launch instance** button

### Step 2: Install the docker

1. Connect the EC2 instance and connect to mobaxTerm
2. Install the docker by the following commands

   ```bash
   # Add Docker's official GPG key:
   sudo apt-get update
   sudo apt-get install ca-certificates curl
   sudo install -m 0755 -d /etc/apt/keyrings
   sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
   sudo chmod a+r /etc/apt/keyrings/docker.asc

   # Add the repository to Apt sources:
   echo \
   "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
   $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
   sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
   sudo apt-get update

   # To install the latest version, run:
   sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
   ```

3. Check the Docker version using below command

   ```bash
   docker --version
   ```

   **Sample Screenshot**

   ![alt text](/images/Activity7/docker%20version.png)

### Step 3: Creating index.html file

**Sample Code** (also attached the html file):

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Custom Docker Page</title>
  </head>
  <body
    style="
      text-align: center;
      background-color: cyan;
      font-weight: 900;
      font-size: 20px;
      font-family: Helvetica, Arial, sans-serif;
    "
  >
    <img
      src="https://www.docker.com/wp-content/uploads/2022/03/Moby-logo.png"
    />
    <h2>This container was deployed:</h2>
    <div id="date"></div>
    <script>
      var date = new Date();
      document.getElementById("date").innerHTML = date.toLocaleString();
    </script>
  </body>
</html>
```

### Step 4: Creating Dockerfile

1. **Sample Code** (also attached the html file):

   ```docker
   FROM nginx
   RUN apt update
   COPY index.html /usr/share/nginx/html
   EXPOSE 8085
   CMD ["nginx","-g","daemon off;"]
   ```

2. Add **ubuntu** user to **docker** group

   ```bash
   sudo usermod -aG docker ubuntu
   ```

   **Sample Screeenshot**

   ![alt text](/images/Activity7/add_user_to_docker_grp.png)

3. Verify the user is added to docker group or not using the below command

   ```bash
   id
   ```

   **Sample Screenshot**

   ![alt text](/images/Activity7/user_docker_grp.png)

4. Build the docker file

   ```bash
   docker build -t custom_docker_image:1.0 .
   ```

   **Sample Screenshot**

   ![alt text](/images/Activity8/build.png)

5. Check the list of images

   ```bash
   docker images
   ```

   **Sample Screenshot**

   Observe the image **custom_docker_page** got newly created

   ![alt text](/images/Activity8/docker_images.png)

### Step 4: Creating docker compose file

1. Create a new file named with **docker-compose.yaml**

2. Add the following data in to that file

   ```yaml
   services:
   my_details:
     image: custom_docker_page:1.0
     container_name: custom_docker_page_compose
     ports:
       - 8086:80
     volumes:
       - ./imp_data:/var/opt/nginx
   ```

3. Run the docker compose file using the below command

   ```bash
   docker compose up -d
   ```

   **Sample Screenshot**

   ![alt text](/images/Activity8/docker_compose_file_run.png)

4. Copy the Public IP Address and open 8086 port in browser

   **Sample Screenshot**

   ![alt text](/images/Activity8/docker_custom_image.png)
