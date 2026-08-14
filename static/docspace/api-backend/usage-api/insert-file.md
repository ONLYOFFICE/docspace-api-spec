# insertFile

Referenced types are defined in the [full reference](../files.md).

> FileIntegerWrapper insertFile(folderId, InsertFile.File, InsertFile.Title, InsertFile.CreateNewIfExist, InsertFile.KeepConvertStatus, InsertFile.Stream.CanRead, InsertFile.Stream.CanWrite, InsertFile.Stream.CanSeek, InsertFile.Stream.CanTimeout, InsertFile.Stream.Length, InsertFile.Stream.Position, InsertFile.Stream.ReadTimeout, InsertFile.Stream.WriteTimeout)

`POST /api/2.0/files/{folderId}/insert`

Insert a file

Inserts a file specified in the request to the selected folder by single file uploading.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **folderId** | path | **Integer** (int32) | The folder ID for inserting a file. | [required] [example: 1] |
| **InsertFile.File** | form | **File** (binary) | The file to be inserted. | [optional] |
| **InsertFile.Title** | form | **String** | The file title to be inserted. | [optional] |
| **InsertFile.CreateNewIfExist** | form | **Boolean** | Specifies whether to create a new file if it already exists or not. | [optional] |
| **InsertFile.KeepConvertStatus** | form | **Boolean** | Specifies whether to keep the file converting status or not. | [optional] |
| **InsertFile.Stream.CanRead** | form | **Boolean** |  | [optional] |
| **InsertFile.Stream.CanWrite** | form | **Boolean** |  | [optional] |
| **InsertFile.Stream.CanSeek** | form | **Boolean** |  | [optional] |
| **InsertFile.Stream.CanTimeout** | form | **Boolean** |  | [optional] |
| **InsertFile.Stream.Length** | form | **Long** (int64) |  | [optional] |
| **InsertFile.Stream.Position** | form | **Long** (int64) |  | [optional] |
| **InsertFile.Stream.ReadTimeout** | form | **Integer** (int32) |  | [optional] |
| **InsertFile.Stream.WriteTimeout** | form | **Integer** (int32) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Inserted file | [**FileIntegerWrapper**](../files.md#model-fileintegerwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | You don&#39;t have enough permission to create | - | - |
| **404** | Folder not found | - | - |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**FileIntegerWrapper**](../files.md#model-fileintegerwrapper)

## Authorization

[Basic](../files.md#basic), [OAuth2](../files.md#oauth2) (scopes: read, write), [ApiKeyBearer](../files.md#apikeybearer) (scopes: read, write), [asc_auth_key](../files.md#asc_auth_key) (scopes: read, write), [Bearer](../files.md#bearer), [OpenId](../files.md#openid)

## HTTP request headers

- **Content-Type**: multipart/form-data
- **Accept**: application/json
