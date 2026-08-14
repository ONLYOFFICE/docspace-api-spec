# uploadFile

Referenced types are defined in the [full reference](../files.md).

> FileIntegerArrayWrapper uploadFile(folderId, createNewIfExist, storeOriginalFile, keepConvertStatus, File)

`POST /api/2.0/files/{folderId}/upload`

Upload a file

Uploads a file specified in the request to the selected folder by single file uploading or standart multipart/form-data method.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **folderId** | path | **Integer** (int32) | The folder ID to upload a file. | [required] [example: 1] |
| **createNewIfExist** | query | **Boolean** | Specifies whether to create the new file if it already exists or not. | [optional] [example: true] |
| **storeOriginalFile** | query | **Boolean** | Specifies whether to upload documents in the original formats as well or not. | [optional] [example: true] |
| **keepConvertStatus** | query | **Boolean** | Specifies whether to keep the file converting status or not. | [optional] [example: false] |
| **File** | form | **File** (binary) | The file to be uploaded. | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Inserted file | [**FileIntegerArrayWrapper**](../files.md#model-fileintegerarraywrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | You don&#39;t have enough permission to create | - | - |
| **404** | Folder not found | - | - |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**FileIntegerArrayWrapper**](../files.md#model-fileintegerarraywrapper)

## Authorization

[Basic](../files.md#basic), [OAuth2](../files.md#oauth2) (scopes: read, write), [ApiKeyBearer](../files.md#apikeybearer) (scopes: read, write), [asc_auth_key](../files.md#asc_auth_key) (scopes: read, write), [Bearer](../files.md#bearer), [OpenId](../files.md#openid)

## HTTP request headers

- **Content-Type**: multipart/form-data
- **Accept**: application/json
