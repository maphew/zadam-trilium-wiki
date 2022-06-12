As Trilium can be run in Docker it also can be deployed in Kubernetes.
Trilium can be applied to Kubernetes manually or per helm chart.

The recommended way is helm.

# Root privileges

Trilium docker container needs to be run with root privileges, while Kubernetes by default runs containers under unprivileged users. You will have to [configure this in Deployment descriptor](https://dev.to/techworld_with_nana/run-pod-with-root-privileges-41n9).

# Helm Install

Unofficial helm chart by [ohdearaugustin](https://github.com/ohdearaugustin): https://github.com/ohdearaugustin/charts

## Add helm repository

```
helm repo add <repo_name> https://ohdearaugustin.github.io/charts/
"<repo_name>" has been added to your repositories
```

## How to install a chart
Just `helm install <repo_name>/trilium-notes`.

For more information on using Helm, refer to the Helm documentation.