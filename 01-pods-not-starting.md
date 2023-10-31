 ## Issue 1: Pods Not Starting
> Symptoms: A user deploys a new pod using a manifest, but the pod remains in the Pending state. 

## [Debug Pods](https://kubernetes.io/docs/tasks/debug/debug-application/debug-pods/#:~:text=If%20a%20Pod%20is%20stuck,or%20another%20that%20prevent%20scheduling.)

If a pod remains in the Pending state, it means that Kubernetes cannot schedule the pod to a node. This can happen for a number of reasons, including:

* Insufficient resources: The pod requests more resources (CPU, memory, etc.) than are available on any node in the cluster.<br />
* Image pull failure: Kubernetes cannot pull the container image(s) specified in the pod manifest.<br />
* Node scheduling conflict: The pod has a scheduling constraint that cannot be satisfied by any node in the cluster.<br />
* Persistent volume claim (PVC) binding failure: The pod requests a PVC that cannot be bound to a persistent volume.

To troubleshoot a pod that is stuck in the Pending state, you can use the following steps:

Run the following command to get more information about the pod:<br />
` kubectl describe pod <pod-name> `<br />
Look for any events in the output that indicate why the pod cannot be scheduled. For example, if the pod is requesting more resources than are available, you will see an event like the following:<br />
FailedScheduling 4m ago  kubelet, pod-name  Failed to find a fit for a pod. Found 0 nodes that satisfied all constraints. Insufficient cpu (requested: 2, available: 1)

Once you have identified the reason why the pod is not starting, you can take steps to fix the issue. For example, if the pod is requesting more resources than are available, you can reduce the resource requests or add more nodes to the cluster.<br />
Here are some specific troubleshooting tips for the symptoms you described:

If the user is deploying a new pod, make sure that the pod manifest is correct and that the container image(s) are available in the registry.<br />
If the user is deploying an existing pod, make sure that the pod is not bound to a hostPort or that the hostPort is not already in use.
If the user is deploying a pod that requests a PVC, make sure that the PVC is bound to a persistent volume.