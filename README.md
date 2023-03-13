### Step to install traefik reverse proxy on kubernetes
1. Install Traefik Resource Definitions  
`kubectl apply -f https://raw.githubusercontent.com/traefik/traefik/v2.9/docs/content/reference/dynamic-configuration/kubernetes-crd-definition-v1.yml`

2. Install RBAC for Traefik  
`kubectl apply -f https://raw.githubusercontent.com/traefik/traefik/v2.9/docs/content/reference/dynamic-configuration/kubernetes-crd-rbac.yml`

3. Install traefik helmchart  
```
helm repo add traefik https://traefik.github.io/charts
helm repo update
helm install traefik traefik/traefik

# Verify service is running
kubectl get svc -l app.kubernetes.io/name=traefik
kubectl get po -l app.kubernetes.io/name=traefik
```

4. Enable traefik dashbaord by  
 `kubectl apply -f traefik-dashboard.yaml`

5. Deploy your service suck as Nginx  
 `kubectl apply -f nginx-deployment.yaml`

6. Deploy traefik ingress route  
`kubectl apply -f ingress-deployment.yaml`
  
*- Helm install `curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash`*  
*- See example in code*