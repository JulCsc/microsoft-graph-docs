---
description: "Automatically generated file. DO NOT MODIFY"
---

```php

<?php

// THIS SNIPPET IS A PREVIEW FOR THE KIOTA BASED SDK. NON-PRODUCTION USE ONLY
$graphServiceClient = new GraphServiceClient($requestAdapter);

$requestBody = new EdiscoverySearch();
$requestBody->setDisplayName('My search 2');

$requestBody->setDescription('My first search');

$requestBody->setContentQuery('(Author=\"edison\")');

$additionalData = [
		'custodianSources@odata.bind' => ['https://graph.microsoft.com/beta/security/cases/ediscoveryCases/b0073e4e-4184-41c6-9eb7-8c8cc3e2288b/custodians/0053a61a3b6c42738f7606791716a22a/userSources/43434642-3137-3138-3432-374142313639', 'https://graph.microsoft.com/beta/security/cases/ediscoveryCases/b0073e4e-4184-41c6-9eb7-8c8cc3e2288b/custodians/0053a61a3b6c42738f7606791716a22a/siteSources/169718e3-a8df-449d-bef4-ee09fe1ddc5d', 'https://graph.microsoft.com/beta/security/cases/ediscoveryCases(\'b0073e4e-4184-41c6-9eb7-8c8cc3e2288b\')/custodians(\'0053a61a3b6c42738f7606791716a22a\')/unifiedGroupSources(\'32e14fa4-3106-4bd2-a245-34bf0c718a7e\')', ],
	'noncustodialSources@odata.bind' => ['https://graph.microsoft.com/beta/security/cases/ediscoveryCases/b0073e4e-4184-41c6-9eb7-8c8cc3e2288b/noncustodialdatasources/35393639323133394345384344303043', ],
];
$requestBody->setAdditionalData($additionalData);




$result = $graphServiceClient->security()->cases()->ediscoveryCasesById('ediscoveryCase-id')->searches()->post($requestBody);


```