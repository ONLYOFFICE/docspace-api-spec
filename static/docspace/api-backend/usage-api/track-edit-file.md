# trackEditFile

Referenced types are defined in the [full reference](../files.md).

> ItemKeyValuePairBooleanStringWrapper trackEditFile(fileId, tabId, docKeyForTrack, isFinish)

`GET /api/2.0/files/file/{fileId}/trackeditfile`

Track file editing

Tracks file changes when editing.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **fileId** | path | **Integer** (int32) | The file ID to track editing changes. | [required] [example: 1] |
| **tabId** | query | **UUID** (uuid) | The tab ID to track editing changes. | [optional] [example: 00000000-0000-0000-0000-000000000000] |
| **docKeyForTrack** | query | **String** | The document key for tracking changes. | [optional] [example: abc123] |
| **isFinish** | query | **Boolean** | Specifies whether to finish file tracking or not. | [optional] [example: true] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | File changes | [**ItemKeyValuePairBooleanStringWrapper**](../files.md#model-itemkeyvaluepairbooleanstringwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | You don&#39;t have enough permission to perform the operation | - | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**ItemKeyValuePairBooleanStringWrapper**](../files.md#model-itemkeyvaluepairbooleanstringwrapper)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
