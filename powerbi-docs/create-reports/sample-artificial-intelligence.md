---
title: 'Artificial Intelligence sample for Power BI: Take a tour'
description: The Artificial Intelligence sample for Power BI is a report for a fictitious company named Contoso, created to understand their products and regions' key contributors for revenue won/loss, identify the highest or lowest breakdown of revenue, and determine if there are anomalies in their data.
author: itsnotaboutthecell
ms.author: alpowers
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: conceptual
ms.date: 02/02/2022
LocalizationGroup: Samples
---
# Artificial Intelligence sample for Power BI: Take a tour

The Artificial Intelligence sample contains a report for a fictitious company named Contoso. The Contoso sales manager created this report to understand their products and regions' key contributors for revenue won/loss, identify the highest or lowest breakdown of revenue, and determine if there are anomalies in their data. This sample is part of a series that shows how you can use Power BI with business-oriented data, reports, and dashboards.

   :::image type="content" source="media/sample-artificial-intelligence/power-bi-ai-sample-report.png" alt-text="Screenshot of opened Artificial Intelligence Sample." lightbox="media/sample-artificial-intelligence/power-bi-ai-sample-report-large.png":::

This tutorial explores the Artificial Intelligence Sample in the Power BI service. Because the report experience may be similar in Power BI Desktop and in the service, you can also follow along by downloading the sample .pbix file in Power BI Desktop.

## Prerequisites

- You just need a [Power BI free license](../consumer/end-user-features.md) to explore the samples in the Power BI service, and save them to your My workspace. 
- You can [download Power BI Desktop](../fundamentals/desktop-get-the-desktop.md) for free, too, to explore the sample .pbix file.

## Get the sample

### Get the sample from the Power BI service

