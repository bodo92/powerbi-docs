---
title: About tenant settings
description: Learn how to enable and disable Power BI tenant settings.
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.custom: tenant-setting
ms.topic: how-to
ms.date: 03/17/2022
LocalizationGroup: Administration
---

# About tenant settings

**Tenant settings** enable fine-grained control over the features that are made available to your organization. If you have concerns around sensitive data, some of our features may not be right for your organization, or you may only want a particular feature to be available to a specific group.

> [!NOTE]
> Tenant settings that control the availability of features in the Power BI user interface can help to establish governance policies, but they're not a security measure. For example, the **Export data** setting doesn't restrict the permissions of a Power BI user on a dataset. Power BI users with read access to a dataset have the permission to query this dataset and might be able to persist the results without using the **Export data** feature in the Power BI user interface.

> [!NOTE]
> It can take up to 15 minutes for a setting change to take effect for everyone in your organization.

## How to get to the tenant settings

Go to the Admin portal and select Tenant settings.

:::image type="content" source="media/service-admin-portal-about-tenant-settings/admin-portal-tenant-settings.png" alt-text="Screenshot of how to get to the tenant settings":::

## How to use the tenant settings

Many of the settings can have one of three states:

* **Disabled for the entire organization**: No one in your organization can use this feature.

    ![Disabled all setting](media/service-admin-portal-about-tenant-settings/powerbi-admin-tenant-settings-disabled.png)

* **Enabled for the entire organization**: Everyone in your organization can use this feature.

    ![Enabled all setting](media/service-admin-portal-about-tenant-settings/powerbi-admin-tenant-settings-enabled.png)

* **Enabled for a subset of the organization**: Specific security groups in your organization are allowed to use this feature.

    You can also enable a feature for your entire organization, **Except specific security groups**.

    ![Enabled subset setting](media/service-admin-portal-about-tenant-settings/powerbi-admin-tenant-settings-enabled-except.png)

    You can also combine settings to enable the feature only for a specific group of users and also disable it for a group of users. Using this approach ensures that certain users don't have access to the feature even if they're in the allowed group. The most restrictive setting for a user applies.

    ![Enable except setting](media/service-admin-portal-about-tenant-settings/powerbi-admin-tenant-settings-enabled-except2.png)

## Tenant setting sections

The sections of the tenant settings page are listed in the table below.

* [Admin API settings](service-admin-portal-admin-api-settings.md)
* [Advanced networking settings](service-admin-portal-advanced-networking.md)
* [Audit and usage settings](service-admin-portal-audit-usage.md)
* [Content pack and app settings](service-admin-portal-content-pack-app.md)
* [Dashboard settings](service-admin-portal-dashboard.md)
* [Dataflow settings](service-admin-portal-dataflow.md)
* [Dataset Security settings](service-admin-portal-dataset-security.md)
* [Developer settings](service-admin-portal-developer.md)
* [Discovery settings](service-admin-portal-discovery.md)
* [Export and sharing settings](service-admin-portal-export-sharing.md)
* [Goals settings (preview)](service-admin-portal-goals-settings.md)
* [Help and support settings](service-admin-portal-help-support.md)
* [Information protection settings](service-admin-portal-information-protection.md)
* [Workspace settings](service-admin-portal-workspace.md)
* [Information protection settings](service-admin-portal-information-protection.md)
* [Insights settings](service-admin-portal-insights.md)
* [Integration settings](service-admin-portal-integration.md)
* [Power BI visuals settings](service-admin-portal-power-bi-visuals.md)
* [Q&A settings](service-admin-portal-qa.md)
* [R and Python visuals settings](service-admin-portal-r-python-visuals.md)
* [Share data with your Microsoft 365 services settings](service-admin-portal-share-data-microsoft-365-services.md)
* [Template app settings](service-admin-portal-template-app.md)
* [User experience experiments settings](service-admin-portal-user-experience-experiments.md)

## Next steps

* [About the Admin portal](service-admin-portal.md)