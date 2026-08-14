# sendEmailChangeInstructions

Referenced types are defined in the [full reference](../people.md).

> StringWrapper sendEmailChangeInstructions(UpdateMemberRequestDto)

`POST /api/2.0/people/email`

Send instructions to change email

Sends a message to the user email with the instructions to change the email address connected to the portal.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **UpdateMemberRequestDto** | body | [**UpdateMemberRequestDto**](../people.md#model-updatememberrequestdto) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Message text | [**StringWrapper**](../people.md#model-stringwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | Incorrect userId or email | - | - |
| **403** | No permissions to perform this action | - | - |
| **404** | User not found | - | - |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**StringWrapper**](../people.md#model-stringwrapper)

## Authorization

[Basic](../people.md#basic), [OAuth2](../people.md#oauth2) (scopes: read, write), [ApiKeyBearer](../people.md#apikeybearer) (scopes: read, write), [asc_auth_key](../people.md#asc_auth_key) (scopes: read, write), [Bearer](../people.md#bearer), [OpenId](../people.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

## PeopleGuestsApi
