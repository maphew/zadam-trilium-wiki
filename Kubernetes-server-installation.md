As trilium can be run in Docker it also can be deployed in Kubernetes.
Trilium can be applied to Kubernetes manually or per helm chart.

The recommended way is helm.

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