Sample dotnetFramework Project and implementing CI/CD with GitHub Actions


Docker Build using Dockerfile > Host the Docker Image on Azure Container registry > Deploy the Image on Azure Kubernetes service


Steps: 
1) Login to Azure on Azure CLI
az login 

2) Create Resource Group
az group create -n "<ResourceGroup>" -l westus	

3)Create a Service Principal
az ad sp create-for-rbac --name "myApp" --role contributor --scopes /subscriptions/<SUBSCRIPTION_ID>/resourceGroups/<RESOURCE_GROUP> --sdk-auth

Add the resulted JSON on GitHub Secrets with Name = AZURE_CREDENTIALS and value as resulted Json file
4) Build a container image and deploy to Azure Kubernetes Service cluster
The build and push of the container images is done using Azure/docker-login@v1 action. To deploy a container image to AKS, you will need to use the Azure/k8s-deploy@v1 action
