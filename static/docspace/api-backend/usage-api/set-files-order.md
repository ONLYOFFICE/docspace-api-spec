# setFilesOrder

Referenced types are defined in the [full reference](../files.md).

> FileEntryIntegerArrayWrapper setFilesOrder(OrdersRequestDtoInteger)

`PUT /api/2.0/files/order`

Set order of files

Sets the order of the files specified in the request.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **OrdersRequestDtoInteger** | body | [**OrdersRequestDtoInteger**](../files.md#model-ordersrequestdtointeger) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Updated file entries information | [**FileEntryIntegerArrayWrapper**](../files.md#model-fileentryintegerarraywrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**FileEntryIntegerArrayWrapper**](../files.md#model-fileentryintegerarraywrapper)

## Authorization

[Basic](../files.md#basic), [OAuth2](../files.md#oauth2) (scopes: read, write), [ApiKeyBearer](../files.md#apikeybearer) (scopes: read, write), [asc_auth_key](../files.md#asc_auth_key) (scopes: read, write), [Bearer](../files.md#bearer), [OpenId](../files.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
