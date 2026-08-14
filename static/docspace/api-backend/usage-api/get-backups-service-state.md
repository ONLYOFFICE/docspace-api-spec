# getBackupsServiceState

Referenced types are defined in the [full reference](../backup.md).

> BackupServiceStateWrapper getBackupsServiceState()

`GET /api/2.0/backup/getservicestate`

Get the backup service state

Returns the backup service state.

## Parameters
This endpoint does not need any parameter.

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Backup service state | [**BackupServiceStateWrapper**](../backup.md#model-backupservicestatewrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | Access denied | - | - |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**BackupServiceStateWrapper**](../backup.md#model-backupservicestatewrapper)

## Authorization

[Basic](../backup.md#basic), [OAuth2](../backup.md#oauth2) (scopes: read, write), [ApiKeyBearer](../backup.md#apikeybearer) (scopes: read, write), [asc_auth_key](../backup.md#asc_auth_key) (scopes: read, write), [Bearer](../backup.md#bearer), [OpenId](../backup.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
