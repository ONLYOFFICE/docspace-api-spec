# copyFileAs

Referenced types are defined in the [full reference](../files.md).

> FileEntryBaseWrapper copyFileAs(fileId, CopyAsJsonElement)

`POST /api/2.0/files/file/{fileId}/copyas`

Copy a file

Copies (and converts if possible) an existing file to the specified folder.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **fileId** | path | **Integer** (int32) | The file ID to copy. | [required] [example: 1] |
| **CopyAsJsonElement** | body | [**CopyAsJsonElement**](../files.md#model-copyasjsonelement) | The parameters for copying a file. | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Copied file entry information | [**FileEntryBaseWrapper**](../files.md#model-fileentrybasewrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | No file id or folder id toFolderId determine provider | - | - |
| **403** | You don&#39;t have enough permission to create | - | - |
| **404** | File not found | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**FileEntryBaseWrapper**](../files.md#model-fileentrybasewrapper)

## Authorization

[Basic](../files.md#basic), [OAuth2](../files.md#oauth2) (scopes: read, write), [ApiKeyBearer](../files.md#apikeybearer), [asc_auth_key](../files.md#asc_auth_key), [Bearer](../files.md#bearer), [OpenId](../files.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
