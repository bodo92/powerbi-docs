---
title: Pause and start your Power BI Embedded capacity in the Azure portal
description: This article walks through how to pause and start a Power BI Embedded capacity in Microsoft Azure.
author: mberdugo
ms.author: monaberdugo
services: power-bi-embedded
editor: ''
tags: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.date: 11/25/2021
---

# Pause and start your Power BI Embedded capacity in the Azure portal

This article walks through how to pause and start a Power BI Embedded capacity in Microsoft Azure. This assumes you have created a Power BI Embedded capacity. If you have not, see [Create Power BI Embedded capacity in the Azure portal](azure-pbie-create-capacity.md) to get started.

If you don't have an Azure subscription, create a [free account](https://azure.microsoft.com/free/) before you begin.

## Pause your capacity

Pausing your capacity prevents you from being billed. Pausing your capacity is great if you don't need to use the capacity for a period of time. Use the following steps to pause your capacity.

> [!NOTE]
> Pausing a capacity may prevent content from being available within Power BI. Make sure to unassign workspaces from your capacity before pausing to prevent interruption.

1. Sign into the [Azure portal](https://portal.azure.com/).

2. Select **All services** > **Power BI Embedded** to see your capacities.

    :::image type="content" source="media/azure-pbie-pause-start/azure-portal-more-services.png" alt-text="Screenshot of all services in Azure portal.":::

3. Select the capacity you want to pause.

    :::image type="content" source="media/azure-pbie-pause-start/azure-portal-capacity-list-active.png" alt-text="Screenshot of Power BI Embedded capacity list. ":::

4. Select **Pause** above the capacity details.

    :::image type="content" source="media/azure-pbie-pause-start/azure-portal-pause-capacity.png" alt-text="Screenshot of pausing a capacity.":::

5. Select **Yes** to confirm you want to pause the capacity.

    :::image type="content" source="media/azure-pbie-pause-start/azure-portal-confirm-pause.png" alt-text="Screenshot of confirming capacity pause.":::

## Start your capacity

Resume usage by starting your capacity. Starting your capacity also resumes billing.

1. Sign into the [Azure portal](https://portal.azure.com/).

2. Select **All services** > **Power BI Embedded** to see your capacities.

    :::image type="content" source="media/azure-pbie-pause-start/azure-portal-more-services.png" alt-text="Screenshot of all services within Azure portal.":::

3. Select the capacity you want to start.

    :::image type="content" source="media/azure-pbie-pause-start/azure-portal-capacity-list.png" alt-text="Screenshot of Power BI Embedded capacity list in Azure portal.":::

4. Select **Start** above the capacity details.

    :::image type="content" source="media/azure-pbie-pause-start/azure-portal-start-capacity.png" alt-text="Screenshot of starting a capacity.":::

5. Select **Yes** to confirm you want to start the capacity.

    :::image type="content" source="media/azure-pbie-pause-start/azure-portal-confirm-start.png" alt-text="Screenshot of confirming start.":::

If any content is assigned to this capacity, it becomes available once started.

## Use CLI to start or pause your capacity

You can also start or pause your capacity from the command line using:

* [ARM API references](/rest/api/power-bi-embedded/capacities)
* [PS references](/powershell/module/az.powerbiembedded)
  * [Suspend](/powershell/module/az.powerbiembedded/suspend-azpowerbiembeddedcapacity)
  * [Resume](/powershell/module/az.powerbiembedded/resume-azpowerbiembeddedcapacity)

## Next steps

>[!div class="nextstepaction"]
>[Scale your Power BI Embedded capacity](azure-pbie-scale-capacity.md).

>[!div class="nextstepaction"]
>[How to embed your Power BI dashboards, reports and tiles](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding-content/).

More questions? [Try asking the Power BI Community](https://community.powerbi.com/)
