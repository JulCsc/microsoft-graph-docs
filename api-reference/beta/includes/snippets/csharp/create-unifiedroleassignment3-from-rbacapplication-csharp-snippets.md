---
description: "Automatically generated file. DO NOT MODIFY"
---

```csharp

var graphClient = new GraphServiceClient(requestAdapter);

var requestBody = new UnifiedRoleAssignment
{
	PrincipalId = "679a9213-c497-48a4-830a-8d3d25d94ddc",
	RoleDefinitionId = "ae79f266-94d4-4dab-b730-feca7e132178",
	AppScopeId = "/AccessPackageCatalog/beedadfe-01d5-4025-910b-84abb9369997",
};
var result = await graphClient.RoleManagement.EntitlementManagement.RoleAssignments.PostAsync(requestBody);


```