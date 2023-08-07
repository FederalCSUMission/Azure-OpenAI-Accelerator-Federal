

# Steps to Install Weaviate on AKS: 

# Article provides the required steps: https://weaviate.io/developers/weaviate/installation/kubernetes

# 1. Create an AKS Cluster 
    az account set --subscription <Subscription ID>
    az aks get-credentials --resource-group <Resource Group Name> --name <AKS Cluster Name>    
# 2. Install HELM
    curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
    chmod 700 get_helm.sh
    ./get_helm.sh
3. Install kubectl
4. helm version (checks the helm version)
5. helm repo add weaviate https://weaviate.github.io/weaviate-helm  (Obtain the Helm Chart)
6. helm show values weaviate/weaviate > values.yaml (Deploy Weviate with values.yaml default values)
7. kubectl create namespace weaviate
8. helm upgrade --install "weaviate" weaviate/weaviate  --namespace "weaviate" --values ./values.yaml

# 9. Commands to verify the Weaviate installation:
    helm list -n weaviate
    helm repo list
    kubectl get pods -n weaviate
    kubectl get all 
    kubectl get all -n weaviate

# 10. Commands to test the Application:
    kubectl get services -n weaviate (Copy the EXTERNAL-IP from the weaviate service)
    Browser: http://<EXTERNAL-IP>/v1
    Shell Commands:
    curl EXTERNAL-IP
    curl <EXTERNAL-IP>/v1/schema
    curl <EXTERNAL-IP>/v1/meta  
    curl <EXTERNAL-IP>/v1/objects



