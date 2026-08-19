# argocd-app-example1

Simple nginx hello world app for Argo CD GitOps deployment in Kubernetes.

## Layout

- `manifests/` contains the Kubernetes resources for the app.
- `argocd/application.yaml` contains the Argo CD `Application` resource.

## Deploy with Argo CD

Apply `argocd/application.yaml` to the cluster where Argo CD is installed:

```sh
kubectl apply -f argocd/application.yaml
```

The Application deploys the app into the `argocd-app-example1` namespace and
creates that namespace automatically if your Argo CD installation has permission.

The app exposes an internal ClusterIP service named `nginx-hello-world` on port
80. To test it from your machine:

```sh
kubectl -n argocd-app-example1 port-forward svc/nginx-hello-world 8080:80
```

Then open `http://localhost:8080`.
