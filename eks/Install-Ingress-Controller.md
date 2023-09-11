# Create the namespace for ingress-nginx
kubectl create namespace ingress-nginx

# Add nginx repository to helm
helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx
helm repo update


# Install nginx ingress controller

helm install ingress-nginx ingress-nginx/ingress-nginx --version="4.0.17" \
    --set rbac.create=true \
    --set controller.kind=DaemonSet \
    --set controller.service.type=LoadBalancer \
    --set controller.service.externalTrafficPolicy=Local \
    --set controller.publishService.enabled=true \
    --set defaultBackend.enabled=true \
    --set defaultBackend.image.repository="k8s.gcr.io/defaultbackend-arm64" \
    --set enable-prometheus-metrics=true \
    --namespace ingress-nginx    