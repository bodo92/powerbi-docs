---
title: Model relationships in Power BI Desktop
description: Introduce theory about model relationships in Power BI Desktop
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: pbi-transform-model
ms.topic: conceptual
ms.date: 03/23/2021
---

# Model relationships in Power BI Desktop

This article targets Import data modelers working with Power BI Desktop. It's an important model design topic that's essential to delivering intuitive, accurate, and optimal models.

For a deeper discussion on optimal model design, including table roles and relationships, see the [Understand star schema and the importance for Power BI](../guidance/star-schema.md) article.

## Relationship purpose

Put simply, Power BI relationships propagate filters applied on the columns of model tables to other model tables. Filters will propagate so long as there's a relationship path to follow, which can involve propagation to multiple tables.

Relationship paths are deterministic, meaning that filters are always propagated in the same way and without random variation. Relationships can, however, be disabled, or have filter context modified by model calculations that use particular DAX functions. For more information, see the [Relevant DAX functions](#relevant-dax-functions) topic later in this article.

> [!IMPORTANT]
> It's important to understand that model relationships do not enforce data integrity. For more information, see the [Relationship evaluation](#relationship-evaluation) topic later in this article. This topics explains how model relationships behave when there are data integrity issues with your data.

Let's see how relationships propagate filters with an animated example.

:::image type="content" source="media/desktop-relationships-understand/animation-filter-propagation.gif" alt-text="Animated example of relationship filter propagation.":::

In this example, the model consists of four tables: **Category**, **Product**, **Year**, and **Sales**. The **Category** table relates to the **Product** table, and the **Product** table relates to the **Sales** table. The **Year** table also relates to the **Sales** table. All relationships are one-to-many (the details of which are described later in this article).

A query—possibly generated by a Power BI card visual—requests the total sales quantity for sales orders made for a single category, **Cat-A**, and for a single year, **CY2018**. It's why you can see filters applied on the **Category** and **Year** tables. The filter on the **Category** table propagates to the **Product** table to isolate two products that are assigned to the category **Cat-A**. Then the **Product** table filters propagate to the **Sales** table to isolate just two sales rows for these products. These two sales rows represent the sales of products assigned to category **Cat-A**. Their combined quantity is 14 units. At the same time, the **Year** table filter propagates to further filter the **Sales** table, resulting in just the one sales row that is for products assigned to category **Cat-A** and that was ordered in year **CY2018**. The quantity value returned by the query is 11 units. Note that when multiple filters are applied to a table (like the **Sales** table in this example), it's always an AND operation, requiring that all conditions must be true.

### Disconnected tables

It's unusual that a model table isn't related to another model table. Such a table in a valid model design can be described as a _disconnected table_. A disconnected table isn't intended to propagate filters to other model tables. Instead, it's used to accept "user input" (perhaps with a slicer visual), allowing model calculations to use the input value in a meaningful way. For example, consider a disconnected table that is loaded with a range of currency exchange rate values. As long as a filter is applied to filter by a single rate value, the value can be used by a measure expression to convert sales values.

The Power BI Desktop what-if parameter is a feature that creates a disconnected table. For more information, see the [Create and use a What if parameter to visualize variables in Power BI Desktop](desktop-what-if.md) article.

## Relationship properties

A model relationship relates one column in a table to one column in a different table. (There's one specialized case where this requirement isn't true, and it applies only to multi-column relationships in DirectQuery models. For more information, see the [COMBINEVALUES](/dax/combinevalues-function-dax) DAX function article.)

> [!NOTE]
> It's not possible to relate a column to a different column _in the same table_. This is sometimes confused with the ability to define a relational database foreign key constraint that is table self-referencing. This relational database concept can be used to store parent-child relationships (for example, each employee record is related to a "reports to" employee). Generating a model hierarchy based on this type of relationship can't be solved by creating model relationships. To achieve this, see the [Parent and Child functions](/dax/parent-and-child-functions-dax) article.

### Cardinality

Each model relationship must be defined with a cardinality type. There are four cardinality type options, representing the data characteristics of the "from" and "to" related columns. The "one" side means the column contains unique values; the "many" side means the column can contain duplicate values.

> [!NOTE]
> If a data refresh operation attempts to load duplicate values into a "one" side column, the entire data refresh will fail.

The four options—together with their shorthand notations—are described in the following bulleted list:

- One-to-many (1:\*)
- Many-to-one (\*:1)
- One-to-one (1:1)
- Many-to-many (\*:\*)

When you create a relationship in Power BI Desktop, the designer will automatically detect and set the cardinality type. The designer queries the model to know which columns contain unique values. For Import models, it uses internal storage statistics; for DirectQuery models it sends profiling queries to the data source. Sometimes, however, it can get it wrong. It happens because tables are yet to be loaded with data, or because columns that you expect to contain duplicate values currently contain unique values. In either case, you can update the cardinality type as long as any "one" side columns contain unique values (or the table is yet to be loaded with rows of data).

The **One-to-many** and **Many-to-one** cardinality options are essentially the same, and they're also the most common cardinality types.

When configuring a One-to-many or Many-to-one relationship, you'll choose the one that matches the order in which you related the columns. Consider how you would configure the relationship from the **Product** table to the **Sales** table by using the **ProductID** column found in each table. The cardinality type would be _One-to-many_, as the **ProductID** column in the **Product** table contains unique values. If you related the tables in the reverse direction, **Sales** to **Product**, then the cardinality would be _Many-to-one_.

A **One-to-one** relationship means both columns contain unique values. This cardinality type isn't common, and it likely represents a suboptimal model design because of the storage of redundant data. For more information on using this cardinality type, see [One-to-one relationship guidance](../guidance/relationships-one-to-one.md).

A **Many-to-many** relationship means both columns can contain duplicate values. This cardinality type is infrequently used. It's typically useful when designing complex model requirements. For guidance on using this cardinality type, see [Many-to-many relationship guidance](../guidance/relationships-many-to-many.md).

> [!NOTE]
> The Many-to-many cardinality type isn't currently supported for models developed for Power BI Report Server.

> [!TIP]
> In Power BI Desktop model view, you can interpret a relationship's cardinality type by looking at the indicators (1 or \*) on either side of the relationship line. To determine which columns are related, you'll need to select—or hover the cursor over—the relationship line to highlight the columns.

### Cross filter direction

Each model relationship must be defined with a cross filter direction. Your selection determines the direction(s) that filters will propagate. The possible cross filter options are dependent on the cardinality type.

| Cardinality type | Cross filter options |
| --- | --- |
| One-to-many (or Many-to-one) | Single<br>Both |
| One-to-one | Both |
| Many-to-many | Single (Table1 to Table2)<br>Single (Table2 to Table1)<br>Both |

_Single_ cross filter direction means "single direction", and _Both_ means "both directions". A relationship that filters in both directions is commonly described as _bi-directional_.

For One-to-many relationships, the cross filter direction is always from the "one" side, and optionally from the "many" side (bi-directional). For One-to-one relationships, the cross filter direction is always from both tables. Lastly, for the Many-to-many relationships, cross filter direction can be from either one of the tables, or from both tables. Notice that when the cardinality type includes a "one" side, that filters will always propagate from that side.

When the cross filter direction is set to **Both**, an additional property is available. It can apply bi-directional filtering when row-level security (RLS) rules are enforced. For more information about RLS, see the [Row-level security (RLS) with Power BI Desktop](../create-reports/desktop-rls.md) article.

Modifying the relationship cross filter direction—including the disabling of filter propagation—can also be done by a model calculation. It's achieved by using the [CROSSFILTER](/dax/crossfilter-function) DAX function.

Bi-directional relationships can impact negatively on performance. Further, attempting to configure a bi-directional relationship could result in ambiguous filter propagation paths. In this case, Power BI Desktop may fail to commit the relationship change and will alert you with an error message. Sometimes, however, Power BI Desktop may allow you to define ambiguous relationship paths between tables. Precedence rules that affect ambiguity detection and path resolution are described later in this article in the [Precedence rules](#precedence-rules) topic.

We recommend using bi-directional filtering only as needed. For more information, see [Bi-directional relationship guidance](../guidance/relationships-bidirectional-filtering.md).

> [!TIP]
> In Power BI Desktop model view, you can interpret a relationship's cross filter direction by noticing the arrowhead(s) along the relationship line. A single arrowhead represents a single-direction filter in the direction of the arrowhead; a double arrowhead represents a bi-directional relationship.

### Make this relationship active

There can only be one active filter propagation path between two model tables. However, it's possible to introduce additional relationship paths, though these relationships must all be configured as _inactive_. Inactive relationships can only be made active during the evaluation of a model calculation. It is achieved by using the [USERELATIONSHIP](/dax/userelationship-function-dax) DAX function.

For more information, see [Active vs inactive relationship guidance](../guidance/relationships-active-inactive.md).

> [!TIP]
> In Power BI Desktop model view, you can interpret a relationship's active vs inactive status. An active relationship is represented by a solid line; an inactive relationship is represented as a dashed line.

### Assume referential integrity

The _Assume referential integrity_ property is available only for One-to-many and One-to-one relationships between two DirectQuery storage mode tables that are based on the same data source. When enabled, native queries sent to the data source will join the two tables together by using an INNER JOIN rather than an OUTER JOIN. Generally, enabling this property improves query performance, though it does depend on the specifics of the data source.

Always enable this property when a database foreign key constraint exists between the two tables. When a foreign key constraint doesn't exist, you can still enable the property as long as you're certain data integrity exists.

> [!IMPORTANT]
> If data integrity should become compromised, the inner join will eliminate unmatched rows between the tables. For example, consider a model **Sales** table with a **ProductID** column value that did not exist in the related **Product** table. Filter propagation from the **Product** table to the **Sales** table will eliminate sales rows for unknown products. This would result in an understatement of the sales results.
>
> For more information, see the [Assume referential integrity settings in Power BI Desktop](../connect-data/desktop-assume-referential-integrity.md) article.

## Relevant DAX functions

There are several DAX functions that are relevant to model relationships. Each function is described briefly in the following bulleted list:

- [RELATED](/dax/related-function-dax): Retrieves the value from "one" side.
- [RELATEDTABLE](/dax/relatedtable-function-dax): Retrieve a table of rows from "many" side.
- [USERELATIONSHIP](/dax/userelationship-function-dax): Forces the use of a specific inactive model relationship.
- [CROSSFILTER](/dax/crossfilter-function): Modifies the relationship cross filter direction (to one or both), or it disables filter propagation (none).
- [COMBINEVALUES](/dax/combinevalues-function-dax): Joins two or more text strings into one text string. The purpose of this function is to support multi-column relationships in DirectQuery models.
- [TREATAS](/dax/treatas-function): Applies the result of a table expression as filters to columns from an unrelated table.
- [Parent and Child functions](/dax/parent-and-child-functions-dax): A family of related functions that can be used to generate calculated columns to naturalize a parent-child hierarchy. These columns can then be used to create a fixed-level hierarchy.

## Relationship evaluation

Model relationships, from an evaluation perspective, are classified as either _regular_ or _limited_. It's not a configurable relationship property. It is in fact inferred from the cardinality type and the data source of the two related tables. It's important to understand the evaluation type because there may be performance implications or consequences should data integrity be compromised. These implications and integrity consequences are described in this topic.

First, some modeling theory is required to fully understand relationship evaluations.

An Import or DirectQuery model sources all of its data from either the Vertipaq cache or the source database. In both instances, Power BI is able to determine that a "one" side of a relationship exists.

A Composite model, however, can comprise tables using different storage modes (Import, DirectQuery or Dual), or multiple DirectQuery sources. Each source, including the Vertipaq cache of Import data, is considered to be a _source group_. Model relationships can then be classified as _intra source group_ or _inter / cross source group_. An intra source group relationship is one that relates two tables within a source group, while a inter / cross source group relationship relates tables from different source group. Note that relationships in Import or DirectQuery models are always intra source group.

Let's see an example of a Composite model.

:::image type="content" source="media/desktop-relationships-understand/source-group-example.png" alt-text="Example of a Composite model consisting of two source groups.":::

In this example, the Composite model consists of two source groups: a Vertipaq source group and a DirectQuery source group. The Vertipaq source group contains three tables, and the DirectQuery source group contains two tables. One cross source group relationship exists to relate a table in the Vertipaq source group to a table in the DirectQuery source group.

### Regular relationships

A model relationship is _regular_ when the query engine can determine the "one" side of relationship. It has confirmation that the "one" side column contains unique values. All One-to-many intra source group relationships are regular relationships.

In the following example, there are two regular relationships, both marked as **R**. Relationships include the One-to-many relationship contained within the Vertipaq source group, and the One-to-many relationship contained within the DirectQuery source.

:::image type="content" source="media/desktop-relationships-understand/source-group-example-regular.png" alt-text="Example of a Composite model consisting of two source groups with regular relationships marked.":::

For Import models, where all data is stored in the Vertipaq cache, a data structure is created for each regular relationship at data refresh time. The data structures consist of indexed mappings of all column-to-column values, and their purpose is to accelerate joining tables at query time.

At query time, regular relationships permit _table expansion_ to take place. Table expansion results in the creation of a virtual table by including the native columns of the base table and then expanding into related tables. For Import tables, it's done in the query engine; for DirectQuery tables it is done in the native query sent to the source database (as long as the **Assume referential integrity** property isn't enabled). The query engine then acts upon the expanded table, applying filters and grouping by the values in the expanded table columns.

> [!NOTE]
> Inactive relationships are expanded also, even when the relationship isn't used by a calculation. Bi-directional relationships have no impact on table expansion.

For One-to-many relationships, table expansion takes place from the "many" to the "one" sides by using LEFT OUTER JOIN semantics. When a matching value from the "many" to the "one" side doesn't exist, a blank virtual row is added to the "one" side table.

Table expansion also occurs for One-to-one intra source group relationships, but by using FULL OUTER JOIN semantics. It ensures that blank virtual rows are added on either side, when necessary.

The blank virtual rows are effectively _Unknown Members_. Unknown members represent referential integrity violations where the "many" side value has no corresponding "one" side value. Ideally these blanks should not exist, and they can be eliminated by cleansing or repairing the source data.

Let's see how table expansion works with an animated example.

:::image type="content" source="media/desktop-relationships-understand/animation-expanded-table.gif" alt-text="Animated example of table expansion.":::

In this example, the model consists of three tables: **Category**, **Product**, and **Sales**. The **Category** table relates to the **Product** table with a One-to-many relationship, and the **Product** table relates to the **Sales** table with a One-to-many relationship. The **Category** table contains two rows, the **Product** table contains three rows, and the **Sales** tables contains five rows. There are matching values on both sides of all relationships meaning that there are no referential integrity violations. A query-time expanded table is revealed. The table consists of the columns from all three tables. It's effectively a denormalized perspective of the data contained in the three tables. A new row is added to the **Sales** table, and it has a production identifier value (9) that has no matching value in the **Product** table. It's a referential integrity violation. In the expanded table, the new row has (Blank) values for the **Category** and **Product** table columns.

### Limited relationships

A model relationship is _limited_ when there's no guaranteed "one" side. It can be the case for two reasons:

- The relationship uses a Many-to-many cardinality type (even if one or both columns contain unique values)
- The relationship is cross source group (which can only ever be the case for Composite models)

In the following example, there are two limited relationships, both marked as **L**. The two relationships include the Many-to-many relationship contained within the Vertipaq source group, and the One-to-many cross source group relationship.

:::image type="content" source="media/desktop-relationships-understand/source-group-example-limited.png" alt-text="Example of a Composite model consisting of two source groups with limited relationships marked.":::

For Import models, data structures are never created for limited relationships. This means table joins must be resolved at query time.

Table expansion never occurs for limited relationships. Table joins are achieved by using INNER JOIN semantics, and for this reason, blank virtual rows are not added to compensate for referential integrity violations.

There are additional restrictions related to limited relationships:

- The RELATED DAX function can't be used to retrieve the "one" side column values
- Enforcing RLS has topology restrictions

> [!NOTE]
> In Power BI Desktop model view, it's not always possible to determine whether a model relationship is regular or limited. A Many-to-many relationship will always be limited, as is a One-to-many relationship when it's a cross source group relationship. To determine whether it's a cross source group relationship, you'll need to inspect the table storage modes and data sources to arrive at the correct determination.

### Precedence rules

Bi-directional relationships can introduce multiple—and therefore ambiguous—filter propagation paths between model tables. The following list presents precedence rules that Power BI uses for ambiguity detection and path resolution:

1. Many-to-one and One-to-one relationships, including limited relationships
2. Many-to-many relationships
3. Bi-directional relationships, in the reverse direction (that is, from the "Many" side)

### Performance preference

The following list orders filter propagation performance, from fastest to slowest performance:

1. One-to-many intra source group relationships
2. Many-to-many model relationships achieved with an intermediary table and that involves at least one bi-directional relationship
3. Many-to-many cardinality relationships
4. Cross source group relationships

## Next steps

For more information about this article, check out the following resources:

- [Understand star schema and the importance for Power BI](../guidance/star-schema.md)
- [One-to-one relationship guidance](../guidance/relationships-one-to-one.md)
- [Many-to-many relationship guidance](../guidance/relationships-many-to-many.md)
- [Active vs inactive relationship guidance](../guidance/relationships-active-inactive.md)
- [Bi-directional relationship guidance](../guidance/relationships-bidirectional-filtering.md)
- [Relationship troubleshooting guidance](../guidance/relationships-troubleshoot.md)
- Video: [The Do's and Don'ts of Power BI Relationships](https://www.youtube.com/watch?v=78d6mwR8GtA)
- Questions? [Try asking the Power BI Community](https://community.powerbi.com/)
- Suggestions? [Contribute ideas to improve Power BI](https://ideas.powerbi.com/)