1. Open the Power BI service ([app.powerbi.com](https://app.powerbi.com)) and sign in.

2. In the navigation pane, select **Learn**.
   
   :::image type="content" source="media/sample-artificial-intelligence/power-bi-learn.png" alt-text="Screenshot of Select Learn.":::

3. In the **Sample reports** section, select the **Artificial Intelligence Sample**.

   :::image type="content" source="media/sample-artificial-intelligence/power-bi-ai-sample.png" alt-text="Screenshot of Sample reports.":::
   
4. Power BI opens the **Artificial Intelligence Sample** report automatically.

### Sample location

The **Artificial Intelligence Sample** is added to your My workspace as a report and dataset.

:::image type="content" source="media/sample-artificial-intelligence/power-bi-my-workspace.png" alt-text="Screenshot of My workspace contents.":::
  
### Get the .pbix file for this sample

Alternatively, after you've saved it to My workspace, you can download the report from the service and save it as a .pbix file. Then you can open it in Power BI Desktop. 

1. Open the report in the Power BI service.
1. On the **File** menu, select **Download the .pbix file**.

    :::image type="content" source="media/sample-artificial-intelligence/download-pbix-file.png" alt-text="Screenshot of Download the dot p b i x file.":::

    It's saved to your Downloads folder, and you can open it with Power BI Desktop. 

See [Download a report from the service to Power BI Desktop](service-export-to-pbix.md) for more details.

## Explore the Artificial Intelligence sample report

The sample report has three pages, **Key Influencers**, **Decomposition Tree**, and **Anomaly Detection**, to demonstrate how people can discover new insights and inform their decision making with easy-to-use artificial intelligence visuals.

## Key Influencers page
The first report page we explore is **Key Influencers**, where we analyze our data to understand the impact and influence of key contributors on our results.

### What are our top contributors for wins and losses?

1. We start by reviewing the top contributors that resulted in a **Status** of **Won** using the **Key influencers** visual in the center of our report. From the visual, we notice the top contributor is when the **Discount goes up 2%**, we are **2.76x** more likely to win new revenue.
1. Select the **2.76x** indicator. Power BI displays a scatter chart next to it, showing the correlation between our **Discount** and **% Status is Won** for this influencer.
 
   :::image type="content" source="media/sample-artificial-intelligence/power-bi-top-contributor.png" alt-text="Screenshot of Top contributor to revenue won.":::

1. By interacting with slicers, filters, and other visuals, the Key influencers visual reruns its analysis based on the updated choice. From the **Close % by Product category** stacked bar chart, select the **Furniture** category to generate new insights based upon the updated selection. We learn that when the **Product category** is **Furniture** and when the **Sales owner** is **Molly Clark**, we are **1.50x** more likely to win new revenue.

    :::image type="content" source="media/sample-artificial-intelligence/power-bi-key-influencers-update.png" alt-text="Screenshot of Updated analysis for Key influencers.":::

1. To review the top contributors for when our **Status** changes, from the drop-down select the **Lost** option to generate new insights based upon the updated selection. We can now answer the question, **“What is the top contributor when a loss occurs?"**

    :::image type="content" source="media/sample-artificial-intelligence/power-bi-key-influencers-status-change.png" alt-text="Screenshot of Status change for Key influencers.":::

To learn more, see [Key influencers visuals](../visuals/power-bi-visualization-influencers.md).

## Decomposition Tree page
The second report page we explore is **Decomposition Tree**, where we conduct root cause and ad hoc analysis to understand the impact of **Sales Opportunities** across the different fields within our data.

### Who is the top sales owner and largest opportunity path for computer sales
1. From the **Decomposition tree** visual in the center of our report, select the **Computers** option within the **Category** breakdown to rerun the analysis.

    :::image type="content" source="media/sample-artificial-intelligence/power-bi-decomposition-selection.png" alt-text="Screenshot of Decomposition tree rerun analysis.":::

1. With our updated analysis, we can leverage *artificial intelligence splits* to determine the path to the next highest sales opportunities in our data. Select the "**+**" symbol next to **Tablets** and the **High value** option.

    :::image type="content" source="media/sample-artificial-intelligence/power-bi-decomposition-ai-split.png" alt-text="Screenshot of Decomposition tree a i split path.":::

3. The **Territory** field is determined as the next path for sales opportunity, with the **US-SOUTH** being the largest. Select the "**+**" symbol next to **US-SOUTH**, then select the **High value** option. From the updated selection, we can now answer the question, **“Who is the top sales owner?"**

    :::image type="content" source="media/sample-artificial-intelligence/power-bi-decomposition-ai-split-sales-owner.png" alt-text="Screenshot of Decomposition tree a i split path to highest value.":::

To learn more, see [Decomposition tree visuals](../visuals/power-bi-visualization-decomposition-tree.md).

## Anomaly Detection page
The final report page we explore is **Anomaly Detection**, where we combine several artificial intelligence capabilities to detect anomalies in our results, generate dynamic text summaries, and use our own natural language to ask questions and get answers from our data.

### Why the sharp decline in software revenue?
1. The clustered bar chart in the top right of the page is divided into multiple versions of itself (*small multiples*) to compare data across the **Manager** and **Product category** fields. In the **Software** multiple, select the bar for **Low, Spencer** to dynamically filter the rest of the page to Spencer's specific results.

    :::image type="content" source="media/sample-artificial-intelligence/power-bi-small-multiple.png" alt-text="Screenshot of Small multiple for Product category.":::

1. On the right side of the page, Power BI has generated a dynamic summary based on the updated selection. The text summary describes the highest and lowest calendar months for **Revenue Won**.

    :::image type="content" source="media/sample-artificial-intelligence/power-bi-smart-narrative.png" alt-text="Screenshot of Smart narrative summary.":::

1. Within the line chart in the center of the page, right-click the **December 2020** data point. Within the menu options, select **Analyze** > **Explain the decrease** to answer **"Why the sharp decline in revenue in December 2020?"** using quick insights.

    :::image type="content" source="media/sample-artificial-intelligence/power-bi-quick-insights.png" alt-text="Screenshot of Quick insights to explain the decrease.":::

To learn more, see [Smart narratives](../visuals/power-bi-visualization-smart-narrative.md) and [Apply insights to explain fluctuations in visuals](desktop-insights.md).

### Why the unexpected increase in revenue over the last 90 days?

1. In the top right of the page, select the **Last 90 days** to view **Revenue Won** displayed as individual days.

    :::image type="content" source="media/sample-artificial-intelligence/power-bi-button.png" alt-text="Screenshot of Power B I button selection.":::

1. The button has preserved the **Low, Spencer** & **Software** selections from earlier steps. It has also rewritten the **Revenue Summary** based upon the last 90 days filter, which we can review for new insights. Within the line chart are also visual **anomaly** indicators. Select the **April 25th** indicator for a possible explanation as to **"Why?"** an anomaly was detected.

    :::image type="content" source="media/sample-artificial-intelligence/power-bi-anomaly-detection.png" alt-text="Screenshot of Anomaly detection.":::

1. The **Anomalies** pane is now displayed on the right side of your report page. It includes **Possible explanations**, a **Strength score**, which means that higher scores may have had a greater impact, and possibly more explanations if we to scroll down. From our highest possible explanation score, we can answer the question, **"Why the increase in revenue?"**. When finished, collapse the Anomalies pane using the double arrows **>>** at the top of the pane.

    :::image type="content" source="media/sample-artificial-intelligence/power-bi-anomalies-pane.png" alt-text="Screenshot of Anomalies pane.":::

To learn more, see [Anomaly detection](../visuals/power-bi-visualization-anomaly-detection.md).

### Which manager had the highest close percentage and in what month?

1. In the bottom right of the page, type the question **close %** in the **Ask a question about your data** field to return a single value.

    :::image type="content" source="media/sample-artificial-intelligence/ask-a-question.png" alt-text="Screenshot of Ask a question.":::

2. To segment the **close %** results by month, modify the current question to **close % by month** to visually display the results in a clustered column chart.

   :::image type="content" source="media/sample-artificial-intelligence/ask-a-question-by-month.png" alt-text="Screenshot of Q and A segmented by month.":::

3. While columns can be great for comparing one item to another they are not as useful when displaying movement over time, update the original text to **close % by month in a line chart**.

   :::image type="content" source="media/sample-artificial-intelligence/ask-a-question-by-month-line-chart.png" alt-text="Screenshot of Q and A in a line chart.":::

4. And to answer the question of **Which manager had the highest close percentage?** update the question to **close % by month in a line chart by manager** and compare the final results.

    :::image type="content" source="media/sample-artificial-intelligence/ask-a-question-by-month-line-chart-by-manager.png" alt-text="Screenshot of Q and A by manager.":::

## Next steps: Connect to your data
This environment is a safe one to play in, because you can choose not to save your changes. If you do save them, you can always visit the **Learn** section's **Sample reports** for a new copy of this sample.

We hope this tour has shown how the artificial intelligence capabilities in Power BI can provide insights into data. Now it's your turn; connect to your own data. With Power BI, you can connect to a wide variety of data sources. To learn more, see [Get started with the Power BI service](../fundamentals/service-get-started.md).
