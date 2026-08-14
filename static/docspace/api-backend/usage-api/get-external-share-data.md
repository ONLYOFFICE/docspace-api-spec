# getExternalShareData

Referenced types are defined in the [full reference](../files.md).

> ExternalShareWrapper getExternalShareData(key, fileId, folderId)

`GET /api/2.0/files/share/{key}`

Get the external data

Returns the external data by the key specified in the request.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **key** | path | **String** | The unique key of the external shared data. | [required] [example: doc_key_123] |
| **fileId** | query | **String** | The unique document identifier. | [optional] [example: 1] |
| **folderId** | query | **String** | The unique folder identifier. | [optional] [example: 1] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | External data | [**ExternalShareWrapper**](../files.md#model-externalsharewrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**ExternalShareWrapper**](../files.md#model-externalsharewrapper)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
