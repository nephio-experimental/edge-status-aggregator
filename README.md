# Edge Status Aggregator 
Edge Status Aggregator watches and processes the NFDeployment custom resources. It runs on Nephio's management cluster.

## Description
Edge Status Aggregator(ESA) watches and processes Nephio's NFDeployment custom resources. The primary goal of ESA is to track and aggregate statuses of different NF instance's deployment.
EdgeStatusAggregator takes the topology information from NFDeployment CR, and builds a relationship graph to track each individual NF specific status. 
The changes in any individual status is reflected on NFDeployment's CR status.

## Getting Started
You’ll need a Kubernetes cluster to run against. You can use [KIND](https://sigs.k8s.io/kind) to get a local cluster for testing, or run against a remote cluster.
**Note:** Your controller will automatically use the current context in your kubeconfig file (i.e. whatever cluster `kubectl cluster-info` shows).

### Running on the cluster
1. Install Instances of Custom Resources:

```sh
make install
```

2. Build and push your image to the location specified by `IMG`:
	
```sh
make docker-build docker-push IMG=<some-registry>/edge-status-aggregator:tag
```
	
3. Deploy the controller to the cluster with the image specified by `IMG`:

```sh
make deploy IMG=<some-registry>/edge-status-aggregator:tag
```

4. Actually deploy the controller:

```sh
kubectl apply -f config/deployment/deployment.yaml
```

**Note** It is expected that your Kubernetes cluster will be running v1.11.0 of all the deployments running in the **cert-manager** namespace, namely: cert-manager, cert-manager-webhook, and cert-manager-cainjector. You can check via `kubectl describe <pod> -n cert-manager`. In case any of them isn't at v1.11.0, you can update via `kubectl edit deployment.apps/cert-manager{-webhook | -cainjector} -n cert-manager`

### Uninstall CRDs
To delete the CRDs from the cluster:

```sh
make uninstall
```

### Undeploy controller
UnDeploy the controller to the cluster:

```sh
make undeploy
```

## Contributing
// TODO: Add detailed information on how you would like others to contribute to this project

### How it works
This project aims to follow the Kubernetes [Operator pattern](https://kubernetes.io/docs/concepts/extend-kubernetes/operator/)

It uses [Controllers](https://kubernetes.io/docs/concepts/architecture/controller/) 
which provides a reconcile function responsible for synchronizing resources untile the desired state is reached on the cluster 

**NOTE:** `make run` does **NOT** work as the controller requires some environment variables and mountPaths to operate
