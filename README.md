# Azure Microk8s Test

Relevant things:

- [This GitHub repo](https://github.com/theopolis/azure-microk8s-test)
- [The azure-microk8s-test/azure-microk8s-test project](https://dev.azure.com/azure-microk8s-test/azure-microk8s-test)
- [The Azure Pipelines app](https://github.com/apps/azure-pipelines)
- [PATs Configuration](https://dev.azure.com/azure-microk8s-test/_usersSettings/tokens)

Links I found useful:

- [Getting started with Azure and GitHub](https://docs.microsoft.com/en-us/azure/devops/pipelines/repos/github?view=azure-devops&tabs=yaml)
- [Create your first pipeline](https://docs.microsoft.com/en-us/azure/devops/pipelines/create-first-pipeline)
- [Use Azure and self-hosted agencts](https://docs.microsoft.com/en-us/azure/devops/pipelines/get-started-multiplatform?view=azure-devops)
- [Run the Azure DevOps agent in Docker](https://docs.microsoft.com/en-us/azure/devops/pipelines/agents/docker?view=azure-devops)
- [Setup PATs for Access](https://docs.microsoft.com/en-us/azure/devops/organizations/accounts/use-personal-access-tokens-to-authenticate?view=azure-devops&tabs=preview-page)

The final parts:

```
docker build -t localhost:32000/azpagent:registry .
docker push localhost:32000/azpagent
microk8s kubectl create secret generic azure-microk8s-secret \
 --from-literal=AZP_URL=https://dev.azure.com/<ORG HERE> \
 --from-literal=AZP_TOKEN=<TOKEN HERE>
microk8s kubectl apply -f azure-microk8s-deployment.yaml 
```
