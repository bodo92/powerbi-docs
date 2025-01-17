---
title: Interacting with an ArcGIS map that has been shared with you
description: 'Using ArcGis map in reading view as a Power BI report consumer'
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/18/2022
ms.author: mihart

---
# Interacting with an ArcGIS map in Power BI
This topic is written from the point of view of a person *consuming* an ArcGIS map in the Power BI service, Desktop, or mobile. Once a creator shares an ArcGIS map with you, there are many ways to interact with that map.  To learn more about creating an ArcGIS map, see [ArcGIS map by Esri tutorial](../visuals/power-bi-visualizations-arcgis.md).

The combination of ArcGIS maps and Power BI takes mapping beyond the presentation of points on a map to a whole new level. The available options for base maps, location types, themes, symbol styles, and reference layers creates gorgeous informative map visualizations. The combination of authoritative data layers (such as census data) on a map with spatial analysis conveys a deeper understanding of the data in your visualization.

> [!TIP]
> GIS stands for Geographic Information System.
> 

The example we're using looks at last year's sales by city and uses a street basemap, bubble symbols to represent size, and a reference layer for average household income. The map contains three pins and one drive time radius (in purple).

![Screenshot of street basemap.](media/end-user-arcgis/power-bi-arcgis-esri.png)

> [!TIP]
> Visit [Esri's page on Power BI](https://www.esri.com/powerbi) to see many examples and read testimonials. And then see esri's [ArcGIS Map for Power BI Getting Started page](https://doc.arcgis.com/en/maps-for-powerbi/get-started/about-maps-for-power-bi.htm).
> 
> 

<br/>

## User consent
The first time a colleague shares an ArcGIS map with you, Power BI will display a prompt. ArcGIS Maps for Power BI is provided by Esri (www.esri.com) and your use of ArcGIS Maps for Power BI is subject by Esri's terms and privacy policy. Power BI users wishing to use the ArcGIS Maps for Power BI visuals need to accept the consent dialog.

## Selection tools
ArcGIS Maps for Power BI allows three selection modes. A maximum of 250 data points can be selected at a time.

![All three selection tools.](media/end-user-arcgis/power-bi-esri-selection-tools.png)

![Selection tool for individual data points.](media/end-user-arcgis/power-bi-esri-selection-single.png) Select individual data points.

![Selection tool for drawing a rectangle.](media/end-user-arcgis/power-bi-esri-selection-marquee.png) Draws a rectangle on the map and selects the contained data points. Use CTRL to select more than one rectangular area.

![Selection tool for boundaries or polygons.](media/end-user-arcgis/power-bi-esri-selection-reference-layer-2.png) Allows boundaries or polygons within reference layers to be used to select contained data points.

<br/>

## Interacting with an ArcGIS map
The features available to you depend on whether you are the *creator* (person who made the map) or the *consumer* (someone shared an ArcGIS map with you). If you are interacting with an ArcGIS map as a consumer (also known as [Reading view](../consumer/end-user-reading-view.md)), here are the actions available to you.

* If you are a Premium consumer with *view* permissions, you'll be able to [view the data used to create the visualization](../consumer/end-user-show-data.md) , [subscribe](../consumer/end-user-subscribe.md), see the map in [focus mode and full screen mode](../consumer/end-user-focus.md), [view related content](../consumer/end-user-related.md), [interact with the filters](../consumer/end-user-report-filter.md) set by the *report creator*, [share the report](/power-bi/collaborate-share/service-share-reports), and more.

* As with other visualization types, Power BI **Pro** consumers can do everything the Premium consumer can do, plus [export the underlying data](../visuals/power-bi-visualization-export-data.md), [get usage metrics](/power-bi/collaborate-share/service-usage-metrics), save a copy and [publish to Web](/power-bi/collaborate-share/service-publish-to-web), and more.

    
* Expand the **Filters** pane to explore the map using filters.   
    ![Filters pane with the word Filters selected](media/end-user-arcgis/power-bi-filter.png)  
* If the map has a reference layer, select locations to display details in a tooltip. Here we've selected Adams County and see data from the average household income reference layer the creator added to the map.
  
    ![Location selected for Adams County.](media/end-user-arcgis/power-bi-reference-layer.png)  
  
    In this case, we also get a chart. Select a bar on the chart to dig into the data. Here we see that 79 households in Adams county earn $200,000 or greater.
  
    ![Last bar selected. ](media/end-user-arcgis/power-bi-tooltip-chart.png)
  
    Select the arrow to display any additional charts.
* Hover over basemap location symbols to display details in a tooltip.     
  ![Details displayed for North Canton, OH.](media/end-user-arcgis/power-bi-arcgis-hover.png)
  
  > [!TIP]
  > You may have to zoom in to select a specific location.  Otherwise, if there are overlapping locations, Power BI will present you with more than one tooltip at a time. Select the arrows to move between the tooltips
  > 
  > ![Tooltip showing page one of three.](media/end-user-arcgis/power-bi-3-screens.png)
  > 
  > 
* If the creator has added an Infographics layer to the ArcGIS map, you'll see additional data displayed in the upper-right corner of the map.  For example, here the map creator added "Children under 14."
  
    ![Infographics card displayed.](media/end-user-arcgis/power-bi-demographics.png)

## Considerations and Limitations
ArcGIS Maps for Power BI is available in the following services and applications:

<table>
<tr><th>Service/App</th><th>Availability</th></tr>
<tr>
<td>Power BI Desktop</td>
<td>Yes</td>
</tr>
<tr>
<td>Power BI service (app.powerbi.com)</td>
<td>Yes</td>
</tr>
<tr>
<td>Power BI mobile applications</td>
<td>Yes</td>
</tr>
<tr>
<td>Power BI publish to web</td>
<td>No</td>
</tr>
<tr>
<td>Power BI Embedded</td>
<td>No</td>
</tr>
<tr>
<td>Power BI service embedding (PowerBI.com)</td>
<td>No</td>
</tr>
</table>

**How do ArcGIS Maps for Power BI work together?**
ArcGIS Map for Power BI is provided by Esri (www.esri.com). Your use of ArcGIS Map for Power BI is subject by Esri's [terms](https://go.microsoft.com/fwlink/?LinkID=8263222) and [privacy policy](https://go.microsoft.com/fwlink/?LinkID=826323). Power BI users wishing to use the ArcGIS Map for Power BI visuals need to accept the consent dialog (see User Consent for details).  Using Esri’s ArcGIS Map for Power BI is subject to Esri’s Terms and Privacy Policy, which are also linked to from the consent dialog. Each user must consent prior to using ArcGIS Map for Power BI for the first time. Once the user accepts the consent, data bound to the visual is sent to Esri’s services at least for geocoding, meaning transforming location information into latitude and longitude information that can be represented in a map. You should assume any data bound to the data visualization can be sent to Esri’s services. Esri provides services like base maps, spatial analytics, geocoding, etc. The ArcGIS Map for Power BI visual interacts with these services using an SSL connection protected by a certificate provided and maintained by Esri. Additional information about ArcGIS Map for Power BI can be obtained from Esri’s [ArcGIS Map for Power BI product page](https://www.esri.com/powerbi).

**Power BI Plus**    
![Select the Plus icon to sign up or sign in](media/end-user-arcgis/power-bi-plus.png)

When a user signs up for a Plus subscription offered by Esri through ArcGIS Map for Power BI, they are entering into an direct relationship with Esri. Power BI does not send personal information about the user to Esri. The user signs in to and trusts an Esri provided active directory application using their own active directory identity. By doing so, the user is sharing their personal information directly with Esri. Once the user adds Plus content to an ArcGIS Map for Power BI visual, other Power BI users also need a Plus subscription from Esri to view or edit that content. 

For technical detailed questions about how Esri’s ArcGIS Map for Power BI works, reach out to Esri through their support site.

**The ArcGIS map is not showing up**    
In services or applications where ArcGIS Map for Power BI is not available, the visualization will show as an empty visual with the Power BI logo.

**I'm not seeing all of my information on the map**    
When geocoding latitude/longitude on the map, up to 30,000 data points are displayed. When geocoding data points such as zip codes or street addresses, only the first 15,000 data points are geocoded. Geocoding place names or countries is not subject to the 15,000 address limit.

**Is there any charge for using ArcGIS Map for Power BI?**

The ArcGIS Map for Power BI is available to all Power BI users at no additional cost. It is a component provided by **Esri** and your use is subject to the terms and privacy policy provided by **Esri** as noted earlier in this article. If you subscribe to ArcGIS **Plus**, there is a charge.

**I'm getting an error message about my cache being full**

This is a bug that is being addressed.  In the meantime, select the link that appears in the error message for instructions on clearing your Power BI cache.

**Can I view my ArcGIS maps offline?**

No, Power BI needs network connectivity to display the maps.

## Next steps
Getting help: **Esri** provides [comprehensive documentation](https://go.microsoft.com/fwlink/?LinkID=828772) on the feature set of **ArcGIS Map for Power BI**.

You can ask questions, find the latest information, report issues, and find answers on the Power BI [community thread related to **ArcGIS Map for Power BI**](https://go.microsoft.com/fwlink/?LinkID=828771).


[ArcGIS Map for Power BI product page](https://www.esri.com/powerbi)