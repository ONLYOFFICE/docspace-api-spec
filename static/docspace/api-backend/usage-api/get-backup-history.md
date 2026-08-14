# getBackupHistory

Referenced types are defined in the [full reference](../backup.md).

> BackupHistoryRecordArrayWrapper getBackupHistory(Dump)

`GET /api/2.0/backup/getbackuphistory`

Get the backup history

Returns the history of the started backup.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **Dump** | query | **Boolean** | Specifies if a dump will be created or not. | [optional] [example: true] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | List of backup history records | [**BackupHistoryRecordArrayWrapper**](../backup.md#model-backuphistoryrecordarraywrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | Access denied | - | - |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**BackupHistoryRecordArrayWrapper**](../backup.md#model-backuphistoryrecordarraywrapper)

## Authorization

[Basic](../backup.md#basic), [OAuth2](../backup.md#oauth2) (scopes: read, write), [ApiKeyBearer](../backup.md#apikeybearer) (scopes: read, write), [asc_auth_key](../backup.md#asc_auth_key) (scopes: read, write), [Bearer](../backup.md#bearer), [OpenId](../backup.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
