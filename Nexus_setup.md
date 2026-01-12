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

## Step-6: Get nexus passsword from Docker since our nexus running in container

```
docker ps
docker exec -it <container-id> /bin/bash
cat /nexus-data/admin.password
```

## Step-7: Login into Nexus Server & Reset pwd
