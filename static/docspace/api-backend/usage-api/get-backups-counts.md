# getBackupsCounts

Referenced types are defined in the [full reference](../backup.md).

> BackupsCountResultWrapper getBackupsCounts(from, to, paid)

`GET /api/2.0/backup/getbackupscountbypaid`

Get the number of free and paid backups

Returns the number of free and paid backups for a period of time. The default is the current calendar month.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **from** | query | **Date** (date-time) | The from date. | [optional] [example: 2025-01-01T00:00:00Z] |
| **to** | query | **Date** (date-time) | The to date. | [optional] [example: 2025-12-31T23:59:59Z] |
| **paid** | query | **Boolean** | Specifies if the backups are paid or not. | [optional] [example: false] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Number of free and paid backups | [**BackupsCountResultWrapper**](../backup.md#model-backupscountresultwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | From date must be less than to date | - | - |
| **403** | Access denied | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../backup.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../backup.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../backup.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**BackupsCountResultWrapper**](../backup.md#model-backupscountresultwrapper)

## Authorization

[Basic](../backup.md#basic), [OAuth2](../backup.md#oauth2) (scopes: read, write), [ApiKeyBearer](../backup.md#apikeybearer), [asc_auth_key](../backup.md#asc_auth_key), [Bearer](../backup.md#bearer), [OpenId](../backup.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
