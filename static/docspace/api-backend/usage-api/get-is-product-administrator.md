# getIsProductAdministrator

Referenced types are defined in the [full reference](../api.md).

> ProductAdministratorWrapper getIsProductAdministrator(productid, userid)

`GET /api/2.0/settings/security/administrator`

Check a product administrator

Checks if the selected user is an administrator of a product with the ID specified in the request.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **productid** | query | **UUID** (uuid) | The ID of the product extracted from the query parameters. | [required] [example: 00000000-0000-0000-0000-000000000000] |
| **userid** | query | **UUID** (uuid) | The user ID extracted from the query parameters. | [required] [example: 00000000-0000-0000-0000-000000000000] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Object with the user security information: product ID, user ID, administrator or not | [**ProductAdministratorWrapper**](../api.md#model-productadministratorwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**ProductAdministratorWrapper**](../api.md#model-productadministratorwrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer) (scopes: read, write), [asc_auth_key](../api.md#asc_auth_key) (scopes: read, write), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
