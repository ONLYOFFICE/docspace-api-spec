# ONLYOFFICE DocSpace Backup API

The browsable version of this reference, with a request builder and code samples, is published at
<https://api.onlyoffice.com/docspace/api-backend/usage-api/>.

All URIs are relative to *https://yourportal.onlyoffice.com*, where the host is the address of your DocSpace instance.

## Endpoints

| Class | Method | HTTP request | Description |
|------------ | ------------- | ------------- | -------------|
| *BackupApi* | [**cancelBackup**](#cancelbackup) | **POST** /api/2.0/backup/cancelbackup | Cancel the running backup |
| *BackupApi* | [**createBackupSchedule**](#createbackupschedule) | **POST** /api/2.0/backup/createbackupschedule | Create the backup schedule |
| *BackupApi* | [**deleteBackup**](#deletebackup) | **DELETE** /api/2.0/backup/deletebackup/{id} | Delete the backup |
| *BackupApi* | [**deleteBackupHistory**](#deletebackuphistory) | **DELETE** /api/2.0/backup/deletebackuphistory | Delete the backup history |
| *BackupApi* | [**deleteBackupSchedule**](#deletebackupschedule) | **DELETE** /api/2.0/backup/deletebackupschedule | Delete the backup schedule |
| *BackupApi* | [**getBackupHistory**](#getbackuphistory) | **GET** /api/2.0/backup/getbackuphistory | Get the backup history |
| *BackupApi* | [**getBackupProgress**](#getbackupprogress) | **GET** /api/2.0/backup/getbackupprogress | Get the backup progress |
| *BackupApi* | [**getBackupSchedule**](#getbackupschedule) | **GET** /api/2.0/backup/getbackupschedule | Get the backup schedule |
| *BackupApi* | [**getBackupsCount**](#getbackupscount) | **GET** /api/2.0/backup/getbackupscount | Get the number of backups |
| *BackupApi* | [**getBackupsCounts**](#getbackupscounts) | **GET** /api/2.0/backup/getbackupscountbypaid | Get free and paid backup counts |
| *BackupApi* | [**getBackupsServiceState**](#getbackupsservicestate) | **GET** /api/2.0/backup/getservicestate | Check whether backups are enabled |
| *BackupApi* | [**getRestoreProgress**](#getrestoreprogress) | **GET** /api/2.0/backup/getrestoreprogress | Get the restoring progress |
| *BackupApi* | [**startBackup**](#startbackup) | **POST** /api/2.0/backup/startbackup | Start the backup |
| *BackupApi* | [**startBackupRestore**](#startbackuprestore) | **POST** /api/2.0/backup/startrestore | Start the restoring process |



## BackupApi

### cancelBackup

> BooleanWrapper cancelBackup()

`POST /api/2.0/backup/cancelbackup`

Cancel the running backup

Drops the backup job of the current portal from the queue, which cancels it if it is still running.  The caller needs the portal settings permission. It answers false, not an error, when there is nothing  to cancel, so the result says whether a job was actually dropped rather than whether the call  succeeded.  This affects backup jobs only: a restoring job cannot be cancelled through the API. The cancelled job  leaves the queue, so a following &#x60;GET api/2.0/backup/getbackupprogress&#x60; reports no job at all rather  than a job with the &#x60;Canceled&#x60; status.

#### Parameters
This endpoint does not need any parameter.

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | True if a backup job was dropped from the queue, false if there was nothing to cancel | [**BooleanWrapper**](#model-booleanwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | No permissions to perform this action | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

#### Return type

[**BooleanWrapper**](#model-booleanwrapper)

#### Authorization

[Basic](#basic), [OAuth2](#oauth2) (scopes: read, write), [ApiKeyBearer](#apikeybearer), [asc_auth_key](#asc_auth_key), [Bearer](#bearer), [OpenId](#openid)

#### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

### createBackupSchedule

> BooleanWrapper createBackupSchedule(BackupScheduleDto)

`POST /api/2.0/backup/createbackupschedule`

Create the backup schedule

Sets the backup schedule of the current portal. A portal keeps at most one schedule, so this replaces  the existing one rather than adding a second, and &#x60;dump&#x60; writes the schedule of the whole server  instead, which requires the space access permission and works on a standalone installation only.  Scheduled backups have to be allowed by the pricing plan of a portal that is not a standalone  installation.  &#x60;cronParams&#x60; is a period plus a time rather than a cron string: &#x60;hour&#x60; is the hour of the day from 0  to 23, and &#x60;day&#x60; has to be given for &#x60;EveryWeek&#x60;, where it is the day of the week from 1 to 7 with  Sunday as 1, and for &#x60;EveryMonth&#x60;, where it is the day of the month from 1 to 31. It is left out for  &#x60;EveryDay&#x60;, and because an omitted &#x60;day&#x60; is stored as 0, which neither period accepts, a weekly or  monthly schedule sent without it fails instead of falling back to a default.  &#x60;backupsStored&#x60; is the number of scheduled copies to keep, from 1 to 30, and it defaults to 1. Older  copies are removed by a background cleaner, and only the ones this schedule created: archives made by  &#x60;POST api/2.0/backup/startbackup&#x60; are not counted and not removed. A portal whose subscription stops  covering backups has its schedule deleted by the scheduler, not suspended, and its administrators are  notified that the scheduled backup failed.  The keys expected in &#x60;storageParams&#x60; are the same as for &#x60;POST api/2.0/backup/startbackup&#x60;, except  that they are sent as an array of key and value pairs here and returned as an object by  &#x60;GET api/2.0/backup/getbackupschedule&#x60;.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **BackupScheduleDto** | body | [**BackupScheduleDto**](#model-backupscheduledto) |  | [optional] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | True if the schedule was saved | [**BooleanWrapper**](#model-booleanwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | The number of the stored copies is outside 1 - 30, or a dump was requested on a portal that is not a standalone installation | - | - |
| **402** | The portal subscription does not cover scheduled backups, has expired or has not been paid | - | - |
| **403** | No permissions to perform this action | - | - |
| **404** | The target folder was not found | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

#### Return type

[**BooleanWrapper**](#model-booleanwrapper)

#### Authorization

[Basic](#basic), [OAuth2](#oauth2) (scopes: read, write), [ApiKeyBearer](#apikeybearer), [asc_auth_key](#asc_auth_key), [Bearer](#bearer), [OpenId](#openid)

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

### deleteBackup

> BooleanWrapper deleteBackup(id)

`DELETE /api/2.0/backup/deletebackup/{id}`

Delete the backup

Deletes one backup: first its history record, then the archive in the storage the record points at.  The ID is the one listed by &#x60;GET api/2.0/backup/getbackuphistory&#x60;, which is also the &#x60;taskId&#x60; the  backup was started with.  Deleting a backup of the whole server rather than of one portal additionally requires the space  access permission. A record that belongs to another portal is left untouched and the call still  answers true, so the result confirms that the request was accepted rather than that anything was  deleted - check with &#x60;GET api/2.0/backup/getbackuphistory&#x60; if it matters.  The record is removed before the archive, so when the storage can no longer be reached the archive  stays behind with nothing pointing at it.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **id** | path | **UUID** (uuid) | The ID of the backup to delete, taken from the route. It is the &#x60;id&#x60; of a record listed by  &#x60;GET api/2.0/backup/getbackuphistory&#x60;, which is also the &#x60;taskId&#x60; the backup was started with. | [required] [example: 11111111-1111-1111-1111-111111111111] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | True once the request has been accepted, whether or not a backup was deleted | [**BooleanWrapper**](#model-booleanwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **402** | The portal subscription has expired or has not been paid | - | - |
| **403** | No permissions to perform this action | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](#model-errorapiresponse) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

#### Return type

[**BooleanWrapper**](#model-booleanwrapper)

#### Authorization

[Basic](#basic), [OAuth2](#oauth2) (scopes: read, write), [ApiKeyBearer](#apikeybearer), [asc_auth_key](#asc_auth_key), [Bearer](#bearer), [OpenId](#openid)

#### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

### deleteBackupHistory

> BooleanWrapper deleteBackupHistory(Dump)

`DELETE /api/2.0/backup/deletebackuphistory`

Delete the backup history

Deletes every backup of the current portal, both the history records and the archives themselves, and  leaves the backup schedule alone. &#x60;dump&#x60; clears the backups of the whole server instead and requires  the space access permission.  The records are walked one by one and a failure on any of them is swallowed, so the result is always  true even when some archives could not be deleted: it does not mean the history is now empty. Call  &#x60;GET api/2.0/backup/getbackuphistory&#x60; afterwards to see what is left.  Each record is removed before its archive, so an archive whose deletion fails stays in the storage  with nothing pointing at it.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **Dump** | query | **Boolean** | Applies the operation to the whole server rather than to the current portal, which requires the space  access permission and works on a standalone installation only. Server-wide backups and schedules are  kept apart from the ones of a portal, so the two values address different data. | [optional] [example: false] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | True once every record has been walked, whether or not all of them were deleted | [**BooleanWrapper**](#model-booleanwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **402** | The portal subscription has expired or has not been paid | - | - |
| **403** | No permissions to perform this action | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](#model-errorapiresponse) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

#### Return type

[**BooleanWrapper**](#model-booleanwrapper)

#### Authorization

[Basic](#basic), [OAuth2](#oauth2) (scopes: read, write), [ApiKeyBearer](#apikeybearer), [asc_auth_key](#asc_auth_key), [Bearer](#bearer), [OpenId](#openid)

#### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

### deleteBackupSchedule

> BooleanWrapper deleteBackupSchedule(Dump)

`DELETE /api/2.0/backup/deletebackupschedule`

Delete the backup schedule

Deletes the backup schedule of the current portal, which stops the scheduled backups; &#x60;dump&#x60; deletes  the schedule of the whole server instead and requires the space access permission. The archives the  schedule has already produced are kept and stay listed by  &#x60;GET api/2.0/backup/getbackuphistory&#x60; - delete them through  &#x60;DELETE api/2.0/backup/deletebackup/{id}&#x60; if they are no longer wanted.  The result is always true, including when there was no schedule to delete, so it confirms that the  portal now has none rather than that anything was removed. The deletion is written to the audit trail  either way.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **Dump** | query | **Boolean** | Applies the operation to the whole server rather than to the current portal, which requires the space  access permission and works on a standalone installation only. Server-wide backups and schedules are  kept apart from the ones of a portal, so the two values address different data. | [optional] [example: false] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | True once the portal has no backup schedule, whether or not one had to be deleted | [**BooleanWrapper**](#model-booleanwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **402** | The portal subscription has expired or has not been paid | - | - |
| **403** | No permissions to perform this action | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](#model-errorapiresponse) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

#### Return type

[**BooleanWrapper**](#model-booleanwrapper)

#### Authorization

[Basic](#basic), [OAuth2](#oauth2) (scopes: read, write), [ApiKeyBearer](#apikeybearer), [asc_auth_key](#asc_auth_key), [Bearer](#bearer), [OpenId](#openid)

#### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

### getBackupHistory

> BackupHistoryRecordArrayWrapper getBackupHistory(Dump)

`GET /api/2.0/backup/getbackuphistory`

Get the backup history

Lists the backups of the current portal whose archive is still present in the storage it was written  to. The records come back in no particular order, so sort them by &#x60;createdOn&#x60; if the newest one is  wanted. &#x60;dump&#x60; lists the backups of the whole server instead and requires the space access  permission.  Despite being a read operation, this prunes the history as it goes: a record whose archive is no  longer in its storage is deleted outright, so the list can shrink between two calls without anybody  deleting anything. A record whose storage can no longer be reached at all - a disconnected  third-party account, for instance - is neither returned nor deleted, so it stays invisible while  still occupying the history.  The &#x60;id&#x60; of a record is the same value as the &#x60;taskId&#x60; that  &#x60;POST api/2.0/backup/startbackup&#x60; returned for it, and it is what  &#x60;DELETE api/2.0/backup/deletebackup/{id}&#x60; and the &#x60;backupId&#x60; of  &#x60;POST api/2.0/backup/startrestore&#x60; expect.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **Dump** | query | **Boolean** | Applies the operation to the whole server rather than to the current portal, which requires the space  access permission and works on a standalone installation only. Server-wide backups and schedules are  kept apart from the ones of a portal, so the two values address different data. | [optional] [example: false] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The backups whose archive is still stored | [**BackupHistoryRecordArrayWrapper**](#model-backuphistoryrecordarraywrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **402** | The portal subscription has expired or has not been paid | - | - |
| **403** | No permissions to perform this action | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](#model-errorapiresponse) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

#### Return type

[**BackupHistoryRecordArrayWrapper**](#model-backuphistoryrecordarraywrapper)

#### Authorization

[Basic](#basic), [OAuth2](#oauth2) (scopes: read, write), [ApiKeyBearer](#apikeybearer), [asc_auth_key](#asc_auth_key), [Bearer](#bearer), [OpenId](#openid)

#### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

### getBackupProgress

> BackupProgressWrapper getBackupProgress(Dump)

`GET /api/2.0/backup/getbackupprogress`

Get the backup progress

Reports the state of the backup job of the current portal, and is the operation to poll after  &#x60;POST api/2.0/backup/startbackup&#x60;. The queue holds one job per portal, so no job ID is passed in;  &#x60;dump&#x60; asks for the state of the server-wide job instead and requires the space access permission.  When there is no such job - none was ever started, or the finished one has already been dropped from  the queue - the call still answers 200, but the body carries no &#x60;response&#x60; member at all, so a client  has to treat the payload as optional rather than expect an empty object.  While the job runs, &#x60;isCompleted&#x60; is false, &#x60;error&#x60; and &#x60;link&#x60; are empty strings and &#x60;progress&#x60; grows  from 0 to 100. Once it stops, &#x60;isCompleted&#x60; turns true and &#x60;status&#x60; says how it ended: a non-empty  &#x60;error&#x60; is the only report of a failure, &#x60;warning&#x60; is set when the archive was written but some files  could not be read or when the job was cancelled, and &#x60;link&#x60; becomes the download link to the stored  archive.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **Dump** | query | **Boolean** | Applies the operation to the whole server rather than to the current portal, which requires the space  access permission and works on a standalone installation only. Server-wide backups and schedules are  kept apart from the ones of a portal, so the two values address different data. | [optional] [example: false] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The state of the backup job, or an empty payload when there is no such job | [**BackupProgressWrapper**](#model-backupprogresswrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | No permissions to perform this action | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](#model-errorapiresponse) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

#### Return type

[**BackupProgressWrapper**](#model-backupprogresswrapper)

#### Authorization

[Basic](#basic), [OAuth2](#oauth2) (scopes: read, write), [ApiKeyBearer](#apikeybearer), [asc_auth_key](#asc_auth_key), [Bearer](#bearer), [OpenId](#openid)

#### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

### getBackupSchedule

> ScheduleWrapper getBackupSchedule(Dump)

`GET /api/2.0/backup/getbackupschedule`

Get the backup schedule

Returns the backup schedule of the current portal. A portal keeps at most one schedule, so no ID is  passed in, and when none is set the call still answers 200 with a body that carries no &#x60;response&#x60;  member at all. &#x60;dump&#x60; asks for the schedule of the whole server instead of the one of this portal and  requires the space access permission.  The answer cannot be sent back unchanged: &#x60;storageParams&#x60; is returned as an object keyed by parameter  name, while &#x60;POST api/2.0/backup/createbackupschedule&#x60; expects an array of key and value pairs. For  every storage type except &#x60;ThirdPartyConsumer&#x60; the &#x60;folderId&#x60; key of the answer is built from the  stored base path rather than read back from the saved parameters, and a schedule that keeps an  unlimited number of copies reports &#x60;backupsStored&#x60; as null instead of 0.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **Dump** | query | **Boolean** | Applies the operation to the whole server rather than to the current portal, which requires the space  access permission and works on a standalone installation only. Server-wide backups and schedules are  kept apart from the ones of a portal, so the two values address different data. | [optional] [example: false] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The backup schedule, or an empty payload when none is set | [**ScheduleWrapper**](#model-schedulewrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **402** | The portal subscription has expired or has not been paid | - | - |
| **403** | No permissions to perform this action | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](#model-errorapiresponse) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

#### Return type

[**ScheduleWrapper**](#model-schedulewrapper)

#### Authorization

[Basic](#basic), [OAuth2](#oauth2) (scopes: read, write), [ApiKeyBearer](#apikeybearer), [asc_auth_key](#asc_auth_key), [Bearer](#bearer), [OpenId](#openid)

#### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

### getBackupsCount

> Int32Wrapper getBackupsCount(from, to, paid)

`GET /api/2.0/backup/getbackupscount`

Get the number of backups

Counts the backups of the current portal that were created within a period, and &#x60;paid&#x60; chooses which  kind is counted: false, the default, counts the ones covered by the free monthly allowance, and true  counts the ones charged to the portal wallet.  The period defaults to the current calendar month - &#x60;from&#x60; becomes the first day of the month at  00:00 UTC and &#x60;to&#x60; becomes the moment of the call. Both bounds are UTC and inclusive, and a &#x60;from&#x60;  later than &#x60;to&#x60; is rejected. Called with no parameters at all, this returns exactly the figure the  free monthly allowance is measured against.  The count is over history records rather than over stored archives, so it includes backups that have  already been deleted; use &#x60;GET api/2.0/backup/getbackuphistory&#x60; to see what can still be restored.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **from** | query | **Date** (date-time) | The start of the period, in UTC and inclusive. It defaults to the first day of the current calendar  month at 00:00 UTC, and it has to be no later than &#x60;to&#x60;. | [optional] [example: 2026-03-01T00:00:00Z] |
| **to** | query | **Date** (date-time) | The end of the period, in UTC and inclusive. It defaults to the moment of the call. | [optional] [example: 2026-03-31T23:59:59Z] |
| **paid** | query | **Boolean** | Counts the backups charged to the portal wallet when true, and the ones covered by the free monthly  allowance when false, which is the default. It is read only by  &#x60;GET api/2.0/backup/getbackupscount&#x60; and is ignored by  &#x60;GET api/2.0/backup/getbackupscountbypaid&#x60;, which always reports both. | [optional] [example: false] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The number of backups created within the period | [**Int32Wrapper**](#model-int32wrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | The start of the period is later than its end | - | - |
| **403** | No permissions to perform this action | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

#### Return type

[**Int32Wrapper**](#model-int32wrapper)

#### Authorization

[Basic](#basic), [OAuth2](#oauth2) (scopes: read, write), [ApiKeyBearer](#apikeybearer), [asc_auth_key](#asc_auth_key), [Bearer](#bearer), [OpenId](#openid)

#### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

### getBackupsCounts

> BackupsCountResultWrapper getBackupsCounts(from, to, paid)

`GET /api/2.0/backup/getbackupscountbypaid`

Get free and paid backup counts

Counts the backups of the current portal created within a period and splits the result into the ones  covered by the free monthly allowance and the ones charged to the portal wallet, which saves calling  &#x60;GET api/2.0/backup/getbackupscount&#x60; twice.  The &#x60;paid&#x60; query parameter is accepted but not read here: the answer always carries both figures. The  period behaves as it does for &#x60;GET api/2.0/backup/getbackupscount&#x60; - it defaults to the current  calendar month, both bounds are UTC and inclusive, and a &#x60;from&#x60; later than &#x60;to&#x60; is rejected.  The counts are over history records rather than over stored archives, so they include backups that  have already been deleted.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **from** | query | **Date** (date-time) | The start of the period, in UTC and inclusive. It defaults to the first day of the current calendar  month at 00:00 UTC, and it has to be no later than &#x60;to&#x60;. | [optional] [example: 2026-03-01T00:00:00Z] |
| **to** | query | **Date** (date-time) | The end of the period, in UTC and inclusive. It defaults to the moment of the call. | [optional] [example: 2026-03-31T23:59:59Z] |
| **paid** | query | **Boolean** | Counts the backups charged to the portal wallet when true, and the ones covered by the free monthly  allowance when false, which is the default. It is read only by  &#x60;GET api/2.0/backup/getbackupscount&#x60; and is ignored by  &#x60;GET api/2.0/backup/getbackupscountbypaid&#x60;, which always reports both. | [optional] [example: false] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The number of free and of paid backups created within the period | [**BackupsCountResultWrapper**](#model-backupscountresultwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | The start of the period is later than its end | - | - |
| **403** | No permissions to perform this action | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

#### Return type

[**BackupsCountResultWrapper**](#model-backupscountresultwrapper)

#### Authorization

[Basic](#basic), [OAuth2](#oauth2) (scopes: read, write), [ApiKeyBearer](#apikeybearer), [asc_auth_key](#asc_auth_key), [Bearer](#bearer), [OpenId](#openid)

#### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

### getBackupsServiceState

> BackupServiceStateWrapper getBackupsServiceState()

`GET /api/2.0/backup/getservicestate`

Check whether backups are enabled

Reports whether the paid backup service is switched on for the current portal. This is a wallet  setting of the portal, not the health of the backup service or of the worker that runs the jobs, so a  false answer does not mean backups are unavailable and a true one does not mean they are working.  While it is on, backups beyond the free monthly allowance are charged to the portal wallet. While it  is off and that allowance is used up, &#x60;POST api/2.0/backup/startbackup&#x60; and  &#x60;POST api/2.0/backup/createbackupschedule&#x60; answer 402.  Starting a backup once the allowance is used up switches the service on by itself, as soon as a  billing session opens for the portal, so this flag can change without anybody editing the portal  settings.

#### Parameters
This endpoint does not need any parameter.

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Whether the paid backup service is switched on for this portal | [**BackupServiceStateWrapper**](#model-backupservicestatewrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | No permissions to perform this action | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

#### Return type

[**BackupServiceStateWrapper**](#model-backupservicestatewrapper)

#### Authorization

[Basic](#basic), [OAuth2](#oauth2) (scopes: read, write), [ApiKeyBearer](#apikeybearer), [asc_auth_key](#asc_auth_key), [Bearer](#bearer), [OpenId](#openid)

#### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

### getRestoreProgress

> BackupProgressWrapper getRestoreProgress(Dump)

`GET /api/2.0/backup/getrestoreprogress`

Get the restoring progress

Reports the state of the restoring job, and is the operation to poll after  &#x60;POST api/2.0/backup/startrestore&#x60;. It is the only operation of this service that needs no  authorization and the only one that stays reachable while the portal is being restored, which is  exactly the state a client polls it in - every other operation of the service answers 403 then.  &#x60;dump&#x60; is read as three states rather than as a flag: omit it to get whichever restoring job concerns  this portal, including a server-wide one, pass false to get the job of this portal only, and pass true  to get the server-wide job; on a portal that is not a standalone installation the value is forced to  false. When there is no matching job the call still answers 200, but the body carries no &#x60;response&#x60;  member at all.  &#x60;isCompleted&#x60; is the field to poll, a non-empty &#x60;error&#x60; is the only report of a failure, and neither  &#x60;link&#x60; nor &#x60;warning&#x60; is ever filled in for a restoring job.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **Dump** | query | **Boolean** | Which restoring job to look for, read as three states rather than as a flag: leave it out for  whichever job concerns this portal, including a server-wide one, send false for the job of this  portal alone, and send true for the server-wide job. On a portal that is not a standalone  installation the value is forced to false. | [optional] [example: false] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The state of the restoring job, or an empty payload when there is no such job | [**BackupProgressWrapper**](#model-backupprogresswrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **429** | Too Many Requests. | [**ErrorApiResponse**](#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](#model-errorapiresponse) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

#### Return type

[**BackupProgressWrapper**](#model-backupprogresswrapper)

#### Authorization

[cookieAuth](#cookieauth), [bearerAuth](#bearerauth)

#### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

### startBackup

> BackupProgressWrapper startBackup(BackupDto)

`POST /api/2.0/backup/startbackup`

Start the backup

Queues a backup of the current portal and returns straight away: the archive itself is written by the  separate backup worker service, which picks the job up from an integration event, so the response  reports a progress of 0 and the &#x60;Created&#x60; status, and its &#x60;taskId&#x60; is the handle to poll with  &#x60;GET api/2.0/backup/getbackupprogress&#x60;. The caller needs the portal settings permission, and  &#x60;dump&#x60; - a backup of the whole server instead of this one portal - additionally requires the space  access permission and is rejected outside a standalone installation.  The keys expected in &#x60;storageParams&#x60; depend on &#x60;storageType&#x60;: &#x60;Documents&#x60; takes an integer &#x60;folderId&#x60;,  &#x60;ThridpartyDocuments&#x60; takes a provider-specific non-integer &#x60;folderId&#x60;, &#x60;Local&#x60; takes &#x60;filePath&#x60; and  works on a standalone installation only, &#x60;ThirdPartyConsumer&#x60; takes &#x60;module&#x60; together with the settings  of that consumer, and &#x60;DataStore&#x60; takes no keys at all; the &#x60;subdir&#x60; key is added by the operation  itself and must not be sent.  A portal that has already used up the free backups of the current calendar month is charged through the  paid backup service instead, and the call is rejected with 402 when that service is not available to it.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **BackupDto** | body | [**BackupDto**](#model-backupdto) |  | [optional] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The state of the queued backup job | [**BackupProgressWrapper**](#model-backupprogresswrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | The folder ID does not match the storage type, or a dump was requested on a portal that is not a standalone installation | - | - |
| **402** | The free backups of the current month are used up and the paid backup service is not available to this portal | - | - |
| **403** | No permissions to perform this action | - | - |
| **404** | The target folder or the backup quota was not found | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

#### Return type

[**BackupProgressWrapper**](#model-backupprogresswrapper)

#### Authorization

[Basic](#basic), [OAuth2](#oauth2) (scopes: read, write), [ApiKeyBearer](#apikeybearer), [asc_auth_key](#asc_auth_key), [Bearer](#bearer), [OpenId](#openid)

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

### startBackupRestore

> BackupProgressWrapper startBackupRestore(BackupRestoreDto)

`POST /api/2.0/backup/startrestore`

Start the restoring process

Queues the restoring of the current portal from a backup and returns straight away: the work itself is  done by the separate backup worker service, which picks the job up from an integration event, so the  response reports a progress of 0 and the &#x60;Created&#x60; status, and the returned &#x60;taskId&#x60; is the handle to  poll with &#x60;GET api/2.0/backup/getrestoreprogress&#x60; - the one operation of this service that stays  reachable while the portal is being restored, because every other one answers 403 in that state.  The source is given either by &#x60;backupId&#x60;, which is the ID of a record from  &#x60;GET api/2.0/backup/getbackuphistory&#x60;, or, when &#x60;backupId&#x60; is not a GUID, by the &#x60;filePath&#x60; key of  &#x60;storageParams&#x60; together with the matching &#x60;storageType&#x60;; an all-zero GUID is parsed as a GUID and  therefore reaches neither branch.  The caller needs the portal settings permission, restoring has to be allowed by the pricing plan of a  portal that is not a standalone installation, and &#x60;dump&#x60; - restoring the whole server rather than this  one portal - additionally requires the space access permission.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **BackupRestoreDto** | body | [**BackupRestoreDto**](#model-backuprestoredto) |  | [optional] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The state of the queued restoring job | [**BackupProgressWrapper**](#model-backupprogresswrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **402** | The pricing plan of this portal does not allow restoring | - | - |
| **403** | No permissions to perform this action | - | - |
| **404** | The backup record was not found, or the file it points to is missing | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](#model-errorapiresponse) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

#### Return type

[**BackupProgressWrapper**](#model-backupprogresswrapper)

#### Authorization

[Basic](#basic), [OAuth2](#oauth2) (scopes: read, write), [ApiKeyBearer](#apikeybearer), [asc_auth_key](#asc_auth_key), [Bearer](#bearer), [OpenId](#openid)

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json


## Models


### Model BackupDto
The request parameters for starting a backup.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **storageType** | [**BackupStorageType**](#model-backupstoragetype) | The storage the archive is written to. It defaults to &#x60;Documents&#x60;, and it decides which keys  &#x60;storageParams&#x60; has to carry. | [optional] [enum: 0, 1, 2, 3, 4, 5] |
| **storageParams** | [**List**](#model-itemkeyvaluepairobjectobject) | The settings of the chosen storage, as an array of key and value pairs. &#x60;Documents&#x60; needs an integer  &#x60;folderId&#x60;, &#x60;ThridpartyDocuments&#x60; a provider-specific non-integer &#x60;folderId&#x60;, &#x60;Local&#x60; a &#x60;filePath&#x60;,  &#x60;ThirdPartyConsumer&#x60; a &#x60;module&#x60; plus the settings of that consumer, and &#x60;DataStore&#x60; none. The  &#x60;subdir&#x60; key is added by the operation itself and must not be sent. | [optional] [example: [{key=folderId, value=1234}]] [nullable] |
| **dump** | **Boolean** | Backs up the whole server rather than this one portal. It requires the space access permission and  works on a standalone installation only. | [optional] [example: false] |


### Model BackupHistoryRecord
One stored backup of a portal.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **id** | **UUID** (uuid) | The ID of the backup, which is the same value as the &#x60;taskId&#x60; the backup was started with. Pass it to  &#x60;DELETE api/2.0/backup/deletebackup/{id}&#x60; or as the &#x60;backupId&#x60; of  &#x60;POST api/2.0/backup/startrestore&#x60;. | [required] [example: 11111111-1111-1111-1111-111111111111] |
| **fileName** | **String** | The name of the stored archive. It is built from the portal alias and the moment the backup started,  or from &#x60;workspace&#x60; instead of the alias for a backup of the whole server. | [required] [example: myportal_2026-03-01_02-15-00.tar.gz] [nullable] |
| **storageType** | [**BackupStorageType**](#model-backupstoragetype) | The storage the archive was written to, reported as a number rather than as a name. | [required] [enum: 0, 1, 2, 3, 4, 5] |
| **createdOn** | **Date** (date-time) | The date and time the backup was stored at, in UTC. | [required] [example: 2026-03-01T02:15:00Z] |
| **expiresOn** | **Date** (date-time) | The date and time a background cleaner removes this backup at. Only a backup written to &#x60;DataStore&#x60;  expires, one day after it was stored; for every other storage type this is &#x60;0001-01-01T00:00:00&#x60;,  which means the backup is kept until it is deleted by hand or pushed out by the stored-copies limit  of a schedule. | [required] [example: 0001-01-01T00:00:00Z] |


### Model BackupHistoryRecordArrayWrapper
The successful API response containing the list of BackupHistoryRecord objects.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **response** | [**List**](#model-backuphistoryrecord) | The list of BackupHistoryRecord objects returned by the operation. | [optional] |
| **count** | **Integer** (int32) | The total number of items in the response | [optional] |
| **links** | [**List**](#model-backuphistoryrecordarraywrapperlinks-item) | List of links related to the response | [optional] |
| **status** | **Integer** (int32) | HTTP status code of the response | [optional] |
| **statusCode** | **Integer** (int32) | HTTP status code of the response (duplicate of status) | [optional] |


### Model BackupHistoryRecordArrayWrapper.links item

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **href** | **String** | URL of the link | [optional] |
| **action** | **String** | Action associated with the link | [optional] |


### Model BackupPeriod

Possible values:

- `0` — Every day (`EveryDay`)
- `1` — Every week (`EveryWeek`)
- `2` — Every month (`EveryMonth`)


### Model BackupProgress
The state of one backup or restoring job.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **isCompleted** | **Boolean** | Specifies whether the job has stopped running. This is the field to poll: true means the job will not  change any more, whether it succeeded, failed or was cancelled, and &#x60;status&#x60; tells which of the three  it is. | [optional] [example: false] |
| **progress** | **Integer** (int32) | The share of the job that is already done, from 0 to 100. A job that has only been queued reports 0,  because the work starts when a separate worker service picks it up. | [optional] [example: 50] |
| **error** | **String** | The message of the error that stopped the job. It is an empty string, not null, while the job runs  and after a job that succeeded, so the sign of a failure is a non-empty value - and this is the only  place where the reason is reported. | [optional] [example: An error occurred during processing] [nullable] |
| **warning** | **String** | A message about a job that stopped without failing: it names the entry inside the archive that lists  the files which could not be read, when a backup finished without some of them, and it says so when  the job was cancelled. It is an empty string otherwise, and it is only ever filled in for a backup  job - a cancelled restoring job leaves it empty. | [optional] [example: Some files were not included in the backup. For more details, please check storage/missing_info] [nullable] |
| **link** | **String** | The link to download the stored archive. It is an empty string until the archive has been uploaded,  and it is only ever filled in for a backup job, never for a restoring one. | [optional] [example: https://example.com/products/files/httphandlers/filehandler.ashx?action=download&fileid=1234] [nullable] |
| **tenantId** | **Integer** (int32) | The ID of the portal the job belongs to, or -1 for a job that covers the whole server. | [optional] [example: 1] |
| **backupProgressEnum** | [**BackupProgressEnum**](#model-backupprogressenum) | Whether this is a backup or a restoring job, reported as a number rather than as a name. | [optional] [enum: 0, 1, 2] |
| **status** | [**DistributedTaskStatus**](#model-distributedtaskstatus) | The state of the job: &#x60;Created&#x60; while it waits for a worker to pick it up, &#x60;Running&#x60; while it works,  &#x60;Completed&#x60; once it has finished on its own, &#x60;Canceled&#x60; after it was cancelled, and &#x60;Failted&#x60; when it  stopped on an error, in which case &#x60;error&#x60; carries the reason. Reported as a number rather than as a  name. | [optional] [enum: 0, 1, 2, 3, 4] |
| **taskId** | **String** | The ID of the job. It is the handle to poll this operation with, and for a backup job it also becomes  the &#x60;id&#x60; of the record in &#x60;GET api/2.0/backup/getbackuphistory&#x60;. | [optional] [example: 11111111-1111-1111-1111-111111111111] [nullable] |


### Model BackupProgressEnum

Possible values:

- `0` — Backup (`Backup`)
- `1` — Restore (`Restore`)
- `2` — Transfer (`Transfer`)


### Model BackupProgressWrapper
The successful API response containing the BackupProgress object.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **response** | [**BackupProgress**](#model-backupprogress) | The BackupProgress object returned by the operation. | [optional] |
| **count** | **Integer** (int32) | The total number of items in the response | [optional] |
| **links** | [**List**](#model-backuphistoryrecordarraywrapperlinks-item) | List of links related to the response | [optional] |
| **status** | **Integer** (int32) | HTTP status code of the response | [optional] |
| **statusCode** | **Integer** (int32) | HTTP status code of the response (duplicate of status) | [optional] |


### Model BackupRestoreDto
The request parameters for restoring a portal from a backup.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **backupId** | **String** | The ID of the backup to restore from, as listed by &#x60;GET api/2.0/backup/getbackuphistory&#x60;. Send  anything that is not a GUID to restore from a file given by &#x60;storageParams&#x60; instead; an all-zero GUID  selects neither, because it parses as a GUID and then matches no record. | [required] [example: 11111111-1111-1111-1111-111111111111] [nullable] |
| **storageType** | [**BackupStorageType**](#model-backupstoragetype) | The storage the archive is read from. It defaults to &#x60;Documents&#x60; and is only used when &#x60;backupId&#x60; is  not a GUID, because a known backup carries the storage of its own record. | [optional] [enum: 0, 1, 2, 3, 4, 5] |
| **storageParams** | [**List**](#model-itemkeyvaluepairobjectobject) | The location of the archive, as an array of key and value pairs. The key read here is &#x60;filePath&#x60; -  not the &#x60;folderId&#x60; a backup is started with - and it holds a file ID for &#x60;Documents&#x60;, a  provider-specific file ID for &#x60;ThridpartyDocuments&#x60; and a path on the server for &#x60;Local&#x60;. It is only  used when &#x60;backupId&#x60; is not a GUID. | [optional] [example: [{key=filePath, value=1234}]] [nullable] |
| **notify** | **Boolean** | Chooses who is emailed when the restoring starts and when it finishes: every active user of the  portal when true, and its owner alone when false. Mail goes only to accounts that have been  activated, so this decides the audience rather than whether anybody is notified at all. | [optional] [example: true] |
| **dump** | **Boolean** | Restores the whole server rather than this one portal. It requires the space access permission. | [optional] [example: false] |


### Model BackupScheduleDto
The request parameters for setting the backup schedule.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **storageType** | [**BackupStorageType**](#model-backupstoragetype) | The storage the scheduled archives are written to. It defaults to &#x60;Documents&#x60;, and it decides which  keys &#x60;storageParams&#x60; has to carry. | [optional] [enum: 0, 1, 2, 3, 4, 5] |
| **storageParams** | [**List**](#model-itemkeyvaluepairobjectobject) | The settings of the chosen storage, as an array of key and value pairs. &#x60;Documents&#x60; and  &#x60;ThridpartyDocuments&#x60; need &#x60;folderId&#x60;, &#x60;Local&#x60; needs &#x60;filePath&#x60;, &#x60;ThirdPartyConsumer&#x60; needs &#x60;module&#x60;  plus the settings of that consumer, and &#x60;DataStore&#x60; needs none. | [optional] [example: [{key=folderId, value=1234}]] [nullable] |
| **backupsStored** | **Integer** (int32) | The number of scheduled copies to keep, from 1 to 30. It defaults to 1, and only the copies this  schedule creates are counted and removed - archives started by hand are left alone. | [optional] [example: 5] [nullable] |
| **cronParams** | [**Cron**](#model-cron) | When the backup runs. It is required: a request without it fails rather than falling back to a  default. | [optional] |
| **dump** | **Boolean** | Schedules a backup of the whole server rather than of this one portal. It requires the space access  permission and works on a standalone installation only. | [optional] [example: false] |


### Model BackupServiceStateDto
Whether the paid backup service is switched on for a portal.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **enabled** | **Boolean** | Specifies whether the paid backup service is switched on for this portal, which is a setting of its  wallet rather than the health of the backup service. While it is true, backups beyond the free  monthly allowance are charged to the wallet. | [optional] [example: true] |


### Model BackupServiceStateWrapper
The successful API response containing the BackupServiceStateDto object.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **response** | [**BackupServiceStateDto**](#model-backupservicestatedto) | The BackupServiceStateDto object returned by the operation. | [optional] |
| **count** | **Integer** (int32) | The total number of items in the response | [optional] |
| **links** | [**List**](#model-backuphistoryrecordarraywrapperlinks-item) | List of links related to the response | [optional] |
| **status** | **Integer** (int32) | HTTP status code of the response | [optional] |
| **statusCode** | **Integer** (int32) | HTTP status code of the response (duplicate of status) | [optional] |


### Model BackupStorageType

Possible values:

- `0` — Documents (`Documents`)
- `1` — Thridparty documents (`ThridpartyDocuments`)
- `2` — Custom cloud (`CustomCloud`)
- `3` — Local (`Local`)
- `4` — Data store (`DataStore`)
- `5` — Thirdparty consumer (`ThirdPartyConsumer`)


### Model BackupsCountResultDto
The backups of a portal, split by who paid for them.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **free** | **Integer** (int32) | The number of backups covered by the free monthly allowance. | [optional] [example: 3] |
| **paid** | **Integer** (int32) | The number of backups charged to the portal wallet. | [optional] [example: 5] |


### Model BackupsCountResultWrapper
The successful API response containing the BackupsCountResultDto object.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **response** | [**BackupsCountResultDto**](#model-backupscountresultdto) | The BackupsCountResultDto object returned by the operation. | [optional] |
| **count** | **Integer** (int32) | The total number of items in the response | [optional] |
| **links** | [**List**](#model-backuphistoryrecordarraywrapperlinks-item) | List of links related to the response | [optional] |
| **status** | **Integer** (int32) | HTTP status code of the response | [optional] |
| **statusCode** | **Integer** (int32) | HTTP status code of the response (duplicate of status) | [optional] |


### Model BooleanWrapper
The successful API response containing the boolean value.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **response** | **Boolean** | The boolean value returned by the operation. | [optional] |
| **count** | **Integer** (int32) | The total number of items in the response | [optional] |
| **links** | [**List**](#model-backuphistoryrecordarraywrapperlinks-item) | List of links related to the response | [optional] |
| **status** | **Integer** (int32) | HTTP status code of the response | [optional] |
| **statusCode** | **Integer** (int32) | HTTP status code of the response (duplicate of status) | [optional] |


### Model Cron
The request parameters for the time the scheduled backup runs.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **period** | [**BackupPeriod**](#model-backupperiod) | How often the backup runs: &#x60;EveryDay&#x60;, &#x60;EveryWeek&#x60; or &#x60;EveryMonth&#x60;. It defaults to &#x60;EveryDay&#x60;. | [optional] [enum: 0, 1, 2] |
| **hour** | **Integer** (int32) | The hour of the day the backup starts at, from 0 to 23. Minutes cannot be chosen - it always starts  on the hour. | [optional] [example: 2] |
| **day** | **Integer** (int32) | The day the backup runs on: the day of the week from 1 to 7, Sunday being 1, for &#x60;EveryWeek&#x60;, and the  day of the month from 1 to 31 for &#x60;EveryMonth&#x60;. Leave it out for &#x60;EveryDay&#x60; only - an omitted value is  stored as 0, which neither of the other two periods accepts, so a weekly or monthly schedule sent  without it fails. | [optional] [example: 1] [nullable] |


### Model CronParams
The time a scheduled backup runs at.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **period** | [**BackupPeriod**](#model-backupperiod) | How often the backup runs: 0 for every day, 1 for every week and 2 for every month. | [optional] [enum: 0, 1, 2] |
| **hour** | **Integer** (int32) | The hour of the day the backup starts at, from 0 to 23. | [optional] [example: 2] |
| **day** | **Integer** (int32) | The day the backup runs on: the day of the week from 1 to 7, Sunday being 1, for a weekly schedule,  and the day of the month from 1 to 31 for a monthly one. It is 0 for a daily schedule. | [optional] [example: 1] |


### Model DistributedTaskStatus

Possible values:

- `0` — Created (`Created`)
- `1` — Running (`Running`)
- `2` — Completed (`Completed`)
- `3` — Canceled (`Canceled`)
- `4` — Failted (`Failted`)


### Model ErrorApiResponse
The error body returned with every failed request.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **status** | **Integer** (int32) | The response status flag. Always 1 on an error, as opposed to 0 on success. | [optional] |
| **statusCode** | **Integer** (int32) | The HTTP status code of the response, repeated in the body. | [optional] |
| **error** | [**ErrorApiResponse_error**](#model-errorapiresponseerror) |  | [optional] |


### Model ErrorApiResponse.error
What went wrong.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **message** | **String** | The human-readable error message. | [optional] |
| **type** | **String** | The .NET type of the underlying exception. Only sent when stack traces are enabled. | [optional] |
| **stack** | **String** | The stack trace of the underlying exception. Only sent when stack traces are enabled. | [optional] |
| **hresult** | **Integer** (int32) | The HRESULT of the underlying exception. Only sent when stack traces are enabled. | [optional] |


### Model FieldError
Field specific validation error

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **field** | **String** | The name of the field that failed validation | [optional] [example: policy_url] |
| **code** | **String** | Error code for localization purposes | [optional] [example: InvalidPolicyUrl] |
| **message** | **String** | Human readable error message | [optional] [example: policy url is expected to be passed as url] |


### Model Int32Wrapper
The successful API response containing the int32 value.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **response** | **Integer** | The int32 value returned by the operation. | [optional] |
| **count** | **Integer** (int32) | The total number of items in the response | [optional] |
| **links** | [**List**](#model-backuphistoryrecordarraywrapperlinks-item) | List of links related to the response | [optional] |
| **status** | **Integer** (int32) | HTTP status code of the response | [optional] |
| **statusCode** | **Integer** (int32) | HTTP status code of the response (duplicate of status) | [optional] |


### Model ItemKeyValuePairObjectObject
One entry of a keyed collection, carried as an explicit pair of &#x60;key&#x60; and &#x60;value&#x60; fields instead of as a member  of a JSON object, so that the key is not restricted to a string and the entries keep the order they are sent in.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **key** | **oas_any_type_not_mapped** |  | [optional] [nullable] |
| **value** | **oas_any_type_not_mapped** |  | [optional] [nullable] |


### Model ProblemDetail
RFC 7807 problem details returned by the registration API for failed requests.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **type** | **URI** (uri) | A URI reference that identifies the problem type. This service sets it to the DocSpace API getting-started page. | [optional] |
| **title** | **String** | A short, human-readable summary of the problem type, typically the HTTP status reason phrase. | [optional] |
| **status** | **Integer** (int32) | The HTTP status code for this occurrence of the problem. | [optional] |
| **detail** | **String** | A human-readable explanation specific to this occurrence of the problem. | [optional] |
| **instance** | **URI** (uri) | A URI reference that identifies the specific occurrence, set to the request path. | [optional] |
| **properties** | **Map** | Extension members carried on the problem. Usually empty; validation failures also surface as the top-level errors array. | [optional] |
| **errors** | [**List**](#model-fielderror) | Field-specific validation errors. Present when the request body or parameters failed validation, or when a named scope is not in the tenant catalogue. | [optional] |


### Model ScheduleDto
The backup schedule of a portal.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **storageType** | [**BackupStorageType**](#model-backupstoragetype) | The storage the scheduled archives are written to, reported as a number rather than as the name the  schedule was created with. | [required] [enum: 0, 1, 2, 3, 4, 5] |
| **storageParams** | **Map** | The settings of the storage, as an object keyed by parameter name - not as the array of key and value  pairs the schedule was created with, so it cannot be sent back unchanged. For every storage type  except &#x60;ThirdPartyConsumer&#x60; the &#x60;folderId&#x60; key is built from the stored base path. | [required] [example: {folderId=1234}] |
| **cronParams** | [**CronParams**](#model-cronparams) | When the backup runs, read back from the stored cron expression. &#x60;day&#x60; is 0 for a daily schedule,  because a daily one has no day. | [required] |
| **backupsStored** | **Integer** (int32) | The number of scheduled copies kept. It is null, not 0, when the schedule keeps an unlimited number. | [optional] [example: 5] [nullable] |
| **lastBackupTime** | **Date** (date-time) | The date and time the schedule last ran at. It is &#x60;0001-01-01T00:00:00&#x60; until the schedule has run  for the first time. | [required] [example: 2026-01-01T00:00:00Z] |
| **dump** | **Boolean** | Specifies whether this schedule backs up the whole server instead of one portal. | [required] [example: false] |


### Model ScheduleWrapper
The successful API response containing the ScheduleDto object.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **response** | [**ScheduleDto**](#model-scheduledto) | The ScheduleDto object returned by the operation. | [optional] |
| **count** | **Integer** (int32) | The total number of items in the response | [optional] |
| **links** | [**List**](#model-backuphistoryrecordarraywrapperlinks-item) | List of links related to the response | [optional] |
| **status** | **Integer** (int32) | HTTP status code of the response | [optional] |
| **statusCode** | **Integer** (int32) | HTTP status code of the response (duplicate of status) | [optional] |


## Authorization


### cookieAuth
- **Type**: API key
- **API key parameter name**: asc_auth_key
- **Location**: 


### bearerAuth

- **Type**: HTTP Bearer Token authentication


### asc_auth_key
- **Type**: API key
- **API key parameter name**: asc_auth_key
- **Location**: 


### Basic

- **Type**: HTTP basic authentication


### Bearer

- **Type**: HTTP Bearer Token authentication (JWT)


### ApiKeyBearer
- **Type**: API key
- **API key parameter name**: ApiKeyBearer
- **Location**: HTTP header


### OAuth2

- **Type**: OAuth
- **Flow**: accessCode
- **Authorization URL**: 
- **Scopes**: 
  - read: Read access to protected resources
  - write: Write access to protected resources


### OpenId


### x-signature
- **Type**: API key
- **API key parameter name**: x-signature
- **Location**: 

