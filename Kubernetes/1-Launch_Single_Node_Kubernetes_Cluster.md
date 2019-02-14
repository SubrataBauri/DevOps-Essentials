# Launch Single Node Kubernetes Cluster

# Step 1 - Start Minikube
## Install and start Minikube
`minikube version`

`minikube start`

# Step 2 - Cluster Info
## Details of the cluster and its health status
`kubectl cluster-info`

## To view the nodes in the cluster 
`kubectl get nodes`

# Step 3 - Deploy Containers
## Deploy containers onto the cluster
Using kubectl run, it allows containers to be deployed onto the cluster - 

`kubectl run first-deployment --image=katacoda/docker-http-server --port=80`

## Status of the deployment can be discovered via the running Pods - 
`kubectl get pods`

Once the container is running it can be exposed via different networking options, depending on requirements. One possible solution is NodePort, that provides a dynamic port to a container.

`kubectl expose deployment first-deployment --port=80 --type=NodePort`

## Find the allocated port and executes a HTTP request
```
export PORT=$(kubectl get svc first-deployment -o go-template='{{range.spec.ports}}{{if .nodePort}}{{.nodePort}}{{"\n"}}{{end}}{{end}}')
echo "Accessing host01:$PORT"
curl host01:$PORT
```
