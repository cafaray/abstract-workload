# abstract-workload

This excercise is a copy of the excellent example and well documented in [medium.com](https://medium.com/@marom.itamar/building-kubernetes-operators-65fbb2043cd0) by (Itamar Marom)[https://medium.com/@marom.itamar]

The goal of the source code is demostrate the use of (kubebuilder)[https://book.kubebuilder.io/quick-start.html] to create CRDs and Controllers in Kubernetes in a "simple" way. 

One of the hardest part of this is the imperative needed knowledge of (GO)[https://go.dev/doc/tutorial/getting-started]. To be honest, I've buidl a couple of services, and a simple console application to start programming in golang. It's simple, and easy manage language, but as other ones, the importance is in the knowlege of the libraries, frameworks, and so on. 

Please, take a look to the serie by Itamar in Medium, here the (link)[https://medium.com/@marom.itamar/kubernetes-controllers-custom-resources-and-operators-explained-8e92f46829f6]

## Description

This CRD help you creating a stateless (Deploy) or stateful (StatefulSet) application with minimun information. Here the API definition:

- replicas
- containerImage
- workloadType (stateless or stateful)

When the yaml of the CRD is applied, the controller creates the deployment or statefulset element to satisfy the required state. 

## Getting Started
You’ll need a Kubernetes cluster to run against. You can use [KIND](https://sigs.k8s.io/kind) to get a local cluster for testing, or run against a remote cluster.
**Note:** Your controller will automatically use the current context in your kubeconfig file (i.e. whatever cluster `kubectl cluster-info` shows).

### Running on the cluster
1. Install Instances of Custom Resources:

```sh
kubectl apply -f config/samples/
```

2. Build and push your image to the location specified by `IMG`:
	
```sh
make docker-build docker-push IMG=<some-registry>/abstract-workload:tag
```
	
3. Deploy the controller to the cluster with the image specified by `IMG`:

```sh
make deploy IMG=<some-registry>/abstract-workload:tag
```

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

### How it works
This project aims to follow the Kubernetes [Operator pattern](https://kubernetes.io/docs/concepts/extend-kubernetes/operator/)

It uses [Controllers](https://kubernetes.io/docs/concepts/architecture/controller/) 
which provides a reconcile function responsible for synchronizing resources untile the desired state is reached on the cluster 

### Test It Out
1. Install the CRDs into the cluster:

```sh
make install
```

2. Run your controller (this will run in the foreground, so switch to a new terminal if you want to leave it running):

```sh
make run
```

**NOTE:** You can also run this in one step by running: `make install run`

### Modifying the API definitions
If you are editing the API definitions, generate the manifests such as CRs or CRDs using:

```sh
make manifests
```

**NOTE:** Run `make --help` for more information on all potential `make` targets

More information can be found via the [Kubebuilder Documentation](https://book.kubebuilder.io/introduction.html)

## License

Copyright 2022.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

