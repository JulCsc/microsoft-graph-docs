---
description: "Automatically generated file. DO NOT MODIFY"
---

```go

//THE GO SDK IS IN PREVIEW. NON-PRODUCTION USE ONLY
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/Me/MailFolders/Item/Copy"
	  //other-imports
)

graphClient := msgraphsdk.NewGraphServiceClientWithCredentials(cred, scopes)


requestBody := graphmodels.NewCopyPostRequestBody()
destinationId := "destinationId-value"
requestBody.SetDestinationId(&destinationId) 

result, err := graphClient.Me().MailFolders().ByMailFolderId("mailFolder-id").Copy().Post(context.Background(), requestBody, nil)


```