# Issue 8: RBAC Permissions Error
> Symptoms: An application or operator running in a pod cannot access or modify Kubernetes resources and logs indicate permission-related errors.

RBAC permissions errors are common in Kubernetes, and can be caused by a variety of factors, including:

* Incorrect role or role binding assignments
* Missing permissions for a specific resource or operation
* Namespaces not being explicitly granted access to resources
To troubleshoot RBAC permissions errors, you can follow these steps:

Identify the resource or operation that is being denied. You can do this by examining the error message in the pod logs.
Verify that the pod has the correct role and role binding assignments. You can use the following commands to check the role and role binding assignments for a pod:
`kubectl get rolebindings -n <namespace>`
`kubectl get roles -n <namespace>`
Verify that the pod has the required permissions for the resource or operation. You can use the following command to check the permissions for a role or role binding:
`kubectl describe role <role-name> -n <namespace>`
Grant the pod the required permissions. You can do this by creating a new role binding or by adding the required permissions to an existing role binding.
Here are some specific troubleshooting tips for RBAC permissions errors:

If the pod is trying to access a resource in a different namespace, make sure that the namespace is explicitly granted access to the resource. You can do this by adding the namespace to the subjects field of the role binding.
If the pod is trying to perform an operation on a resource that is not explicitly allowed by its role, you can add the required permission to the role.
If you are using a third-party application or operator, make sure that it has the required permissions. You can check the documentation for the application or operator to see what permissions it needs.
