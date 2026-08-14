# createUploadSessionInFolder

Referenced types are defined in the [full reference](../files.md).

> ChunkedUploadSessionResponseIntegerWrapper createUploadSessionInFolder(folderId, SessionRequest)

`POST /api/2.0/files/{folderId}/session`

Creates a session for uploading a file to a specific folder in chunks.

The session allows the user to upload a file in smaller chunks to the folder identified by its ID.  The file information, such as name, size, and additional metadata, must be provided in the request.  This method facilitates large file upload scenarios by enabling chunked file uploads.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **folderId** | path | **Integer** (int32) | The session folder ID. | [required] [example: 1] |
| **SessionRequest** | body | [**SessionRequest**](../files.md#model-sessionrequest) | The session parameters. | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | OK | [**ChunkedUploadSessionResponseIntegerWrapper**](../files.md#model-chunkeduploadsessionresponseintegerwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**ChunkedUploadSessionResponseIntegerWrapper**](../files.md#model-chunkeduploadsessionresponseintegerwrapper)

## Authorization

[Basic](../files.md#basic), [OAuth2](../files.md#oauth2) (scopes: read, write), [ApiKeyBearer](../files.md#apikeybearer) (scopes: read, write), [asc_auth_key](../files.md#asc_auth_key) (scopes: read, write), [Bearer](../files.md#bearer), [OpenId](../files.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
