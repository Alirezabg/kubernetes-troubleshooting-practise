## Issue 2: Service Not Accessible
> Symptoms: A service is deployed, but users cannot access the app using the service's Cluster IP or NodePort.

# [Debug Services](https://kubernetes.io/docs/tasks/debug/debug-application/debug-service/)


If a service is deployed but users cannot access the app using the service's Cluster IP or NodePort, it could be due to a number of factors, including:

* The service is not ready.
* The service type is not correct.
* The service is not exposed to the outside world.
* There is a problem with the pods that the service is targeting.
* There is a problem with the network between the user's machine and the Kubernetes cluster.


To troubleshoot a service that is not accessible, you can use the following steps:

Run the following command to get more information about the service:<br />
`kubectl describe service <service-name>`<br />
Look for any events in the output that indicate why the service is not accessible. For example, if the service is not ready, you will see an event like the following:<br />
Endpoints for service <service-name> are not ready yet.<br />

Once you have identified the reason why the service is not accessible, you can take steps to fix the issue. For example, if the service is not ready, you need to wait for the pods that the service is targeting to come up and be ready.<br />
Here are some specific troubleshooting tips for the symptoms you described:

If users cannot access the app using the service's Cluster IP, make sure that the service is exposed to the outside world. You can do this by setting the type field in the service manifest to LoadBalancer.<br />
If users cannot access the app using the service's NodePort, make sure that the NodePorts are exposed to the outside world. You can do this by configuring your firewall to allow traffic to the NodePorts.
If you are using a load balancer, make sure that the load balancer is configured correctly and that the service's NodePorts are mapped to the load balancer's ports.<br />
If the pods that the service is targeting are not running, the service will not be accessible. Make sure that the pods are running and that they are healthy.
