# Resource Locks, Tags and Blueprints

## Resource locks

You can apply resource locks at different levels like subscription, resource group, resource etc.
Two types:
- Dont delete
- Read only

## Tags

Tags are metadata. It is a key and a value. You can also set it at different levels.
Tags don't get inherited.

## Blueprint

You can define different types of artifacts like ARM template, RBAC and policy and assign it 
to a subscription. Blueprints can have different types of locks:
- Dont lock
- Do not delete
- Read only