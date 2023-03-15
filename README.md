# tech

Example deployment of elasticsearch and kibana.
The manifests are intended to deploy to any kubernetes cluster.

If you have a jenkins instance set up with a kubeconfig file to your cluster, you can create a jenkins pipeline job and run the Jenkinsfile from the checked out github repo.

Otherwise, you can install the deployments manually through kubectl or with a script including the commands.

Steps:
- Install the namespace yaml (tech-assignment-namespace.yaml)
```
kubectl apply -f tech-assignment-namespace.yaml
```
- Install the yamls for elasticsearch (NoSQL database)
```
kubectl apply -f elasticsearch/es-cm.yaml
kubectl apply -f elasticsearch/es-svc.yaml
kubectl apply -f elasticsearch/es-svc-headless.yaml
kubectl apply -f elasticsearch/es-statefulset.yaml
```
- Install the yamls for kibana (front-end for elastic stack)
```
kubectl apply -f kibana/kibana-cm.yaml
kubectl apply -f kibana/kibana-svc.yaml
kubectl apply -f kibana/kibana-deployment.yaml
```
