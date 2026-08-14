# uploadAsyncSession

Referenced types are defined in the [full reference](../files.md).

> ChunkedUploadSessionResponseIntegerWrapper uploadAsyncSession(folderId, sessionId, ChunkNumber, File)

`POST /api/2.0/files/{folderId}/session/{sessionId}/upload`

Handles the upload of a chunk for an existing upload session.

This method allows the caller to upload a specific chunk of a file to an ongoing upload session.  The session is identified by the session ID provided in the request. The chunk can be of any size  within the limits allowed during the session initialization. Each chunk must be uploaded in the  correct order for the server to process it appropriately.  The server updates the upload session status and stores the progress information after processing  each chunk. The updated session details are returned in the response.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **folderId** | path | **Integer** (int32) | The folder ID. | [required] [example: 1] |
| **sessionId** | path | **String** | The upload session ID. | [required] [example: session_abc123] |
| **ChunkNumber** | query | **Integer** (int32) | The chunk number. | [optional] [example: 1] |
| **File** | form | **File** (binary) | The file chunk to be uploaded as part of the multipart/form-data request.  This property represents the uploaded file chunk content from the HTTP request form for chunked upload operations.  The file chunk is accessed via the IFormFile interface which provides access to the chunk content and length. | [optional] |

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

- **Content-Type**: multipart/form-data
- **Accept**: application/json
