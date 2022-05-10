# argocd-app-configuration

The repository shows the implementation of GitOps for a simple node express app using argocd and it's associated services for RBAC and notifications/alerts to a dedicated slack channel.

See architectural diagram below

### Commands
```
# install ArgoCD in k8s
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

# access ArgoCD UI
kubectl get svc -n argocd
kubectl port-forward svc/argocd-server 8080:443 -n argocd

# login with admin user and below token (as in documentation):
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 --decode && echo

# The initial password can be deleted or changed
```

### Links


Config repo: https://devopsebenezer.westus.cloudapp.azure.com/ebenezermakinde/argocd-app-configuration


Docker repo: https://hub.docker.com/repository/docker/ebenezermakinde/simpleapp


Install ArgoCD: https://argo-cd.readthedocs.io/en/stable/getting_started/#1-install-argo-cd


Login to ArgoCD: https://argo-cd.readthedocs.io/en/stable/getting_started/#4-login-using-the-cli


ArgoCD Configuration: https://argo-cd.readthedocs.io/en/stable/operator-manual/declarative-setup/

ArgoCD Slack Notification setup: https://argocd-notifications.readthedocs.io/en/latest/services/slack/

### GitOps Flow
![Flow Diagram](GitOps_Flow.png)