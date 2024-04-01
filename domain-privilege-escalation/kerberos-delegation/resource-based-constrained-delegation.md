# Resource-Based Constrained Delegation

{% embed url="https://blog.netwrix.com/2022/09/29/resource-based-constrained-delegation-abuse/" %}

### Resource-Based Constrained Delegation (RBCD)

RBCD is a security feature in Windows environments that allows services to act on behalf of users by delegating permissions to access other resources, with the following key characteristics:

* **Constrained**: Limits delegation to specific services, enhancing security by preventing unrestricted delegation.
* **Resource-Based**: Configuration is performed on the target resource rather than the service account, enabling more granular control over what resources a service can access on behalf of a user.
* **Flexible Management**: Managed at the target resource, it allows administrators to easily define and adjust which services can delegate access to the resource.

#### Benefits

* **Enhanced Security**: By limiting the services that can delegate access, RBCD minimizes potential attack surfaces.
* **Administrative Ease**: Directly configuring resources simplifies delegation management.
* **Scalability**: Suitable for both small and large-scale environments.

RBCD plays a crucial role in modern Windows-based environments, providing a secure and manageable method for delegated authentication.
