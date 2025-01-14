---
title: Capabilities and properties of Power BI visuals
description: This article describes the capabilities and properties of Power BI visuals.
author: mberdugo
ms.author: monaberdugo
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 02/15/2022
---

# Capabilities and properties of Power BI visuals

Every visual has a *capabilities.json file* that describes the visual to the host. The *capabilities.json* file tells the host what kind of data the visual accepts, what customizable attributes to put on the properties pane, and other information needed to create the visual. All properties in the *capabilities.json* file are **optional**.

The *capabilities.json* file has the following format:

```json
{
    "dataRoles": [ ... ],
    "dataViewMappings": [ ... ],
    "objects":  { ... },
    "supportsHighlight": true|false,
    "advancedEditModeSupport": 0|1|2,
    "sorting": { ... }
    ...
}
```

When you create a new visual, the default *capabilities.json* file includes the following root objects:

* [dataRoles](#data-roles-define-the-data-fields-that-your-visual-expects)
* [dataViewMappings](#dataviewmappings-how-you-want-the-data-mapped)
* [objects](#objects-define-property-pane-options)

The above objects are the ones needed for data-binding. They can be edited as necessary for your visual.

The following additional root objects can be added as needed:

* [tooltips](add-tooltips.md#add-tooltips-support-to-the-report-page)
* [supportsHighlight](highlight.md)
* [sorting](sort-options.md)
* [drilldown](drill-down-support.md)
* [expandCollapse](dataview-mappings.md#expanding-and-collapsing-row-headers)
* [supportsKeyboardFocus](supportskeyboardfocus-feature.md)
* [supportsSynchronizingFilterState](enable-sync-slicers.md)
* [advancedEditModeSupport](advanced-edit-mode.md)
* [supportsLandingPage](landing-page.md#creating-a-landing-page)
* [supportsEmptyDataView](landing-page.md#creating-a-landing-page)
* [supportsMultiVisualSelection](supportsmultivisualselection-feature.md)
* [subtotals](total-subtotal-api.md)

You can find all these objects and their parameters in the [*capabilities.json* schema](https://github.com/microsoft/powerbi-visuals-api/blob/master/schema.capabilities.json#L4-L65)

## data roles: define the data fields that your visual expects

To define fields that can be bound to data, you use `dataRoles`. `dataRoles` is an array of `DataViewRole` objects, which defines all the required properties. The `dataRoles` objects are the **fields** that appear on the [Properties pane](../../visuals/service-getting-started-with-color-formatting-and-axis-properties.md).

The user drags data fields into them to bind data the data fields to the objects.

### DataRole properties

DataRoles are defined by the following properties:

* **name**: The internal name of this data field (must be unique).
* **displayName**: The name displayed to the user in the **Properties** pane.
* **kind**: The kind of field:
  * `Grouping`: Set of discrete values that are used to group measure fields.
  * `Measure`: Single numeric values.
  * `GroupingOrMeasure`: Values that can be used as either a grouping or a measure.
* **description**: A short text description of the field (optional).
* **requiredTypes**: The required type of data for this data role. Values that don't match are set to null (optional).
* **preferredTypes**: The preferred type of data for this data role (optional).

#### Valid data types for requiredTypes and preferredTypes

* **bool**: A boolean value
* **integer**: An integer value
* **numeric**: A numeric value
* **text**: A text value
* **geography**: A geographic data

### dataRoles example

```json
"dataRoles": [
    {
        "displayName": "My Category Data",
        "name": "myCategory",
        "kind": "Grouping",
        "requiredTypes": [
            {
                "text": true
            },
            {
                "numeric": true
            },
            {
                "integer": true
            }
        ],
        "preferredTypes": [
            {
                "text": true
            }
        ]
    },
    {
        "displayName": "My Measure Data",
        "name": "myMeasure",
        "kind": "Measure",
        "requiredTypes": [
            {
                "integer": true
            },
            {
                "numeric": true
            }
        ],
        "preferredTypes": [
            {
                "integer": true
            }
        ]
    }
]
...
}
```

The preceding data roles would create the fields that are displayed in the following image:

![Data role fields](media/capabilities/data-role-display.png)

## dataViewMappings: how you want the data mapped

The `dataViewMappings` objects describe how the data roles relate to each other and  allow you to specify conditional requirements for the displaying data views.

Most visuals provide a single mapping, but you can provide multiple dataViewMappings. Each valid mapping produces a data view.

```json
"dataViewMappings": [
    {
        "conditions": [ ... ],
        "categorical": { ... },
        "table": { ... },
        "single": { ... },
        "matrix": { ... }
    }
]
```

For more information, see [Understand data view mapping in Power BI visuals](dataview-mappings.md).

## objects: define property pane options

Objects describe customizable properties that are associated with the visual. The objects defined in this section are the objects that appear in the [Format pane](../../create-reports/service-the-report-editor-take-a-tour.md#format-your-visuals). Each object can have multiple properties, and each property has a type that's associated with it.

```json
"objects": {
    "myCustomObject": {
        "displayName": "My Object Name",
        "properties": { ... }
    }
}
```

For more information, see [Objects and properties of Power BI visuals](objects-properties.md).

## Next steps

> [!div class="nextstepaction"]
> [Understand data view mapping in Power BI visuals](dataview-mappings.md)

> [!div class="nextstepaction"]
> [Objects and properties of Power BI visuals](objects-properties.md)

> [!div class="nextstepaction"]
> [Advanced edit mode in Power BI visuals](advanced-edit-mode.md)

> [!div class="nextstepaction"]
> [Sorting options for Power BI visuals](sort-options.md)
