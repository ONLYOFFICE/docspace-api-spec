# checkDocServiceUrl

Referenced types are defined in the [full reference](../files.md).

> DocServiceUrlWrapper checkDocServiceUrl(CheckDocServiceUrlRequestDto)

`PUT /api/2.0/files/docservice`

Check the document service URL

Checks the document service location URL.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **CheckDocServiceUrlRequestDto** | body | [**CheckDocServiceUrlRequestDto**](../files.md#model-checkdocserviceurlrequestdto) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Document service information: the Document Server address, the Document Server address in the local private network, the Community Server address | [**DocServiceUrlWrapper**](../files.md#model-docserviceurlwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | Invalid input urls/Mixed Active Content is not allowed. HTTPS address for Document Server is required | - | - |
| **403** | You don&#39;t have enough permission to perform the operation | - | - |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**DocServiceUrlWrapper**](../files.md#model-docserviceurlwrapper)

## Authorization

[Basic](../files.md#basic), [OAuth2](../files.md#oauth2) (scopes: read, write), [ApiKeyBearer](../files.md#apikeybearer) (scopes: read, write), [asc_auth_key](../files.md#asc_auth_key) (scopes: read, write), [Bearer](../files.md#bearer), [OpenId](../files.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
