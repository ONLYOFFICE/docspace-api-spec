# getBackupProgress

Referenced types are defined in the [full reference](../backup.md).

> BackupProgressWrapper getBackupProgress(Dump)

`GET /api/2.0/backup/getbackupprogress`

Get the backup progress

Reports the state of the backup job of the current portal, and is the operation to poll after  &#x60;POST api/2.0/backup/startbackup&#x60;. The queue holds one job per portal, so no job ID is passed in;  &#x60;dump&#x60; asks for the state of the server-wide job instead and requires the space access permission.  When there is no such job - none was ever started, or the finished one has already been dropped from  the queue - the call still answers 200, but the body carries no &#x60;response&#x60; member at all, so a client  has to treat the payload as optional rather than expect an empty object.  While the job runs, &#x60;isCompleted&#x60; is false, &#x60;error&#x60; and &#x60;link&#x60; are empty strings and &#x60;progress&#x60; grows  from 0 to 100. Once it stops, &#x60;isCompleted&#x60; turns true and &#x60;status&#x60; says how it ended: a non-empty  &#x60;error&#x60; is the only report of a failure, &#x60;warning&#x60; is set when the archive was written but some files  could not be read or when the job was cancelled, and &#x60;link&#x60; becomes the download link to the stored  archive.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **Dump** | query | **Boolean** | Applies the operation to the whole server rather than to the current portal, which requires the space  access permission and works on a standalone installation only. Server-wide backups and schedules are  kept apart from the ones of a portal, so the two values address different data. | [optional] [example: false] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The state of the backup job, or an empty payload when there is no such job | [**BackupProgressWrapper**](../backup.md#model-backupprogresswrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | No permissions to perform this action | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../backup.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../backup.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../backup.md#model-errorapiresponse) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](../backup.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**BackupProgressWrapper**](../backup.md#model-backupprogresswrapper)

## Authorization

[Basic](../backup.md#basic), [OAuth2](../backup.md#oauth2) (scopes: read, write), [ApiKeyBearer](../backup.md#apikeybearer), [asc_auth_key](../backup.md#asc_auth_key), [Bearer](../backup.md#bearer), [OpenId](../backup.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
