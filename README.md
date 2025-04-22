# k8s-argocd

```bash
helm repo add argo https://argoproj.github.io/argo-helm
helm repo update
helm dependency build

helm install my-argo-cd . -n argocd --create-namespace -f values.yaml
```

This is based from this [Chart.yaml](https://github.com/argoproj/argo-helm/tree/argo-cd-7.8.27/charts/argo-cd).

```bash
helm upgrade -i my-argo-cd argo/argo-cd -n argocd --create-namespace \
  --set server.ingress.enabled=true \
  --set server.ingress.ingressClassName=nginx \
  --set global.domain='argocd.home.local'
  --set configs.params.server\\.insecure=true
```

You can open with http://localhost:8080 to test after make a port forward.

```bash
kubectl port-forward service/my-argo-cd-argocd-server -n argocd 8080:443
```

Login password can be get with this command:

```bash
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```

8225aY6u4utkDRrX
