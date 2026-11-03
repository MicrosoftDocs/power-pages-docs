---
title: Manage administrative access to Power Pages with role-based access control (preview)
description: Power Pages role-based access control (RBAC) grants precise admin access to sites. Learn how roles, scopes, and principals work during the preview.
ms.date: 10/30/2026
ms.topic: concept-article
author: shwetamurkute
ms.author: smurkute
---

# Manage administrative access to Power Pages with role-based access control (preview)

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-banner.md)]

**Power Pages role-based access control (RBAC)** is an authorization system that grants users, groups, service principals, and managed identities precise administrative access to Power Pages resources. Instead of granting broad administrative access across the tenant, RBAC controls who can view, manage, or delete Power Pages resources and where they can perform those actions.

> [!IMPORTANT]
> This feature is in preview. Preview features aren't meant for production use and might have restricted functionality. These features are subject to [supplemental terms of use](https://go.microsoft.com/fwlink/?linkid=2189520) and are available before an official release so customers can get early access and provide feedback.

For example, an automation identity can manage sites in one environment, or a user can view the configuration of one site without access to every Power Pages site in the tenant.

Power Pages RBAC is built on [role-based access control for Power Platform](/power-platform/admin/security/role-based-access-control). Power Pages adds built-in roles for Power Pages operations and a site-level scope for access to an individual site.

> [!NOTE]
> Power Pages RBAC controls administrative access to Power Pages resources. It doesn't control what site users can access. Continue to use [web roles](../security/create-web-roles.md), [table permissions](../security/table-permissions.md), and [page permissions](../security/page-security.md) to manage site-user access.

## Prerequisites

- Familiarity with [Role-based access control for Power Platform](/power-platform/admin/security/role-based-access-control)
- Familiarity with the [Power Platform API](/rest/api/power-platform/)

## Expectations and limitations

During preview, Power Platform RBAC is primarily intended for administration through the Power Platform API and management SDKs, including automation that uses service principals and managed identities.

The following limitations apply during preview:

- Manage role assignments through the Power Platform API and management SDKs.
- Can't customize built-in role definitions.

## Role assignment components

A role assignment combines three parts:

| **Part** | **What it determines** | **Power Pages example** |
|----|----|----|
| **Security principal** | Who receives access. A principal can be a user, security-enabled group, service principal, or managed identity. | A service principal used by site-monitoring automation. |
| **Role** | What the principal can do. | View Power Pages sites and their configuration. |
| **Scope** | Where the principal can perform those actions. | One environment or one Power Pages site. |

The following example grants a monitoring service principal read-only access to Power Pages sites in one environment:

```text
Monitoring service principal + Power Pages Reader + Environment A
```

The same principal can have different roles at different scopes. For more information about security principals, role assignments, and inheritance, see [Role-based access control for Power Platform](/power-platform/admin/security/role-based-access-control).

## Role families

Power Pages provides two families of built-in roles. A principal might need to manage the site, work with Power Pages data in Dataverse, or do both. When both are required, assign a role from each family.

| **Role family** | **Grants access to** | **Use for** |
|----|----|----|
| **Management roles** | Site infrastructure and configuration, including site lifecycle operations, web application firewall (WAF) rules, custom domains, certificates, IP address rules, security scans, and site settings. | Operating and configuring Power Pages sites without granting access to the site's business data in Dataverse. |
| **Data access roles** | Power Pages data stored in Dataverse, such as the website record used when provisioning a site or a security scan report. | Automation that creates sites or performs other operations that require access to Power Pages data in Dataverse. |

The role families separate site management from data access. A principal with only a management role can operate site infrastructure but can't use that role to read or change business data in Dataverse. A principal with only a Data access role can work with the allowed Power Pages data but can't use that role to reconfigure site infrastructure.

> [!NOTE]
> Power Pages Data roles don't replace Dataverse security roles or the web roles and table permissions used to protect data from website users.

## Permission levels

Each role family provides three levels of access:

- **Reader** provides view-only access.
- **Contributor** includes Reader permissions and adds create, update, or management operations.
- **Owner** includes Contributor permissions and adds delete operations.

Choose the lowest level that supports the required work.

### Power Pages Management roles

| **Role** | **Role ID** | **Permissions** | **What a principal can do (Not Exhaustive)** |
|----|----|----|----|
| **Power Pages Reader** |  |  | View sites and their configuration, including site details, WAF status and rules, custom domain and SSL configuration, IP rules, security scan status, and governance settings. The role can't make changes. |
| **Power Pages Contributor** |  |  | Perform Reader operations and manage sites. This role includes starting, stopping, and restarting sites; configuring WAF and IP address rules; managing custom domains, SSL bindings, and certificates; starting security scans; and updating site settings such as data loss prevention, visibility, and security group settings. The role can't delete resources. |
| **Power Pages Owner** |  |  | Perform Contributor operations and delete sites. |

### Power Pages data access roles

