# insertFileToMyFromBody

Referenced types are defined in the [full reference](../files.md).

> FileIntegerWrapper insertFileToMyFromBody(File, Title, CreateNewIfExist, KeepConvertStatus, Stream.CanRead, Stream.CanWrite, Stream.CanSeek, Stream.CanTimeout, Stream.Length, Stream.Position, Stream.ReadTimeout, Stream.WriteTimeout)

`POST /api/2.0/files/@my/insert`

Insert a file to the My documents section

Inserts a file specified in the request to the My documents section by single file uploading.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **File** | form | **File** (binary) | The file to be inserted. | [optional] |
| **Title** | form | **String** | The file title to be inserted. | [optional] |
| **CreateNewIfExist** | form | **Boolean** | Specifies whether to create a new file if it already exists or not. | [optional] |
| **KeepConvertStatus** | form | **Boolean** | Specifies whether to keep the file converting status or not. | [optional] |
| **Stream.CanRead** | form | **Boolean** |  | [optional] |
| **Stream.CanWrite** | form | **Boolean** |  | [optional] |
| **Stream.CanSeek** | form | **Boolean** |  | [optional] |
| **Stream.CanTimeout** | form | **Boolean** |  | [optional] |
| **Stream.Length** | form | **Long** (int64) |  | [optional] |
| **Stream.Position** | form | **Long** (int64) |  | [optional] |
| **Stream.ReadTimeout** | form | **Integer** (int32) |  | [optional] |
| **Stream.WriteTimeout** | form | **Integer** (int32) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Inserted file | [**FileIntegerWrapper**](../files.md#model-fileintegerwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | You don&#39;t have enough permission to create | - | - |
| **404** | Folder not found | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**FileIntegerWrapper**](../files.md#model-fileintegerwrapper)

## Authorization

[Basic](../files.md#basic), [OAuth2](../files.md#oauth2) (scopes: read, write), [ApiKeyBearer](../files.md#apikeybearer), [asc_auth_key](../files.md#asc_auth_key), [Bearer](../files.md#bearer), [OpenId](../files.md#openid)

## HTTP request headers

- **Content-Type**: multipart/form-data
- **Accept**: application/json
