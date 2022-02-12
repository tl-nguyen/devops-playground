# devops-playground
Testing capabilities of some DevOps tools

```
helm repo add argo-cd https://argoproj.github.io/argo-helm
helm dep update helm/charts/argo-cd/
helm upgrade --install argo-cd helm/charts/argo-cd/ \     
--create-namespace --namespace argocd --wait

kubectl apply -f helm/root.yaml 

kubectl get secret argocd-initial-admin-secret \
--namespace argocd \
--output jsonpath="{.data.password}" \
| base64 -d; echo

kubectl port-forward svc/argo-cd-argocd-server 8080:443 \
--namespace argocd
```
