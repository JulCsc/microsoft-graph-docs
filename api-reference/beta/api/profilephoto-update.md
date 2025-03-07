---
title: "Update profilephoto"
description: "Update the photo for any user in the tenant including the signed-in user, or the specified group or contact or team."
ms.localizationpriority: medium
doc_type: apiPageType
ms.prod: "people"
author: "kevinbellinger"
---

# Update profilephoto

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Update the photo for the specified contact, group, team, or user in a tenant. The size of the photo you can update to must be under 8MB.

Only use PUT for this operation.

> **Note**:  When updating the **user** photo, this operation first attempts to update the photo in Microsoft 365. If that fails (due to the user not having a mailbox), this API will attempt to update the photo in Azure Active Directory.

## Permissions
The following tables show the least privileged permission or permissions required to call this API on each supported resource type. Follow [best practices](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions) to request least privileged permissions. For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).


### To update the profile photo of a contact

|Permission type      | Least privileged permissions             | Higher privileged permissions             |
|:--------------------|:-----------------------------------------|:------------------------------------------|
|Delegated (work or school account)      |   Contacts.ReadWrite           | Contacts.ReadWrite.Shared |
|Delegated (personal Microsoft account)      |   Not supported.            | Not supported. |
|Application      |    Contacts.ReadWrite           | Not supported. |

### To update the profile photo of a group

|Permission type      | Least privileged permissions             | Higher privileged permissions             |
|:--------------------|:-----------------------------------------|:------------------------------------------|
|Delegated (work or school account)      |   Group.ReadWrite.All           | Not supported. |
|Delegated (personal Microsoft account)      |   Not supported.            | Not supported. |
|Application      |    Group.ReadWrite.All           | Not supported. |

### To update the profile photo of a team

|Permission type      | Least privileged permissions             | Higher privileged permissions             |
|:--------------------|:-----------------------------------------|:------------------------------------------|
| Delegated (work or school account)     | TeamSettings.ReadWrite.All | Group.ReadWrite.All*, Directory.ReadWrite.All* |
| Delegated (personal Microsoft account) | Not supported.                                                         | Not supported. |
| Application                            | Not supported.                                                         | Not supported. |

### To update the profile photo of the signed-in user

|Permission type      | Least privileged permissions             | Higher privileged permissions             |
|:--------------------|:-----------------------------------------|:------------------------------------------|
|Delegated (work or school account)      |   User.ReadWrite | User.ReadWrite.All           |
|Delegated (personal Microsoft account)      |   Not supported.            | Not supported. |
|Application      |    User.ReadWrite.All           | Not supported. |

> [!NOTE]
> - There is currently a [known issue](/graph/known-issues#groups) with accessing group photos using application permissions.
> - Permissions marked with * are supported only for backward compatibility. Please update your solutions to use an alternative permission and avoid using these permissions going forward.
> - To update the photo of any user in the organization, your app must have the *User.ReadWrite.All* application permission and call this API under its own identity, not on behalf of a user. To learn more, see [get access without a signed-in user](/graph/auth-v2-service). Updating the photo of the signed-in user only requires *User.ReadWrite* permission.
> - Updating a user's photo using the Microsoft Graph API is currently not supported in Azure AD B2C tenants.

## HTTP request

To update a contact's profile photo:
<!-- { "blockType": "ignored" } -->
```http
PUT /me/contacts/{id}/photo/$value
PUT /users/{id | userPrincipalName}/contacts/{id}/photo/$value
PUT /me/contactfolders/{contactFolderId}/contacts/{id}/photo/$value
PUT /users/{id | userPrincipalName}/contactfolders/{contactFolderId}/contacts/{id}/photo/$value
```

To update a group photo:

<!-- { "blockType": "ignored" } -->
```http
PUT /groups/{id}/photo/$value
```

To update a team photo:
<!-- { "blockType": "ignored" } -->
```http
PUT /groups/{teamId}/photo/$value
```

To update a user's profile photo:
<!-- { "blockType": "ignored" } -->
```http
PUT /me/photo/$value
PUT /users/{id | userPrincipalName}/photo/$value
```


## Request headers
| Header       | Value |
|:---------------|:--------|
| Authorization  | Bearer {token}. Required.  |
| Content-Type  | image/jpeg. Required.  |

## Request body
In the request body, include the binary data of the photo in the request body.

## Response

If successful, this method returns a `200 OK` response code or a `204 No Content` response code for updating the photo of a team.

## Examples
### Example 1: Update the profile photo of the user
#### Request
The following is an example of the request.

# [HTTP](#tab/http)
<!-- {
  "blockType": "request",
  "name": "update_profilephoto"
}-->
```http
PUT https://graph.microsoft.com/beta/me/photo/$value
Content-type: image/jpeg

Binary data for the image

```

# [Java](#tab/java)
[!INCLUDE [sample-code](../includes/snippets/java/update-profilephoto-java-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [JavaScript](#tab/javascript)
[!INCLUDE [sample-code](../includes/snippets/javascript/update-profilephoto-javascript-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

---

#### Response
The following is an example of the response. 

> **Note:** The response object shown here might be shortened for readability.

<!-- {
  "blockType": "response"
} -->
```http
HTTP/1.1 200 OK
```

### Example 2: Update the photo of a team

#### Request
The following is an example of a request to update a team photo.


# [HTTP](#tab/http)
<!-- {
  "blockType": "request",
  "name": "update_team_photo"
}-->
```http
PUT https://graph.microsoft.com/beta/teams/172b0cce-e65d-44ce-9a49-91d9f2e8491e/photo/$value
Content-type: image/jpeg

Binary data for the image
```

# [Java](#tab/java)
[!INCLUDE [sample-code](../includes/snippets/java/update-team-photo-java-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [JavaScript](#tab/javascript)
[!INCLUDE [sample-code](../includes/snippets/javascript/update-team-photo-javascript-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

---

#### Response

The following is an example of the response.

<!-- {
  "blockType": "response",
  "truncated": true
} -->

```http
HTTP/1.1 204 No Content
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!--
{
  "type": "#page.annotation",
  "description": "Update profilephoto",
  "keywords": "",
  "section": "documentation",
  "tocPath": "",
  "suppressions": [
  ]
}
-->
