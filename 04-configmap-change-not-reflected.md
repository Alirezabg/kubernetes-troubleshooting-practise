## Issue 4: ConfigMap Changes Not Reflected
> Symptoms: After updating a ConfigMap, the changes are not reflected in the pods using it.

Two reasons are most common: [LINK](https://pauldally.medium.com/my-kubernetes-application-is-not-seeing-configmap-or-secret-updates-785da0c496ae#:~:text=Two%20reasons%20are%20most%20common,the%20file%20whenever%20it%20changes.)
1. The ConfigMap or Secret is being used as a subPath volumeMount. These mounts are not updated automatically.
2. The application is coded to cache the ConfigMap or Secret at container startup and does not re-read the file whenever it changes.

There are a few reasons why ConfigMap changes might not be reflected in pods using it:

* The pods are not configured to mount the ConfigMap.
* The pods are running with a cached version of the ConfigMap.
* The pods are using a subPath mount, which is not updated automatically.
* The application is caching the ConfigMap values and not reloading them when the ConfigMap changes.

To troubleshoot this issue, you can try the following steps:

Make sure that the pods are configured to mount the ConfigMap. You can check this by looking at the pod manifest. The ConfigMap mount should be defined in the volumeMounts section of the pod spec.
If the pods are running with a cached version of the ConfigMap, you can restart the pods to force them to pick up the latest version of the ConfigMap.
If the pods are using a subPath mount, you will need to manually update the subPath file to reflect the changes in the ConfigMap.
If the application is caching the ConfigMap values, you will need to update the application to reload the ConfigMap values when the ConfigMap changes.
Here are some specific troubleshooting tips:

If you are using a Deployment, StatefulSet, or DaemonSet, you can restart the pods by running the following command:
kubectl rollout restart deployment/statefulset/daemonset <name>
If you are using a standalone pod, you can restart the pod by running the following command:
kubectl restart pod <name>
If you are using a subPath mount, you can update the subPath file by running the following command:
kubectl exec -it <pod-name> -- echo "<new-value>" > /path/to/subPath/file
If the application is caching the ConfigMap values, you will need to consult the application documentation to learn how to reload the ConfigMap values.
