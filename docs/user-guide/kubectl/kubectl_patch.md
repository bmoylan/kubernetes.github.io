---
assignees:
- bgrant0607
- caesarxuchao

---

## kubectl patch

Update field(s) of a resource using strategic merge patch.

### Synopsis


Update field(s) of a resource using strategic merge patch

JSON and YAML formats are accepted.

Please refer to the models in https://htmlpreview.github.io/?https://github.com/kubernetes/kubernetes/blob/release-1.2/docs/api-reference/v1/definitions.html to find if a field is mutable.

```
kubectl patch (-f FILENAME | TYPE NAME) -p PATCH
```

### Examples

```

# Partially update a node using strategic merge patch
kubectl patch node k8s-node-1 -p '{"spec":{"unschedulable":true}}'

# Partially update a node identified by the type and name specified in "node.json" using strategic merge patch
kubectl patch -f node.json -p '{"spec":{"unschedulable":true}}'

# Update a container's image; spec.containers[*].name is required because it's a merge key
kubectl patch pod valid-pod -p '{"spec":{"containers":[{"name":"kubernetes-serve-hostname","image":"new image"}]}}'

# Update a container's image using a json patch with positional arrays
kubectl patch pod valid-pod --type='json' -p='[{"op": "replace", "path": "/spec/containers/0/image", "value":"new image"}]'
```

### Options

```
  -f, --filename=[]: Filename, directory, or URL to a file identifying the resource to update
  -o, --output="": Output mode. Use "-o name" for shorter output (resource/name).
  -p, --patch="": The patch to be applied to the resource JSON file.
      --record[=false]: Record current kubectl command in the resource annotation.
      --type="strategic": The type of patch being provided; one of [json merge strategic]
```

### Options inherited from parent commands

```
      --alsologtostderr[=false]: log to standard error as well as files
      --certificate-authority="": Path to a cert. file for the certificate authority.
      --client-certificate="": Path to a client certificate file for TLS.
      --client-key="": Path to a client key file for TLS.
      --cluster="": The name of the kubeconfig cluster to use
      --context="": The name of the kubeconfig context to use
      --insecure-skip-tls-verify[=false]: If true, the server's certificate will not be checked for validity. This will make your HTTPS connections insecure.
      --kubeconfig="": Path to the kubeconfig file to use for CLI requests.
      --log-backtrace-at=:0: when logging hits line file:N, emit a stack trace
      --log-dir="": If non-empty, write log files in this directory
      --log-flush-frequency=5s: Maximum number of seconds between log flushes
      --logtostderr[=true]: log to standard error instead of files
      --match-server-version[=false]: Require server version to match client version
      --namespace="": If present, the namespace scope for this CLI request.
      --password="": Password for basic authentication to the API server.
  -s, --server="": The address and port of the Kubernetes API server
      --stderrthreshold=2: logs at or above this threshold go to stderr
      --token="": Bearer token for authentication to the API server.
      --user="": The name of the kubeconfig user to use
      --username="": Username for basic authentication to the API server.
      --v=0: log level for V logs
      --vmodule=: comma-separated list of pattern=N settings for file-filtered logging
```

### SEE ALSO

* [kubectl](/docs/user-guide/kubectl/kubectl/)	 - kubectl controls the Kubernetes cluster manager

###### Auto generated by spf13/cobra on 2-Mar-2016

