## Issue 5: Node in NotReady State
> Symptoms: One of the cluster nodes is in a NotReady state when running kubectl get nodes.

A Kubernetes node in a NotReady state means that the node cannot be used to run pods. This can happen for a number of reasons, including:

The kubelet service is not running on the node.
The node has insufficient resources (CPU, memory, etc.).
The node has a network connectivity issue.
The node's kubelet is unable to connect to the Kubernetes API server.
There is a problem with the node's underlying infrastructure (e.g., a hardware failure).
To troubleshoot a node in a NotReady state, you can use the following steps:

Run the following command to get more information about the node:
`kubectl describe node <node-name>`
Look for any events in the output that indicate why the node is in a NotReady state. For example, if the kubelet service is not running, you will see an event like the following:
NodeNotReady 5m ago  kubelet, <node-name>  Node is not ready: Kubelet has failed to register
Once you have identified the reason why the node is in a NotReady state, you can take steps to fix the issue. For example, if the kubelet service is not running, you can start the kubelet service.
Here are some specific troubleshooting tips:

If the kubelet service is not running, you can start the kubelet service by running the following command:
systemctl start kubelet
If the node has insufficient resources, you can add more resources to the node or reduce the resource requests of the pods that are running on the node.
If the node has a network connectivity issue, you can check the node's network configuration and troubleshoot any network connectivity issues.
If the node's kubelet is unable to connect to the Kubernetes API server, you can check the connectivity between the node and the Kubernetes API server and troubleshoot any connectivity issues.
If there is a problem with the node's underlying infrastructure, you will need to contact your cloud provider or hardware vendor for assistance.