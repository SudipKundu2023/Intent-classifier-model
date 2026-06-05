go to Help website :

curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-4

or 
curl -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-4

chmod 700 get_helm.sh

./get_helm.sh


## In  windows local
open powershell as Administrator:
>> choco install kubernetes-helm

# Traefik Ingress Controller Installation

---

## 1. Add Traefik Helm Repository

    helm repo add traefik https://helm.traefik.io/traefik
    helm repo update

---

## 2. Install Traefik Ingress Controller

    helm install traefik traefik/traefik \
      --namespace traefik \
      --create-namespace

---

## 3. Verify Installation

    kubectl get pods -n traefik

You should see the Traefik controller running.

---

## 4. Retrieve the Load Balancer Endpoint

    kubectl get svc -n traefik

Look for the `traefik` service of type **LoadBalancer**, and use the external DNS name to access applications via Ingress.

---

# End of installation steps

# add ingress resource

# get the traefik pod name
kubectl get pods -n traefik

# get the log floating
kubectl logs traefik-6f4ff44789-tdlr9 -n traefik -f

# appliy the ingress.yaml
kubectl apply -f 06-ingress.yaml

# check for external address and map to DNS
kubectl get ingress -n intent-namespace
# for testing purpose map locally
curl -X POST --resolve example.com:80:<ARN Address> http://example.com/predict -H "Content-Type: application/json" -d {"a":"hello"}

trouble shoot:
to check for IP address:
nslookup <ARN Address>
OR
dig +short <ARN Address>
OR
getent ahosts <ARN Address>








