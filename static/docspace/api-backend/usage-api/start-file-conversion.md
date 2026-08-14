# startFileConversion

Referenced types are defined in the [full reference](../files.md).

> ConversationResultArrayWrapper startFileConversion(fileId, CheckConversionRequestDtoInteger)

`PUT /api/2.0/files/file/{fileId}/checkconversion`

Start file conversion

Starts a conversion operation of a file with the ID specified in the request.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **fileId** | path | **Integer** (int32) | The file ID to start conversion proccess. | [required] [example: 1] |
| **CheckConversionRequestDtoInteger** | body | [**CheckConversionRequestDtoInteger**](../files.md#model-checkconversionrequestdtointeger) | The parameters for checking file conversion. | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Conversion result | [**ConversationResultArrayWrapper**](../files.md#model-conversationresultarraywrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**ConversationResultArrayWrapper**](../files.md#model-conversationresultarraywrapper)

## Authorization

[Basic](../files.md#basic), [OAuth2](../files.md#oauth2) (scopes: read, write), [ApiKeyBearer](../files.md#apikeybearer) (scopes: read, write), [asc_auth_key](../files.md#asc_auth_key) (scopes: read, write), [Bearer](../files.md#bearer), [OpenId](../files.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
