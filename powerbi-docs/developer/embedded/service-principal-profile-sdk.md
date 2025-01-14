---
title: Use the Power BI SDK with service principal profiles
description: Learn how to use the Power BI SDK to create and set the Power BI Client when using a service principal profile.
author: mberdugo
ms.author: monaberdugo
ms.reviewer: mshmordo
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.date: 03/17/2022
---

# Use the Power BI SDK with service principal profiles

This article explains how to use the SDK with [service principal profiles](embed-multi-tenancy.md).
There are two ways to connect a Power BI client to a service principal profile. You can:

* [Create a client with a profile object ID](#create-a-power-bi-client-with-a-service-principal-profile)
* [Specify the profile ID in the API request call](#set-profile-on-api-request-call)

Once the client is associated with a profile, you can [get the current service principal profile from the Power BI client](#get-the-current-service-principal-profile-from-power-bi-client).

## Create a Power BI client with a service principal profile

```csharp
var profileObjectId = new Guid("81f24a6d-7ebb-4478-99c7-2c36f7870a26"); 
var powerBIclient = new PowerBIClient(credentials, profileObjectId: profileObjectId);
```

When you create a Power BI client with the profile object ID, every API call that uses the client is issued with the `X-PowerBI-profile-id` in the request header.

For example,

```rest
GET https://powerbiapi.analysis-df.windows.net/v1.0/myorg/groups


Authorization: Bearer eyJ0eXAiO.....5U_g
X-PowerBI-profile-id: 81f24a6d-7ebb-4478-99c7-2c36f7870a26
```

## Set profile on API request call

Alternatively, you can specify the profile ID in the API request by using the `customHeaders` property in the API’s overloaded PowerBIClient method `WithHttpMessagesAsync`.

```csharp
var powerBIclient = new PowerBIClient(credentials); 
var profileHeader = new Dictionary<string, List<string>>(); 
profileHeader.Add("X-PowerBI-profile-id", new List<string> { "81f24a6d-7ebb-4478-99c7-2c36f7870a26" }); 
var groups = await powerBIclient.Groups.GetGroupsWithHttpMessagesAsync(customHeaders: profileHeader); 
```

For example,

```rest
GET https://powerbiapi.analysis-df.windows.net/v1.0/myorg/groups 

Authorization: Bearer eyJ0eXAiO.....5U_g 
X-PowerBI-profile-id: 81f24a6d-7ebb-4478-99c7-2c36f7870a26 
```

In the case, the profile header will *not* be added to the client default headers. You need to specify it with every API request.

Make sure you avoid duplications. For example, creating a client with a profile object ID and then specifying the header with the API request will result in unauthorized errors.  

## Get the current service principal profile from Power BI client

To retrieve the current service principal profile from the SDK client, call `GetServicePrincipalProfileObjectId`.

```csharp
var profileObjectId = new Guid("81f24a6d-7ebb-4478-99c7-2c36f7870a26"); 
var powerBIclient = new PowerBIClient(credentials, profileObjectId: profileObjectId); 
var currentProfileObjectId = powerBIclient.GetServicePrincipalProfileObjectId(); 
```

## Next steps

>[!div class="nextstepaction"]
>[Service principal profiles in Power BI Embedded](embed-multi-tenancy.md)
