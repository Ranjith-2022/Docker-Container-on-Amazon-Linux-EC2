# Docker Container on Amazon Linux EC2

## Step 1: Docker Installation on Cloud9

### Docker Installation

```bash
sudo yum update -y
sudo yum install docker -y
sudo systemctl start docker
sudo systemctl status docker
```

## Step 2: Configuring Access

```bash
sudo chmod 666 /var/run/docker.sock
sudo usermod -a -G docker ec2-user
```

## Step 3: Configure AWS Keys

```bash
aws configure
sudo vi ~/.aws/credentials
```
## Step 4: Add GIT Secrets in Your GitHub

<img width="596" alt="GitHub Secrets" src="https://github.com/Ranjith-2022/clo835-assignment1/assets/114111480/0e029200-4c03-4f91-8660-deac6b6c2c94">

## Step 5: Terraform Configuration

Move to the Terraform folder and generate an assignment1 key pair file using the following command:

```bash
ssh-keygen -t rsa -f assignment1
terraform init
terraform plan
terraform apply -auto-approve
```

## Step 6: Pull Image from Amazon ECR

Once the image is successfully pushed from GitHub to Amazon ECR clo835-ecr-assignment1, Docker login using the following commands:

```bash
docker pull db_uri
docker pull App_uri
```

## Step 7: Docker Create and Run

```bash

docker network create -d bridge ranjith-network
docker run -d --network ranjith-network -e MYSQL_ROOT_PASSWORD=pw uri
docker inspect <container_id>

```
## Step 8: Exporting Keys

```bash
export DBHOST=172.18.0.2
export DBPORT=3306
export DBUSER=root
export DATABASE=employees
export DBPWD=pw

```
## Step 9: Run Application in Website

```bash

export APP_COLOR=blue
docker run -p 8081:8080 --name blue --network=ranjith-network -e APP_COLOR=$APP_COLOR -e DBHOST=$DBHOST -e DBPORT=$DBPORT -e DBUSER=$DBUSER -e DBPWD=$DBPWD [uri]

export APP_COLOR=pink
docker run -p 8082:8080 --name pink --network=ranjith-network -e APP_COLOR=$APP_COLOR -e DBHOST=$DBHOST -e DBPORT=$DBPORT -e DBUSER=$DBUSER -e DBPWD=$DBPWD uri

export APP_COLOR=lime
docker run -p 8083:8080 --name lime --network=ranjith-network -e APP_COLOR=$APP_COLOR -e DBHOST=$DBHOST -e DBPORT=$DBPORT -e DBUSER=$DBUSER -e DBPWD=$DBPWD uri

```
## Step 10: Accessing Database in Docker

```bash

docker exec -it <container_name> /bin/bash
mysql -u root -p employees

```


















