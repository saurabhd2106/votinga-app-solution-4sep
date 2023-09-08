eksctl create cluster --name eks-cluster --region ap-south-1 --version 1.26 --without-nodegroup

kubectl get nodes -o wide

kubectl get pods -o wide

aws eks update-kubeconfig --region ap-south-1 --name eks-cluster

kubectl config get-clusters

kubectl config get-contexts

eksctl delete cluster --name eks-cluster --region ap-south-1