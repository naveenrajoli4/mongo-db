# MongoDB

We use bastion host as Docker server and EKS client.
Make sure `aws configure` is done in bastion and connected to EKS cluster.
```
aws eks update-kubeconfig --region us-east-1 --name kdp-roboshop-prod-eks
```
```
kubectl create namespace roboshop
```
* Login to ECR
```
aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 135808959960.dkr.ecr.us-east-1.amazonaws.com
```
* Build MongoDB image.
```
docker build -t 135808959960.dkr.ecr.us-east-1.amazonaws.com/kdp-roboshop-prod/mongodb:v1.0.1 .
```
* Push image
```
docker push 135808959960.dkr.ecr.us-east-1.amazonaws.com/kdp-roboshop-prod/mongodb:v1.0.1
```
* Now install using Helm. move to helm directory
```
helm upgrade --install mongodb . -n rnk-roboshop
```
