# k8s-Ingress-with-ssl-tls
#1: Install Helm 3 on Kubernetes Cluster
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3
chmod 700 get_helm.sh
./get_helm.sh
helm version
#2: Create Namespace 
 kubectl apply -f namespace.yaml 
#3: Deploy ngix application 
  kubectl apply -f nginx-deploy.yaml 
#4: Deploy nginx xluster service 
kubectl apply -f nginx-svc.yaml 

#5: Install Nginx Ingress Controller Kubernetes using Helm
helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx
helm install ingress-nginx ingress-nginx/ingress-nginx

#6:Pointing Nginx Ingress Loadbalancer in Domain Name provider to Access app using Domain Name

#7: Configure cert manager for Nginx Ingress 
 helm Installation Documentation:- 
 https://cert-manager.io/docs/installation/helm/
 
 kubectl apply -f https://github.com/cert-manager/cert-manager/releases/download/v1.9.1/cert-manager.yaml

#8: Configure cluster Issure 
 kubectl apply -f cert-issuer.yaml

#9: Update ingress controller 
 kubectl apply -f ingress.yaml 

#10: Deploy certificate 
 kubectl apply -f certificate.yaml s

# Configure one more nginx ingress in same k8s


helm install botshot-web-nginx-ingress ingress-nginx/ingress-nginx --namespace botshot-web-nginx-ingress --set controller.ingressClass="botshot-web-nginx-ingress" --set controller.ingressClassResource.name="botshot-web-nginx-ingress" 
