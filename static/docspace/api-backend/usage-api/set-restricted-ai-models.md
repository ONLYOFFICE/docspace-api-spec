# setRestrictedAiModels

Referenced types are defined in the [full reference](../api.md).

> RestrictedModelsResponseWrapper setRestrictedAiModels(SetRestrictedAiModelsRequestDto)

`PUT /api/2.0/portal/payment/ai-model/restrictions`

Set restricted AI models

Overwrites the entire set of restricted AI model IDs for the current tenant.  The request body must contain the complete desired set — to add a restriction, include the new model alongside existing ones;  to remove one, omit it. An empty set lifts all restrictions. Only portal administrators can perform this action.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **SetRestrictedAiModelsRequestDto** | body | [**SetRestrictedAiModelsRequestDto**](../api.md#model-setrestrictedaimodelsrequestdto) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The updated list of restricted AI model IDs | [**RestrictedModelsResponseWrapper**](../api.md#model-restrictedmodelsresponsewrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | No permissions to perform this action | - | - |
| **404** | Customer could not be found | - | - |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**RestrictedModelsResponseWrapper**](../api.md#model-restrictedmodelsresponsewrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer) (scopes: read, write), [asc_auth_key](../api.md#asc_auth_key) (scopes: read, write), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
