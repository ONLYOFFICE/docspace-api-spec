# applyExternalSharePassword

Referenced types are defined in the [full reference](../files.md).

> ExternalShareWrapper applyExternalSharePassword(key, ExternalShareRequestParam)

`POST /api/2.0/files/share/{key}/password`

Apply external data password

Applies a password specified in the request to get the external data.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **key** | path | **String** | The unique document identifier. | [required] [example: doc_key_123] |
| **ExternalShareRequestParam** | body | [**ExternalShareRequestParam**](../files.md#model-externalsharerequestparam) | The external data share request parameters. | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | External data | [**ExternalShareWrapper**](../files.md#model-externalsharewrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **429** | Too many requests | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**ExternalShareWrapper**](../files.md#model-externalsharewrapper)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
