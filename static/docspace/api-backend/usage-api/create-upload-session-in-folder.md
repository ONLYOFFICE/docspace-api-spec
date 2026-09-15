# createUploadSessionInFolder

Referenced types are defined in the [full reference](../files.md).

> ChunkedUploadSessionResponseIntegerWrapper createUploadSessionInFolder(folderId, SessionRequest)

`POST /api/2.0/files/{folderId}/session`

Create an upload session

Opens a chunked upload session for a file in the folder named by the path and returns the session itself,  which is the difference from the deprecated &#x60;POST api/2.0/files/{folderId}/upload/create_session&#x60; and its  success envelope. The answer gives &#x60;id&#x60;, quoted by every later call, &#x60;location&#x60; for the standalone chunk  handler used by clients that bypass this API, &#x60;expired&#x60;, and &#x60;bytes_total&#x60; echoing the reserved size. Whether  parts are really needed follows from &#x60;fileSize&#x60;: below &#x60;chunkUploadSize&#x60; from &#x60;GET api/2.0/files/settings&#x60; the  whole payload goes in one &#x60;POST api/2.0/files/{folderId}/session/{sessionId}&#x60;, which stores the file and  answers 201, and above it the parts go one by one to  &#x60;POST api/2.0/files/{folderId}/session/{sessionId}/upload&#x60; and the file appears only after  &#x60;PUT api/2.0/files/{folderId}/session/{sessionId}/finalize&#x60;. The caller must be allowed to add content to the  folder, so readers, editors and guests are refused, a section root is refused as well, and an unknown folder  is answered as missing. Nothing is written until the parts arrive, and an abandoned session disappears twelve  hours later.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **folderId** | path | **Integer** (int32) | The folder that receives the file; take the id from a listing such as &#x60;GET api/2.0/files/@root&#x60;. A room or an  ordinary folder inside one is accepted, a section root is not. | [required] [example: 1] |
| **SessionRequest** | body | [**SessionRequest**](../files.md#model-sessionrequest) | The file the session is opened for, and how a clash with an existing name is settled. | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The created upload session | [**ChunkedUploadSessionResponseIntegerWrapper**](../files.md#model-chunkeduploadsessionresponseintegerwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **401** | Unauthorized | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**ChunkedUploadSessionResponseIntegerWrapper**](../files.md#model-chunkeduploadsessionresponseintegerwrapper)

## Authorization

[Basic](../files.md#basic), [OAuth2](../files.md#oauth2) (scopes: read, write), [ApiKeyBearer](../files.md#apikeybearer), [asc_auth_key](../files.md#asc_auth_key), [Bearer](../files.md#bearer), [OpenId](../files.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
