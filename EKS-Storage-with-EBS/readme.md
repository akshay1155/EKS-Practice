- kubectl -n kube-system describe configmap aws-auth

- kubectl version --client --short

- kubectl apply -k "github.com/kubernetes-sigs/aws-ebs-csi-driver/deploy/kubernetes/overlays/stable/?ref=master"

- kubectl get pods -n kube-system

- kubectl apply -f kube_manifests/
- kubectl get sc
- kubectl get pvc
- kubectl get pv


- #https://docs.aws.amazon.com/eks/latest/userguide/csi-iam-role.html
- #https://docs.aws.amazon.com/eks/latest/userguide/managing-ebs-csi.html#adding-ebs-csi-eks-add-on
- aws eks describe-cluster --name eksdemo1 --query "cluster.identity.oidc.issuer" --output text
- aws iam create-role --role-name AmazonEKS_EBS_CSI_DriverRole --assume-role-policy-document file://"aws-ebs-csi-driver-trust-policy.json"
- aws iam attach-role-policy --policy-arn arn:aws:iam::aws:policy/service-role/AmazonEBSCSIDriverPolicy --role-name AmazonEKS_EBS_CSI_DriverRole
- aws eks create-addon --cluster-name eksdemo1 --addon-name aws-ebs-csi-driver --service-account-role-arn arn:aws:iam::590183828947:role/AmazonEKS_EBS_CSI_DriverRole