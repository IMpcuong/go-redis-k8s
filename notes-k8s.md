1. `docker` must be conducted to run before the `minikube` has been started:

```pwsh
'C:\Program Files\Docker\Docker\resources\dockerd.exe'
```

to run just a `Docker-daemon`, that'll only let you run Docker Windows Containers.

- Or start the `docker` service with the `administrator` privileges:

```cmd
net start com.docker.service
```

- To make `docker` as the default driver for `minikube`, then start a cluster using the `docker` driver:

```bash
minikube config set driver docker
minikube start --driver=docker
```

2. `minikube`: create a cluster with this command

```bash
minikube start
```

- FIXME: `Pulling base image ...` -> `The image 'k8s.gcr.io/kube-proxy:v1.24.1' was not found; unable to add it to cache.`
  -> Maybe you need to using `gcloud` - the Google CLoud CLI to access the remote container registry.

- Solution: If your machine stands behine the firewall/proxy server ---> You need to configure ad below:

```bash
export http_proxy="http://<IP_Adress>:<Port>"
export https_proxy="http://<IP_Adress>:<Port>"
```

- NOTE: Whenever you have to face against this error `Unable to restart cluster, will reset it: apiserver healthz: apiserver process never appeared`, please following this advices step by step as below:

```bash
minikube delete

minikube start --v=5 # Or higher.

kubectl config use-context minikube

kubectl get pods --context=minikube
```
