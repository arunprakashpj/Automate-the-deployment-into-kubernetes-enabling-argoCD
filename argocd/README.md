## ArgoCD Manifests 

Place the ArgoCD manifests in this directory.
## kubectl get pods -n argocd -l app.kubernetes.io/name=argocd-server -o name | cut -d'/' -f2