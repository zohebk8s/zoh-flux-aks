# Gitops Implementation ArgoCD:

Pipeline is configured in such a way that whenever commit happens in main branch.

Github Actions will trigger a pipeline with below actions:

1. Build an Image
2. Push Image to ACR
3. Update commit tag in helm/values.yaml
4. Push the change
5. As soon as the tag has been replaced, ArgoCD will deployed the tag in AKS Cluster
6. Added runners in K8s Cluster
7. Runners are available in GKE Cluster.

The runner deployment will not work in GKE -v1.24.9-gke.3200. In cluster, the runners will be up/running. But it won't be availble to use.(As it will be in offline state in Github)

Add below code in order to make it work:

<img width="173" alt="image" src="https://user-images.githubusercontent.com/128701612/231151321-87e14148-39f2-4110-9ec4-06dad5f55ef7.png">

