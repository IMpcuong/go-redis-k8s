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