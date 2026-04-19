# Kubernetes EKS 2048 Game Deployment

Deployed the 2048 game on AWS EKS Fargate using kubectl, eksctl, Helm and AWS Load Balancer Controller.

## Tools & Technologies
- AWS EKS Fargate
- kubectl, eksctl, AWS CLI
- Helm
- AWS Load Balancer Controller (ALB Ingress)

## Steps Followed
1. Created EKS Fargate cluster using eksctl
2. Associated IAM OIDC provider
3. Created IAM policy and service account
4. Installed AWS Load Balancer Controller via Helm
5. Deployed 2048 app using kubectl
6. Accessed the app via ALB DNS URL
