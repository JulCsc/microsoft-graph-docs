---
description: "Automatically generated file. DO NOT MODIFY"
---

```csharp

var graphClient = new GraphServiceClient(requestAdapter);

var result = await graphClient.IdentityGovernance.LifecycleWorkflows.WorkflowTemplates.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "category eq 'leaver'";
});


```