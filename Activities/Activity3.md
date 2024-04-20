# Activity 1

### Get me IP address of particular domain (guvi.in)?

```bash
nslookup guvi.in
```

Sample Screenshot:

![alt text](/images/Activity3/nslookup.png)

### How do I find my CPU/memory usage of my server?

```bash
top
```

Sample Screenshot:

![alt text](/images/Activity3/top.png)

### Test the connectivity between 2 nodes?

**Created a 2 ec2 instances in aws:**

```txt
Server1 private ip address: 172.31.18.186
Server2 private ip address: 172.31.90.83

Server1 public ip address:
Server2 public ip address: 54.198.219.222
```

Sample screenshot for server 1:
![alt text](/images/Activity3/server1_initial_ip_address.png)

Sample screenshot for server 2:
![alt text](/images/Activity3/server2_initial_ip_address.png)

**From Server 1:**

```bash
# To generate a pubic key
ssh-keygen

# To list the public keys
# Navigate to .ssh directory and isting them
cd .ssh
ls -l
```

Sample Screenshot:

![alt text](/images/Activity3/listing_public_key.png)

```bash
# Coping the id_rsa.pub file content (public key)
cat id_rsa.pub
```

Sample Screenshot:

![alt text](/images/Activity3/public_key.png)

**From Server 2:**

```bash
# Naviagte to .ssh directory and open authorized_keys file
cd .ssh
ls -l
cat authorized_keys
# Paste the public key in this file
```

Sample Screenshot:
![alt text](/images/Activity3/authorized_keys.png)

**From Server 1:**

```bash
# SSH to public ip address from server 2
ssh 54.198.219.222
```

Sample Screenshot from server1 (connected to server 2):

![alt text](/images/Activity3/connected_server.png)

### I have deployed an application in guvi.com:9000, and logs shows my app is running, but I’m unable to view the page. Check whether my port is open or not ?

```bash
# To check the port 9000 is opened or not
# Using lsof
lsof -i:9000

# Using netstat
netstat -tuln | grep 9000
```
