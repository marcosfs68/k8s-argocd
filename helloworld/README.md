# Command Line

```bash
argocd login argocd.home.local

argocd app create hello-world-app \
--repo https://github.com/marcosfs68/k8s-argocd.git \
--path helloworld \
--dest-server https://kubernetes.default.svc \
--dest-namespace default \
--sync-policy automated
```
