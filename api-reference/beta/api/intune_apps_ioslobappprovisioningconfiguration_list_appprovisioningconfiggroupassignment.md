﻿# List appProvisioningConfigGroupAssignments

> **Note:** Using the Microsoft Graph APIs to configure Intune controls and policies still requires that the Intune service is [correctly licensed](https://go.microsoft.com/fwlink/?linkid=839381) by the customer.

Get the appProvisioningConfigGroupAssignments from the groupAssignments navigation property.
## Prerequisites
One of the following **scopes** is required to execute this API:

*DeviceManagementApps.ReadWrite.All; DeviceManagementApps.Read.All*
## HTTP Request
<!-- {
  "blockType": "ignored"
}
-->
```http
GET /appProvisioningConfigurationGroupAssignments/
GET /deviceAppManagement/iosLobAppProvisioningConfigurations/{iosLobAppProvisioningConfigurationId}/groupAssignments/
```

## Request headers
|Header|Value|
|---|---|
|Authorization|Bearer {token}. Required.|
|Accept|application/json|

## Request body
Do not supply a request body for this method.

## Response
If successful, this method returns a `200 OK` response code and a collection of [appProvisioningConfigGroupAssignment](../resources/intune_apps_appprovisioningconfiggroupassignment.md) objects in the response body.

## Example
### Request
Here is an example of the request.
```http
GET https://graph.microsoft.com/beta/appProvisioningConfigurationGroupAssignments/
```

### Response
Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.
```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 217

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.appProvisioningConfigGroupAssignment",
      "targetGroupId": "Target Group Id value",
      "id": "9f68a8a7-a8a7-9f68-a7a8-689fa7a8689f"
    }
  ]
}
```



