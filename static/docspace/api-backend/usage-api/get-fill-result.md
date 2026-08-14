# getFillResult

Referenced types are defined in the [full reference](../files.md).

> FillingFormResultIntegerWrapper getFillResult(fillingSessionId)

`GET /api/2.0/files/file/fillresult`

Get form-filling result

Retrieves the result of a form-filling session.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **fillingSessionId** | query | **String** | The form-filling session ID. | [optional] [example: doc_key_123] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Ok | [**FillingFormResultIntegerWrapper**](../files.md#model-fillingformresultintegerwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**FillingFormResultIntegerWrapper**](../files.md#model-fillingformresultintegerwrapper)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
