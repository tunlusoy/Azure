# Azure Platform

## What Is It

## Why Use It

## Components

1. Resource Group

    A resource group is a container that holds related resources for an application. The resource group could include all of the resources for an application, or only those resources that are logically grouped together. You can decide how you want to allocate resources to resource groups based on what makes the most sense for your organization.

    There are some important factors to consider when defining your resource group:

    - All of the resources in your group should share the same life-cycle. You will deploy, update and delete them together. If one resource, such as a database server, needs to exist on a different deployment cycle it should be in another resource group.
    - Each resource can only exist in one resource group.
    - You can add or remove a resource to a resource group at any time.
    - You can move a resource from one resource group to another group.
    - A resource group can contain resources that reside in different regions.
    - A resource group can be used to scope access control for administrative actions.
    - A resource can be linked to a resource in another resource group when the two resources must interact with each other but they do not share the same life-cycle (for example, multiple apps connecting to a database).

2. Access Control

    Resource Manager enables you to control who has access to specific actions for your organization. It natively integrates role-based access control (RBAC) into the management platform and applies that access control to all services in your resource group. You can add users to pre-defined platform and resource-specific roles and apply those roles to a subscription, resource group, or other resource to limit access. For example, you can take advantage of the pre-defined role called Reader that permits users to view resources but not edit them. You add users in your organization that need this type of access to the Reader role and apply the role to the subscription, resource group or resource. Other platform roles include Owner, Contributor, and User Access Administrator.



4. Resource

    1. Tags

        Tags enable you to logically organize your resources. Only resources created through Resource Manager support tags. You cannot apply tags to classic resources.

        Resource Manager enables you to logically organize resources by applying tags. The tags consist of key/value pairs that identify resources with properties that you define. Examples of key/value pairs include:
        - dept : Accounting
        - environment: test

        When you view resources with a particular tag, you see resources from all of your resource groups. You are not limited to only resources in the same resource group which enables you to organize your resources in a way that is independent of the deployment relationships. Tags can be particularly helpful when you need to organize resources for billing or management.

        Tags provide a convenient way to identify and manage multiple resources. For example, if you want to delete all resources for a particular project, you will have to manually find those resources. Tagging allows you to quickly locate the resources and can be helpful when you need to organize resources for billing or management.

        Each resource or resource group can have a maximum of 15 tags. The tag name is limited to 512 characters, and the tag value is limited to 256 characters. To mark resources as belonging to the same category, apply the same tag to those resources.

