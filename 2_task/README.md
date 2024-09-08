# To create kind cluster
kind create cluster --config kind-config.yaml --name ppro

#To create namespace manually
kubectl create namespace qa
kubectl create namespace prod

# To add helm repository
helm repo add bitnami https://charts.bitnami.com/bitnami
helm repo update

# To create environments folder
mkdir -p environments/qa environments/prod

# To generate manifests
helm template nginx ./nginx -f environments/qa/values.yaml --namespace qa > environments/qa/nginx-manifest.yaml
helm template nginx ./nginx -f environments/prod/values.yaml --namespace prod > environments/prod/nginx-manifest.yaml

# To install charts (This will create the namespace and apply the manifest by updating the based on values.yaml on each environment folder)
helm install nginx ./nginx -f environments/prod/values.yaml --namespace prod --create-namespace
helm install nginx ./nginx -f environments/qa/values.yaml --namespace qa --create-namespace

