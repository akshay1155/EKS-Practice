# Create Cluster
 - eksctl create cluster --name=eksdemo1 --region=us-east-1 --zones=us-east-1a,us-east-1b --without-nodegroup 
 - eksctl get cluster                  

 - eksctl utils associate-iam-oidc-provider --region us-east-1 --cluster eksdemo1 --approve

  
 - eksctl create nodegroup --cluster=eksdemo1 --region=us-east-1 --name=eksdemo1-ng-public1 --node-type=t3.medium --nodes=2 --nodes-min=2 --nodes-max=4 --node-volume-size=20 --ssh-access --ssh-public-key=kube-demo --managed --asg-access --external-dns-access --full-ecr-access --appmesh-access --alb-ingress-access 

 - eksctl get cluster


 - eksctl delete cluster eksdemo1


- #https://docs.aws.amazon.com/eks/latest/userguide/csi-iam-role.html
- #https://docs.aws.amazon.com/eks/latest/userguide/managing-ebs-csi.html#adding-ebs-csi-eks-add-on
- aws eks describe-cluster --name eksdemo1 --query "cluster.identity.oidc.issuer" --output text
- aws iam create-role --role-name AmazonEKS_EBS_CSI_DriverRole --assume-role-policy-document file://"aws-ebs-csi-driver-trust-policy.json"
- aws iam attach-role-policy --policy-arn arn:aws:iam::aws:policy/service-role/AmazonEBSCSIDriverPolicy --role-name AmazonEKS_EBS_CSI_DriverRole
- aws eks create-addon --cluster-name eksdemo1 --addon-name aws-ebs-csi-driver --service-account-role-arn arn:aws:iam::590183828947:role/AmazonEKS_EBS_CSI_DriverRole


aws iam detach-role-policy --policy-arn arn:aws:iam::aws:policy/service-role/AmazonEBSCSIDriverPolicy --role-name AmazonEKS_EBS_CSI_DriverRole
aws iam delete-role --role-name AmazonEKS_EBS_CSI_DriverRole


