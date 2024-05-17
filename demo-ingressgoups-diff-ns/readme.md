# EKS Ingress that will load balance between 3 different apps in different namespace

- Create EKS Node Group in Private Subnets
- Create an AWS IAM Policy for aws-load-balancer-controller
- Create an iamserviceaccount using this IAM Policy ARN in the namespace kube-system using eksctl command
- Install aws-load-balancer-controller in the namespace kube-system using Helm chart from the repo eks/aws-load-balancer-controller
- Create an ingressclass resource that specifies the controller as ingress.k8s.aws/alb
- Create 3 deployments which are deployed in 3 different namespaces
- Create an ALB Ingress resource such that the single loadbalancer can loadbalance between the 3 deployments based on path
- Implement SSL Redirect
