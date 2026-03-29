---
title: "IAM"
id: IAM
aliases: 
tags:
  - aws
---

## IAM : Users & Groups

iam - Identity and access management ,Global service
root create by default shouldn't be shared
Users are people within your organization and can be grouped
Groups can only contain user not others groups.


**IAM : Permissions**

. Users or Groups can be assigned Json documents called policies.
. These policies define the permissions of the users.


**IAM Policies structure**

- Consists of:
    . Version: policy language versoin.
    . Id: an idetifier for the policy(optional)
    . Statement: One or more individual statement(required)
- Statement Consists of:
    . Sid: an identifer for the statement (opt)
    . Effect: whether the statement allwos of denies access(allow or deny) 
    . Principle: account/user/role to which the policy is applied to.
    . Action: list of actions this policies allows or denies
    . Resource: list of resources to which the actions applied for.
    . Condition: conditions for when the policy is in effect(optional)

**IAM Roles for Services**

. Some AWS service need to perform actions on your behalf
. To do so we will assign permissions to aws services with IAM roles.
. Common Roles:
    . EC2 instance role
    . Lamda function role
    . Roles for cloudformation

**IAM Security tools**

- Iam credential report (account level)
    . a report that list all account users and the status of their various credentials

- Iam access advisor(user level)
    . Access advisor shows the service permissions granted to user and when those services were last accessed.
    . You can use this information to revise your policies.


----
[[aws]]
