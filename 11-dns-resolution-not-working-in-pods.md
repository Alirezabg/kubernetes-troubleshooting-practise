## Issue 11: DNS Resolution Not Working in Pods
> Symptoms: Applications within pods are unable to resolve domain names, leading to failures when trying to access external services.

There are a number of reasons why DNS resolution might not be working in pods, including:

The CoreDNS pods are not running or are in an unhealthy state.
The pods are not configured to use CoreDNS.
The pods are using a custom DNS resolver that is not configured correctly.
There is a network connectivity issue between the pods and CoreDNS.
There is a problem with the Kubernetes networking plugin.
To troubleshoot DNS resolution failures in pods, you can use the following steps:

Verify that the CoreDNS pods are running and healthy. You can do this by running the following command:
kubectl get pods -n kube-system -l k8s-app=kube-dns
If any of the CoreDNS pods are not running or are in an unhealthy state, you can restart them or scale the CoreDNS deployment.

Verify that the pods are configured to use CoreDNS. You can check the pod's DNS configuration by running the following command:
kubectl describe pod <pod-name>
Look for the dnsConfig field in the pod spec. If the dnsConfig field is not empty, the pod is using a custom DNS resolver. If the dnsConfig field is empty, the pod is using CoreDNS.

If the pods are using a custom DNS resolver, verify that it is configured correctly. You can check the documentation for the custom DNS resolver to see how to configure it.

Verify that there is no network connectivity issue between the pods and CoreDNS. You can do this by running the following command on one of the pods:

ping <IP address of CoreDNS pod>
If the ping fails, there is a network connectivity issue between the pods and CoreDNS.

Verify that the Kubernetes networking plugin is working correctly. You can check the status of the Kubernetes networking plugin by running the following command:
kubectl get pods -n kube-system -l component=kube-proxy
If the pod is not running or is in an unhealthy state, there is a problem with the Kubernetes networking plugin.

If you are still having trouble troubleshooting DNS resolution failures in pods, you can consult the Kubernetes documentation or ask for help on the Kubernetes community forums.

Here are some additional troubleshooting tips:

Check the Kubernetes logs for errors related to DNS resolution.
Try restarting the Kubernetes networking plugin.
Try deleting the pods and recreating them.
Try upgrading to the latest version of Kubernetes.