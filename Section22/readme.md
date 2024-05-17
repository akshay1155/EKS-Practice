# EKS & ECS
- docker build -t aws-ecr-kubenginx .
- docker tag aws-ecr-kubenginx:latest 590183828947.dkr.ecr.us-east-1.amazonaws.com/aws-ecr-kubenginx:latest
- aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 590183828947.dkr.ecr.us-east-1.amazonaws.com
- docker push 590183828947.dkr.ecr.us-east-1.amazonaws.com/aws-ecr-kubenginx:latest