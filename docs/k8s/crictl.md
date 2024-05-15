## overview
**`crictl`** 是一个用于与容器运行时（如 `containerd、CRI-O` 等）进行交互的命令行工具。它是一个专门用于 `Kubernetes` 容器运行时接口（`CRI`）的客户端工具，用于管理和操作容器、镜像和其他相关资源。

## crictl cmd

```shell
root@test-cluster-worker:/# crictl
NAME:
   crictl - client for CRI

USAGE:
   crictl [global options] command [command options] [arguments...]

VERSION:
   1.28.0

COMMANDS:
   attach              Attach to a running container
   create              Create a new container
   exec                Run a command in a running container
   version             Display runtime version information
   images, image, img  List images
   inspect             Display the status of one or more containers
   inspecti            Return the status of one or more images
   imagefsinfo         Return image filesystem info
   inspectp            Display the status of one or more pods
   logs                Fetch the logs of a container
   port-forward        Forward local port to a pod
   ps                  List containers
   pull                Pull an image from a registry
   run                 Run a new container inside a sandbox
   runp                Run a new pod
   rm                  Remove one or more containers
   rmi                 Remove one or more images
   rmp                 Remove one or more pods
   pods                List pods
   start               Start one or more created containers
   info                Display information of the container runtime
   stop                Stop one or more running containers
   stopp               Stop one or more running pods
   update              Update one or more running containers
   config              Get and set crictl client configuration options
   stats               List container(s) resource usage statistics
   statsp              List pod statistics. Stats represent a structured API that will fulfill the Kubelet's /stats/summary endpoint.
   metricsp            List pod metrics. Metrics are unstructured key/value pairs gathered by CRI meant to replace cAdvisor's /metrics/cadvisor endpoint.
   completion          Output shell completion code
   checkpoint          Checkpoint one or more running containers
   runtime-config      Retrieve the container runtime configuration
   help, h             Shows a list of commands or help for one command

GLOBAL OPTIONS:
   --config value, -c value            Location of the client config file. If not specified and the default does not exist, the program's directory is searched as well (default: "/etc/crictl.yaml") [$CRI_CONFIG_FILE]
   --debug, -D                         Enable debug mode (default: false)
   --image-endpoint value, -i value    Endpoint of CRI image manager service (default: uses 'runtime-endpoint' setting) [$IMAGE_SERVICE_ENDPOINT]
   --runtime-endpoint value, -r value  Endpoint of CRI container runtime service (default: uses in order the first successful one of [unix:///var/run/dockershim.sock unix:///run/containerd/containerd.sock unix:///run/crio/crio.sock unix:///var/run/cri-dockerd.sock]). Default is now deprecated and the endpoint should be set instead. [$CONTAINER_RUNTIME_ENDPOINT]
   --timeout value, -t value           Timeout of connecting to the server in seconds (e.g. 2s, 20s.). 0 or less is set to default (default: 2s)
   --help, -h                          show help
   --version, -v                       print the version
root@test-cluster-worker:/# crictl pods
POD ID              CREATED             STATE               NAME                                 NAMESPACE           ATTEMPT             RUNTIME
2dee5c34ee734       47 hours ago        Ready               prometheus-server-574dbc6996-4j9j9   default             0                   (default)
5ae1b6597f5d4       2 days ago          Ready               kube-proxy-rstsz                     kube-system         0                   (default)
6eb9790418750       2 days ago          Ready               kindnet-dgbgj                        kube-system         0                   (default)
root@test-cluster-worker:/#
```
