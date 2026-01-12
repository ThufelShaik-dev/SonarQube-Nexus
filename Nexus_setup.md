## Step-1 : Setup Linux VM (Amazon Linux AMI)

Login into AWS Cloud account -> Launch Linux VM using EC2 service ->
AMI : Amazon Linux -> Instance Type : t2.medium ->
Connect to VM using GitBash

## Step-2 : Install Docker In Linux VM

```
sudo yum update -y
sudo yum install docker -y
sudo service docker start
sudo usermod -aG docker ec2-user
exit
```

## Step-3 : Verify docker installation

```
docker -v
```

## Step-4 : Run Nexus using official docker image

```
docker run -d -p 8081:8081 --name nexus sonatype/nexus3
```

## Step-5: Enable 8081 port number in Security Group Inbound Rules & Access Nexus Server

http://EC2-public-ip:8081/

## Step-6: Get Nexus password from the Docker container since Nexus is running in a container, log in to the container using the commands below

-> List running Docker containers
Identify the Nexus container ID or name:

```
docker ps
```

-> Log in to the Nexus container
Replace <container-id> with the actual container ID or name:

```
docker exec -it <container-id> /bin/bash
```

-> Read the admin password file
Nexus stores the initial admin password in the following location:

```
cat /nexus-data/admin.password
```

-> Copy the password
Use this password to log in to the Nexus UI as the admin username.

## Step-7: Login into Nexus Server & Reset pwd
