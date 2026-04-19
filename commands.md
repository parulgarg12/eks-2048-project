# Commands Used

## Create EKS Cluster
eksctl create cluster --name demo-cluster --region ap-south-1 --fargate

## Associate OIDC Provider
eksctl utils associate-iam-oidc-provider --cluster demo-cluster --region ap-south-1 --approve

## Create IAM Service Account
eksctl create iamserviceaccount --cluster=demo-cluster --namespace=kube-system --name=aws-load-balancer-controller --role-name AmazonEKSLoadBalancerControllerRole --attach-policy-arn=arn:aws:iam::510593089399:policy/AWSLoadBalancerControllerIAMPolicy --approve --region=ap-south-1

## Install AWS Load Balancer Controller
helm repo add eks https://aws.github.io/eks-charts
helm repo update eks
helm install aws-load-balancer-controller eks/aws-load-balancer-controller -n kube-system --set clusterName=demo-cluster --set serviceAccount.create=false --set serviceAccount.name=aws-load-balancer-controller --set region=ap-south-1 --set vpcId=vpc-0e02305769ae60b01

## Deploy 2048 App
kubectl apply -f https://raw.githubusercontent.com/kubernetes-sigs/aws-load-balancer-controller/v2.5.4/docs/examples/2048/2048_full.yaml
