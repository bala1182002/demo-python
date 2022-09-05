# Cloud9->ECR-> Fargate

## Steps

Create a cloud9 environment. 
Attach 'Instance Profile'  with Admin access to the Cloud9 EC2 instance.

Clone this git repository in Cloud9 IDE.

```bash
git clone https://github.com/bala1182002/demo-python.git
```

Create a docker image

```bash
cd ~/environment/demo-python/
docker build -t app .
docker images
```
Run the image locally

```bash
docker run -d -p 5000:5000 app
curl localhost:5000
```

Create ECR resource in AWS and push your image.

```bash
aws ecr get-login-password --region <region> | docker login --username AWS --password-stdin <ecr endpoint>

docker tag app:latest <ecr endpoint>/<repo Name>:latest

docker push <ecr endpoint>/<repo Name>:latest
```
