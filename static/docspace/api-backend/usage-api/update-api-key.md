# updateApiKey

Referenced types are defined in the [full reference](../people.md).

> BooleanWrapper updateApiKey(keyId, UpdateApiKeyRequest)

`PUT /api/2.0/keys/{keyId}`

Update an API key

Updates an existing API key changing its name, permissions, and status.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **keyId** | path | **UUID** (uuid) | The unique identifier of the API key to update. | [required] [example: 00000000-0000-0000-0000-000000000000] |
| **UpdateApiKeyRequest** | body | [**UpdateApiKeyRequest**](../people.md#model-updateapikeyrequest) | The request parameters for updating an existing API key. | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Update optional params for user api keys | [**BooleanWrapper**](../people.md#model-booleanwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**BooleanWrapper**](../people.md#model-booleanwrapper)

## Authorization

[Basic](../people.md#basic), [OAuth2](../people.md#oauth2) (scopes: read, write), [ApiKeyBearer](../people.md#apikeybearer) (scopes: read, write), [asc_auth_key](../people.md#asc_auth_key) (scopes: read, write), [Bearer](../people.md#bearer), [OpenId](../people.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

## GroupApi
