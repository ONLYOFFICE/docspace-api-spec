# startExternalDbSync

Referenced types are defined in the [full reference](../files.md).

> ExternalDbSyncTaskWrapper startExternalDbSync(id)

`POST /api/2.0/files/rooms/{id}/externaldbsync`

Start external DB sync

Triggers external DB synchronization for all form templates in the specified filling forms room.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **id** | path | **Integer** (int32) | The room ID. | [required] [example: 1] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Synchronization task information | [**ExternalDbSyncTaskWrapper**](../files.md#model-externaldbsynctaskwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | External DB is not configured | - | - |
| **403** | You do not have enough permissions to perform this action | - | - |
| **404** | Room not found | - | - |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**ExternalDbSyncTaskWrapper**](../files.md#model-externaldbsynctaskwrapper)

## Authorization

[Basic](../files.md#basic), [OAuth2](../files.md#oauth2) (scopes: read, write), [ApiKeyBearer](../files.md#apikeybearer) (scopes: read, write), [asc_auth_key](../files.md#asc_auth_key) (scopes: read, write), [Bearer](../files.md#bearer), [OpenId](../files.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
