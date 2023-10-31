## Issue 3: Liveness Probe Failing
> Symptoms: A pod keeps restarting frequently, and the description indicates the liveness probe is failing.

## [Configure Liveness, Readiness and Startup Probes](https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-startup-probes/)

##

A failing liveness probe indicates that Kubernetes considers the container to be unhealthy and restarts it. This can happen for a number of reasons, including:

The application is actually unhealthy and is unable to respond to the probe.
The probe is configured incorrectly and is failing even though the application is healthy.
There is a problem with the network between the Kubernetes node and the probe.
To troubleshoot a failing liveness probe, you can use the following steps:

Run the following command to get more information about the pod:
kubectl describe pod <pod-name>
Look for any events in the output that indicate why the liveness probe is failing. For example, if the probe is timing out, you will see an event like the following:
Liveness probe failed: http://localhost:8080/healthz: net/http: request canceled (Client.Timeout exceeded while awaiting headers)

Once you have identified the reason why the liveness probe is failing, you can take steps to fix the issue. For example, if the application is actually unhealthy, you need to fix the bug in the application. If the probe is configured incorrectly, you need to update the probe configuration. If there is a problem with the network, you need to troubleshoot the network issue.
Here are some specific troubleshooting tips for the symptoms you described:

If the pod keeps restarting frequently, it is possible that the liveness probe is configured to run too often. Try increasing the interval or initialDelay of the probe.
If the liveness probe is timing out, it is possible that the application is taking too long to respond to the probe. Try increasing the timeoutSeconds of the probe.
If the liveness probe is failing with an HTTP error, make sure that the application is actually listening on the port that the probe is targeting. You can use the following command to check if the application is listening on a port:
kubectl exec -it <pod-name> -- netstat -an | grep :<port>
If the application is not listening on the port, you need to update the probe configuration to target the correct port.
