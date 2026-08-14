# sendOwnerChangeInstructions

Referenced types are defined in the [full reference](../api.md).

> OwnerChangeInstructionsWrapper sendOwnerChangeInstructions(OwnerIdSettingsRequestDto)

`POST /api/2.0/settings/owner`

Send the owner change instructions

Sends the instructions to change the DocSpace owner.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **OwnerIdSettingsRequestDto** | body | [**OwnerIdSettingsRequestDto**](../api.md#model-owneridsettingsrequestdto) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Message about changing the portal owner | [**OwnerChangeInstructionsWrapper**](../api.md#model-ownerchangeinstructionswrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | Owner&#39;s email is not activated | - | - |
| **403** | Collaborator can not be an owner | - | - |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**OwnerChangeInstructionsWrapper**](../api.md#model-ownerchangeinstructionswrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer) (scopes: read, write), [asc_auth_key](../api.md#asc_auth_key) (scopes: read, write), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
