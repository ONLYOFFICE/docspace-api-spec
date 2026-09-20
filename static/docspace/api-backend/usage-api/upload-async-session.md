# uploadAsyncSession

Referenced types are defined in the [full reference](../files.md).

> ChunkedUploadSessionResponseResponseWrapper uploadAsyncSession(folderId, sessionId, ChunkNumber, File)

`POST /api/2.0/files/{folderId}/session/{sessionId}/upload`

Upload a numbered chunk

Stores one part of a file under the number given in &#x60;chunkNumber&#x60;, which is what the ordinary chunked flow  uses: parts are kept by their number rather than by arrival, so a part that failed can be resent under the  same number without restarting the session. Numbering starts at 1, and leaving the number out makes the server  count the parts itself. The answer is always the session, never the file, and this call never completes the  upload: the file appears only after &#x60;PUT api/2.0/files/{folderId}/session/{sessionId}/finalize&#x60;. Use  &#x60;POST api/2.0/files/{folderId}/session/{sessionId}&#x60; instead when the parts go strictly in order and the upload  should complete by itself. A part bigger than &#x60;chunkUploadSize&#x60; from &#x60;GET api/2.0/files/settings&#x60; is refused,  so that value is also the size to split the payload by. The first part of a PDF is inspected, and a PDF that  is not a fillable form is refused when the session targets a form-filling room. The session is found by its id  alone.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **folderId** | path | **Integer** (int32) | The folder the session was opened against. It is part of the route only and is not matched against the  session, which is found by its own id. | [required] [example: 1] |
| **sessionId** | path | **String** | The session this part belongs to, as returned in &#x60;id&#x60; when it was created; a 32-character hexadecimal string. | [required] [example: 9f1c7a2b4d3e4f5a8b6c0d1e2f3a4b5c] |
| **ChunkNumber** | query | **Integer** (int32) | The position of this part in the file, counted from 1. Sending the same number again replaces that part  instead of adding one, which is how a failed part is retried; leaving the number out makes the server count  the parts itself. | [optional] [example: 1] |
| **File** | form | **File** (binary) | The part of the file to store, sent as the multipart field of the same name. It is kept under the number given  beside it, and a part larger than the portal chunk size is refused. | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The session with its progress after the part was stored | [**ChunkedUploadSessionResponseResponseWrapper**](../files.md#model-chunkeduploadsessionresponseresponsewrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **401** | Unauthorized | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**ChunkedUploadSessionResponseResponseWrapper**](../files.md#model-chunkeduploadsessionresponseresponsewrapper)

## Third-party storage

For a file or folder in a connected third-party storage the identifier is a string such as `sbox-42`, and the call differs in these parts only:

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **folderId** | path | **String** | The folder the session was opened against. It is part of the route only and is not matched against the  session, which is found by its own id. | [required] [example: 1] |

Return type: [**ThirdPartyChunkedUploadSessionResponseResponseWrapper**](../files.md#model-thirdpartychunkeduploadsessionresponseresponsewrapper)

## Authorization

[Basic](../files.md#basic), [OAuth2](../files.md#oauth2) (scopes: read, write), [ApiKeyBearer](../files.md#apikeybearer), [asc_auth_key](../files.md#asc_auth_key), [Bearer](../files.md#bearer), [OpenId](../files.md#openid)

## HTTP request headers

- **Content-Type**: multipart/form-data
- **Accept**: application/json
