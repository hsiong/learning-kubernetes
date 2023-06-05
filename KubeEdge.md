# Deploying using Keadm

## Install keadm
```
docker run --rm kubeedge/installation-package:v1.12.1 cat /usr/local/bin/keadm > /usr/local/bin/keadm && chmod +x /usr/local/bin/keadm
```

## Setup Cloud Side (KubeEdge Master Node)

By default ports `10000` and `10002` in your cloudcore needs to be accessible for your edge nodes.

> **IMPORTANT NOTE:**
>
> 1. At least one of kubeconfig or master must be configured correctly, so that it can be used to verify the version and other info of the k8s cluster.
> 2. Please make sure edge node can connect cloud node using local IP of cloud node, or you need to specify public IP of cloud node with `--advertise-address` flag.∂
> 3. `--advertise-address` is the address exposed by the cloud side (will be added to the SANs of the CloudCore certificate), the default value is the local IP.

