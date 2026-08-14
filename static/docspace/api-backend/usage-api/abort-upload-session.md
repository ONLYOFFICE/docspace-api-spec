# abortUploadSession

Referenced types are defined in the [full reference](../files.md).

> abortUploadSession(sessionId, folderId)

`DELETE /api/2.0/files/{folderId}/session/{sessionId}`

Aborts an in-progress file upload session.

This method allows users to cancel an ongoing upload session identified by the session ID.  Once the session is aborted, the associated resources will be cleaned up, and the session will no longer accept further uploads.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **sessionId** | path | **String** | The session ID. | [required] [example: session-123-abc] |
| **folderId** | path | **Integer** (int32) | The folder ID. | [required] [example: 1] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | OK | - | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

null (empty response body)

## Authorization

[Basic](../files.md#basic), [OAuth2](../files.md#oauth2) (scopes: read, write), [ApiKeyBearer](../files.md#apikeybearer) (scopes: read, write), [asc_auth_key](../files.md#asc_auth_key) (scopes: read, write), [Bearer](../files.md#bearer), [OpenId](../files.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: Not defined
