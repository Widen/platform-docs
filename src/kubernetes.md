---
title: Kubernetes @ Widen
---

# Kubernetes @ Widen

## About
"[Kubernetes](http://kubernetes.io/docs/whatisk8s) is an open-source system for automating deployment, scaling, and management of containerized applications."

---
## CLI
###  Installation (OSX)
1. `brew update && brew install kubernetes-cli`
2. Obtain current kubeconfig from Platform Team
3. Copy kubeconfig to `~/.kube/config`

### Cheat Sheet
#### Viewing & finding resources
```
# Columnar output
$ kubectl config current-context              # View current context (cluster/user)
$ kubectl config use-context                  # Switch context
$ kubectl get services --all-namespaces       # List services in all namespaces
$ kubectl get namespaces                      # List namespaces
$ kubectl --namespace=<namespace> get pods    # List pods in a namespace
$ kubectl get pods -o wide                    # List pods in the default namespace, with more details
$ kubectl get replicaset <replicaset>         # View a ReplicaSet

# Verbose output
$ kubectl describe nodes <node>               # Describe a node
$ kubectl describe pods <replicaset>          # Describe pods created by a ReplicaSet
```
#### Creating, modifying & deleting resources
```
$ kubectl create -f <file.yaml>     # Create resource(s) from a single YAML file
$ kubectl create -f <dir>           # Create resources from all YAML and JSON files in a directory
$ kubectl create -f <URL>           # Create resource(s) from a URL

$ kubectl apply -f <file.yaml>      # Apply changes to (or create) resource(s) from a single YAML file

$ kubectl delete pod <pod>          # Delete a pod (will be re-created if managed by a ReplicaSet)
```
#### Interacting with running pods
```
$ kubectl logs <pod>          # Dump a pod's logs to stdout
$ kubectl logs <pod> -f       # Stream a pod's logs to stdout until canceled (ctrl-C) or timeout

$ kubectl run -it <pod> --image=<image> -- <command>  # Run an interactive command in a new pod
$ kubectl attach -i <pod>                             # Attach to a running pod
$ kubectl port-forward <pod> <port>                   # Forward a pod's port to the local port
$ kubectl exec -it <pod> -- <command>                 # Run an interactive command in a single-container pod
$ kubectl exec <pod> -c <container> -- <command>      # Run a command in a multiple-container pod
```

---
## External References
* [http://kubernetes.io/docs/user-guide/kubectl-overview/](http://kubernetes.io/docs/user-guide/kubectl-overview/)
