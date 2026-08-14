# getEncryptionInfo

Referenced types are defined in the [full reference](../files.md).

> FileEncryptionInfoWrapper getEncryptionInfo(fileId)

`GET /api/2.0/files/{fileId}/access`

Get file encryption information

Returns the encryption information for a file with the specified identifier, including user encryption keys and file-specific encryption keys.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **fileId** | path | **Integer** (int32) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | File encryption information | [**FileEncryptionInfoWrapper**](../files.md#model-fileencryptioninfowrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | Invalid operation | - | - |
| **403** | You don&#39;t have enough permission to read the file | - | - |
| **404** | File not found | - | - |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**FileEncryptionInfoWrapper**](../files.md#model-fileencryptioninfowrapper)

## Authorization

[Basic](../files.md#basic), [OAuth2](../files.md#oauth2) (scopes: read, write), [ApiKeyBearer](../files.md#apikeybearer) (scopes: read, write), [asc_auth_key](../files.md#asc_auth_key) (scopes: read, write), [Bearer](../files.md#bearer), [OpenId](../files.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
