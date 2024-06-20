Install npm packages for frontend
Install packages for each service in backend

Commands to start
Frontend - serve -s build
Backend - node index.js

Docker commands
docker build -t samplemern-frontend:v1 .
docker build -t profile-service:v1 .
docker build -t hello-service:v1 .

Configure and push each docker image to ECR
aws ecr get-login-password --region eu-west-2 | docker login --username AWS --password-stdin 515210271098.dkr.ecr.eu-west-2.amazonaws.com

docker tag samplemern-frontend:v1 515210271098.dkr.ecr.eu-west-2.amazonaws.com/sample-mernap
p-frontend:latest
docker push 515210271098.dkr.ecr.eu-west-2.amazonaws.com/sample-mernapp-frontend:latest

docker tag hello-service:v1 515210271098.dkr.ecr.eu-west-2.amazonaws.com/sample-mern-hello-svc:latest
docker push 515210271098.dkr.ecr.eu-west-2.amazonaws.com/sample-mern-hello-svc:latest

docker tag profile-service:v1 515210271098.dkr.ecr.eu-west-2.amazonaws.com/sample-mernapp-profile-svc:latest
docker push 515210271098.dkr.ecr.eu-west-2.amazonaws.com/sample-mernapp-profile-svc:latest

AWS CodeCommit
Attach AWSCodeCommitPowerUser Policy to IAM User
Generate credentials to push git code to AWSCodeCommit and download those credentials
Install Git into local computer if not installed Git
Clone the aws codecommit repository

git clone https://git-codecommit.eu-west-2.amazonaws.com/v1/repos/sample-mern-app

https://docs.aws.amazon.com/codecommit/latest/userguide/getting-started-cc.html

Git commands to push the code to AWSCodeCommit repo
git add .
git commit -m msg
git push 

Install Jenkins on Amazon EC2
ssh -i "C:/Users/ishwa/Downloads/ishwari-2.pem" ubuntu@ec2-18-130-232-25.eu-west-2.compute.amazonaws.com

Install Jenkins on EC2 Ubuntu machine
sudo apt update
sudo apt install fontconfig openjdk-17-jre
java -version
sudo wget -O /usr/share/keyrings/jenkins-keyring.asc   https://pkg.jenkins.io/debian/jenkins.io-2023.key

echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc]"   https://pkg.jenkins.io/debian binary/ | sudo tee   /etc/apt/sources.list.d/jenkins.list > /dev/null

sudo apt-get update
sudo apt-get install jenkins

Create public key and private key pair through ssh-key for authenticating jenkins in AWSCodeCommit.
ssh-keygen

Upload generated public key for User SSH public keys for AWS CodeCommit









