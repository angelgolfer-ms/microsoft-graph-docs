---
title: "itemInsights resource type"
description: "Insights are relationships calculated using advanced analytics and machine learning techniques. You can, for example, identify OneDrive for Business documents trending around users."
author: "simonhult"
localization_priority: Priority
ms.prod: "insights"
doc_type: resourcePageType
---

# itemInsights resource type

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

[!INCLUDE [itemInsightsdisclaimer](../../includes/itemInsightsdisclaimer.md)]

Insights are relationships calculated using advanced analytics and machine learning techniques. You can, for example, identify OneDrive for Business documents trending around users.

Insights are returned by the following APIs:

- [Trending](insights-trending.md) - returns documents from OneDrive for Business and from SharePoint sites trending around a user.
- [Used](insights-used.md) - returns documents viewed and modified by a user. Includes documents the user used in OneDrive for Business, and SharePoint.
- [Shared](insights-shared.md) - returns documents shared with a user. Documents can be shared as email attachments or as OneDrive for Business links sent in emails.

Each insight is returned with a `resourceVisualization` and `resourceReference` complex value type (CVT). The resourceVisualization CVT contains properties such as `title` and `previewImageUrl`. Microsoft uses the visualization properties to render the files in experiences like Office Delve.

## Relationships

| Relationship      | Type          | Description  |
| ------------- |---------------| -------------|
| trending    	| [trending](insights-trending.md) collection		| Calculated relationship identifying documents trending around a user. Trending documents are calculated based on activity of the user's closest network of people and include files stored in OneDrive for Business and SharePoint. Trending insights help the user to discover potentially useful content that the user has access to, but has never viewed before.|
| used    	| [usedInsight](insights-used.md) collection		| Calculated relationship identifying the latest documents viewed and modified by a user, including OneDrive for Business and SharePoint documents, ranked by recency of use.|
| shared    	| [sharedInsight](insights-shared.md) collection		| Calculated relationship identifying documents shared with or by the user, includes file attachments in emails and meetings, as well as URLs and Reference attachments to OneDrive for Business and SharePoint files found in emails, meetings, and Teams conversations. Ordered by recency of share.|

## item Insights limitation settings
Trending and some types of used insights can be disabled for members of a specific security AAD group or for entire organization by updating [organizationsettings](organizationsettings.md) object using [organizationsettings-update](api/organizationsettings-update.md). 


Following privacy configurations are available for administrators to set up:
1. Item insights are enabled for all users in the organization without exceptions. Administrator need to set up
   1.1 'isEnabledInOrganization' == true
   1.2 'disabledForGroup' == empty
2. Item insights are enabled in the organization, but some users' item insights need to be disabled.Administrator need to set up
   2.1 'isEnabledInOrganization' == true
   2.2 'disabledForGroup' == ID of an security AAD group, where administrtator collect all users, which item insights need to be disabled.
3. Item insights are disabled for all users in the organization without exceptions. 
   3.1 isEnabledInOrganization' == false
   3.2 the 'disabledForGroup' parameter value does not matter

Disabled user item insights have followong consequences
1. API
2. UX

## JSON representation

Here is a JSON representation of the resource
<!-- {
  "blockType": "resource",
  "keyProperty":"id",
  "baseType":"microsoft.graph.entity",
  "optionalProperties": [
    "trending",
    "used",
    "shared"
  ],
  "@odata.type": "microsoft.graph.itemInsights"
}-->

```json
{
  "id": "string",
  "trending": [ { "@odata.type": "microsoft.graph.trending" } ],
  "used": [ { "@odata.type": "microsoft.graph.used" } ],
  "shared": [ { "@odata.type": "microsoft.graph.shared" } ]
}
```