| **Role** | **What a principal can do** |
|----|----|
| **Power Pages Data Reader** | Read allowed Power Pages data stored in Dataverse, such as retrieving a security scan report. |
| **Power Pages Data Contributor** | Perform Data Reader operations and create or update allowed Power Pages data, such as creating the website record when provisioning a site. |
| **Power Pages Data Owner** | Perform Data Contributor operations and delete allowed Power Pages data. |

You can't change Power Pages roles. Listing the available role definitions before creating an assignment provides the current role names, permissions, and role definition IDs. Role definition IDs returned by the API are the authoritative source; don't copy or hard-code IDs from documentation.

## Scopes

The scope determines which resources the role assignment covers. Power Platform provides tenant, environment group, and environment scopes. Power Pages adds an individual site scope beneath the environment.

```text
Tenant
└── Environment group
    └── Environment
        └── Power Pages site
```

A role assignment applies to its selected scope and the resources beneath it. For example:

- A role assigned at the tenant scope is inherited by the environment groups, environments, and sites in the tenant.
- A role assigned at the environment scope applies to the Power Pages sites in that environment.
- A role assigned at the site scope applies only to that site.

Assigning the role at the narrowest scope that covers the principal's work reduces the number of resources that can be affected if the principal's credentials are compromised.

For a detailed explanation of the Power Platform scope hierarchy and inheritance, see [Scope](/power-platform/admin/security/role-based-access-control#scope).

### Power Pages site scope

The site scope applies when a principal needs access to only one Power Pages site. Specify the site beneath its environment by using the following scope:

```text
/tenants/{tenantId}/environments/{environmentId}/powerpages/{siteId}
```

A role assigned at this scope authorizes operations on that site only. It doesn't authorize an operation that acts on the entire environment.

### Supported scopes for each role family

The role families support different assignment scopes:

- **Management roles** can be assigned from the tenant scope down to an individual Power Pages site.
- **Data access roles** can be assigned only at the environment or Power Pages site scope. You can't assign them above the environment because the associated Dataverse data belongs to a specific environment.

## Role and scope examples

The following examples show how least privilege applies to common Power Pages scenarios:

| **Scenario** | **Recommended role** | **Recommended scope** |
|----|----|----|
| A monitoring service principal lists sites and reads their status in one environment. | Power Pages Reader | The environment being monitored |
| An operations identity starts and stops sites and manages custom domains in one environment. | Power Pages Contributor | The environment being managed |
| A support administrator needs to inspect the configuration of one site. | Power Pages Reader | The individual site |
| Automation provisions new Power Pages sites and creates the required website records. | Power Pages Data Contributor, together with any required Management role | The target environment |
| An administrator decommissions one site and deletes its custom domain. | Power Pages Owner | The individual site |

If a principal needs both site-management operations and access to Power Pages data in Dataverse, assign the appropriate role from each family. Don't grant Owner access when Contributor access is sufficient.

## Role assignment requirements

Creating a Power Pages role assignment requires:

- A calling identity with the **Power Platform Administrator** or **Power Platform role-based access control administrator** role.
- The object ID of the principal receiving access. For a service principal, use the Enterprise Application object ID, not the application or client ID.
- The Power Pages role definition ID returned by the role-definitions API.
- The identifiers required to construct the selected scope.

## Role assignment process

Power Pages uses the same assignment process as Power Platform RBAC. The process involves authenticating with the Power Platform API, listing the available role definitions to select the required Power Pages role, creating a role assignment that contains the principal object ID, role definition ID, principal type, and scope, and then listing the role assignments to verify the assignment.

For the authentication and API steps, see [Tutorial: Assign roles to service principals](/power-platform/admin/programmability-tutorial-rbac-role-assignment). In the assignment request, substitute:

- The role definition ID for the selected Power Pages role.
- The tenant, environment group, environment, or Power Pages site scope required for the scenario.

When assigning a role to one site, use the following scope format:

```text
/tenants/{tenantId}/environments/{environmentId}/powerpages/{siteId}
```

## Common role assignment issues

### The principal has a role but the operation is denied

The assignment's scope might not cover the operation. A role assigned to one site doesn't authorize an environment-wide operation. A role assigned to the environment is inherited by its sites.

### The role doesn't include the required operation

Both the role family and permission level determine allowed operations:

- Reader roles can't make changes.
- Contributor roles can't delete resources.
- Management roles don't grant access to Power Pages data in Dataverse.
- Data access roles don't grant permission to configure site infrastructure.

Assign an additional role only when the principal needs operations from both role families.

### A service principal's assignment doesn't work

The assignment must use the Enterprise Application object ID from Microsoft Entra ID, not the application or client ID.

### A new assignment doesn't work immediately

A new or changed assignment can take a few minutes to propagate. Wait and try the operation again before changing the assignment.

## Related content

- [Role-based access control for Power Platform](/power-platform/admin/security/role-based-access-control)
- [Tutorial: Assign roles to service principals](/power-platform/admin/programmability-tutorial-rbac-role-assignment)
- [Power Platform API reference](/rest/api/power-platform/)
- [Power Pages security](../security/power-pages-security.md)