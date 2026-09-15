# startBackup

Referenced types are defined in the [full reference](../backup.md).

> BackupProgressWrapper startBackup(BackupDto)

`POST /api/2.0/backup/startbackup`

Start the backup

Queues a backup of the current portal and returns straight away: the archive itself is written by the  separate backup worker service, which picks the job up from an integration event, so the response  reports a progress of 0 and the &#x60;Created&#x60; status, and its &#x60;taskId&#x60; is the handle to poll with  &#x60;GET api/2.0/backup/getbackupprogress&#x60;. The caller needs the portal settings permission, and  &#x60;dump&#x60; - a backup of the whole server instead of this one portal - additionally requires the space  access permission and is rejected outside a standalone installation.  The keys expected in &#x60;storageParams&#x60; depend on &#x60;storageType&#x60;: &#x60;Documents&#x60; takes an integer &#x60;folderId&#x60;,  &#x60;ThridpartyDocuments&#x60; takes a provider-specific non-integer &#x60;folderId&#x60;, &#x60;Local&#x60; takes &#x60;filePath&#x60; and  works on a standalone installation only, &#x60;ThirdPartyConsumer&#x60; takes &#x60;module&#x60; together with the settings  of that consumer, and &#x60;DataStore&#x60; takes no keys at all; the &#x60;subdir&#x60; key is added by the operation  itself and must not be sent.  A portal that has already used up the free backups of the current calendar month is charged through the  paid backup service instead, and the call is rejected with 402 when that service is not available to it.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **BackupDto** | body | [**BackupDto**](../backup.md#model-backupdto) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The state of the queued backup job | [**BackupProgressWrapper**](../backup.md#model-backupprogresswrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | The folder ID does not match the storage type, or a dump was requested on a portal that is not a standalone installation | - | - |
| **402** | The free backups of the current month are used up and the paid backup service is not available to this portal | - | - |
| **403** | No permissions to perform this action | - | - |
| **404** | The target folder or the backup quota was not found | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../backup.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../backup.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../backup.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**BackupProgressWrapper**](../backup.md#model-backupprogresswrapper)

## Authorization

[Basic](../backup.md#basic), [OAuth2](../backup.md#oauth2) (scopes: read, write), [ApiKeyBearer](../backup.md#apikeybearer), [asc_auth_key](../backup.md#asc_auth_key), [Bearer](../backup.md#bearer), [OpenId](../backup.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
