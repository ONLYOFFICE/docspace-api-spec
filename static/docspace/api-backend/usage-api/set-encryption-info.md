# setEncryptionInfo

Referenced types are defined in the [full reference](../files.md).

> setEncryptionInfo(fileId, AccessRequestKeyDto)

`PUT /api/2.0/files/{fileId}/access`

Set file encryption information

Sets or updates the encryption keys for a file with the specified identifier. This allows updating the file&#39;s encryption configuration.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **fileId** | path | **Integer** (int32) | File ID | [required] [example: 12345] |
| **AccessRequestKeyDto** | body | [**List**](../files.md#model-accessrequestkeydto) | Collection of encryption key data for users with access to the file | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Encryption information successfully updated | - | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | You don&#39;t have enough permission to edit the file | - | - |
| **404** | File not found | - | - |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

null (empty response body)

## Authorization

[Basic](../files.md#basic), [OAuth2](../files.md#oauth2) (scopes: read, write), [ApiKeyBearer](../files.md#apikeybearer) (scopes: read, write), [asc_auth_key](../files.md#asc_auth_key) (scopes: read, write), [Bearer](../files.md#bearer), [OpenId](../files.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: Not defined
