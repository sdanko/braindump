# Scopes

Azure trusts a particular Entra ID tenant.

In Active Directory, there is an idea of Root Management Group. You can create a 
hierarchy of management groups. There can be up to 6 levels of management groups.

RBAC, policies and budget are applied at the management group level. They are inherited from the
parent to child groups.

## Subscription

Subscriptions are created at the level of the management group. Subscriptions use a certain
billing model. RBAC, policies and budget can also be applied at the subscription level.

Resources are created in a certain resource group.RBAC, policies and budget can also be applied 
at the resource group level.

Resources in a resource group have a common lifecycle.