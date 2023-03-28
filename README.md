# Gitops Implementation ArfoCD

Pipeline is configured in such a way that whenever commit happens in main branch.

Github Actions will trigger a pipeline with below actions:

1. Build an Image
2. Push Image to ACR
3. Update commit tag in helm/values.yaml
4. Push the change
5. As soon as the tag has been replaced, ArgoCD will deployed the tag in AKS Cluster
6. Repo Structuring - In Progress
7. Added runners in K8s Cluster
