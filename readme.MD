# MongoDB

We use bastion host as Docker server and EKS client.
* Login to ECR
```
aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 315069654700.dkr.ecr.us-east-1.amazonaws.com
```
* Build MongoDB image.
```
docker build -t 315069654700.dkr.ecr.us-east-1.amazonaws.com/roboshop/dev/mongodb:v1.0.0 .
```
* Push image
```
docker push 315069654700.dkr.ecr.us-east-1.amazonaws.com/roboshop/dev/mongodb:v1.0.0
```
* Now install using Helm.
```
helm upgrade --install mongodb .
```