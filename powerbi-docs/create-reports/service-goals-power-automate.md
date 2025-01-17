---
title: Use Power Automate to update goals automatically (preview)
description: Automate business flows from a scorecard.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: 'cnews'
featuredvideoid: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 11/01/2021
---
# Use Power Automate to update goals automatically (preview)

Many organizations want to use scorecards in processes that help them achieve results more quickly. However, manually monitoring scorecards can be resource intensive and error prone. In this documentation, we go over how you automate business processes when important changes happen within your scorecard. It helps organization quickly respond to changing conditions by keeping everyone up to date, and taking automated actions to improve outcomes. This new capability is easy to use: You launch Power Automate right from your scorecard and immediately construct your automated flow.   

## Get started

On the **Goals** hub page, select the scorecard you want to update, and select the **Create a flow** button in the ribbon.

:::image type="content" source="media/service-goals-create/flow-from-ribbon.png" alt-text="Access power automate by selecting the Create a flow button in the ribbon.":::

## Actions and triggers

For now, we're offering standalone actions and triggers. To get started, select **Create your own flow**, search for *Power BI* in the connector search area, and select **Power BI**.

:::image type="content" source="media/service-goals-create/PBI-connector.png" alt-text="A list of actions and triggers after selecting the PBI connector.":::
    
On the **Actions** tab, browse the list of actions.

:::image type="content" source="media/service-goals-create/goals-actions.png" alt-text="A list of the available actions in Power BI Goals.":::

On the **Triggers** tab, browse the list of triggers. 

:::image type="content" source="media/service-goals-create/goals-triggers.png" alt-text="A list of the available triggers in Power BI Goals.":::

### Actions

-	Create a goal.
-	Create a check-in.
-	Add a note to a check-in.
-	Create a scorecard.
-	Update a check-in.
-	Update a goal.
-	Get goal(s).
-	Get goal check-in(s).

### Triggers

-	When a goal changes, for example, status, owner, and so on. 
-	When someone adds or edits a check-in.
-	When an owner is assigned to a goal.
-	When a data refresh for a goal fails. 

From here, you can create and customize your flows to help automate business processes related to your scorecards. Using Power Automate with your Power BI goals helps your teams and organization respond more quickly to changing conditions, and use data to take better actions. 

 :::image type="content" source="media/service-goals-create/example-goals-flow.png" alt-text="An example of a flow you set up in Power Automate for your scorecard.":::
    
For more information on what each action and trigger does, see the documentation for each one by selecting the information icon to the right of each item, and selecting **Learn more**.

:::image type="content" source="media/service-goals-create/more-info-goals.png" alt-text="Information icon highlighted next to each action and trigger.":::

You can also see all the documentation by going to the "Create a goal" section of the [Power BI connectors](/connectors/powerbi/#create-a-goal-(preview)) article.

:::image type="content" source="media/service-goals-create/docs-for-goals.png" alt-text="A snapshot of the documentation screen for each action and trigger.":::

## Templates

Templates will allow you to choose a flow that matches your complex business scenarios, and ensure you have the building blocks to automate your process. Templates will be rolling out in the coming weeks. We'll update the documentation then. A sneak peek at just a few of the scenarios we'll be enabling:  
  
- Triggering a teams notification when a status changes to *behind* or *at risk*.  
- Sending reminders to team members at specific intervals with links to scorecards or goals to review.
- Notifying a specific team member when they're assigned to a new goal and should perform a check-in. 
- Sending a Forms survey that gets added as a check-in note on a goal at a specified interval.
- Sending a congratulations email when a team completes a goal. 

## Next steps

- For more information on creating flows, see the [Power automate](/power-automate/getting-started) documentation. 
- [Get started with goals in Power BI](service-goals-introduction.md)
