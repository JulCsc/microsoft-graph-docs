---
description: "Automatically generated file. DO NOT MODIFY"
---

```php

<?php

// THIS SNIPPET IS A PREVIEW FOR THE KIOTA BASED SDK. NON-PRODUCTION USE ONLY
$graphServiceClient = new GraphServiceClient($requestAdapter);

$requestBody = new ConnectorGroup();
$requestBody->setName('Connector Group Demo');



$result = $graphServiceClient->onPremisesPublishingProfilesById('onPremisesPublishingProfile-id')->connectorGroups()->post($requestBody);


```