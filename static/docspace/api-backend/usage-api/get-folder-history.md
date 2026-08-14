# getFolderHistory

Referenced types are defined in the [full reference](../files.md).

> HistoryArrayWrapper getFolderHistory(folderId, fromDate, toDate, count, startIndex)

`GET /api/2.0/files/folder/{folderId}/log`

Get folder history

Returns the activity history of a folder with a specified identifier.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **folderId** | path | **Integer** (int32) | The folder ID of the history request. | [required] [example: 1] |
| **fromDate** | query | **ApiDateTime** | The start date of the history request. | [optional] [example: 2025-01-01T00:00:00.0000000Z] |
| **toDate** | query | **ApiDateTime** | The end date of the history request. | [optional] [example: 2025-12-31T23:59:59.0000000Z] |
| **count** | query | **Integer** (int32) | The number of records to retrieve for the folder history. | [optional] [example: 25] [min: 1] [max: 100] |
| **startIndex** | query | **Integer** (int32) | The starting index from which the history records are retrieved in the request. | [optional] [example: 0] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | List of actions in the folder | [**HistoryArrayWrapper**](../files.md#model-historyarraywrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | You don&#39;t have enough permission to perform the operation | - | - |
| **404** | The required folder was not found | - | - |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**HistoryArrayWrapper**](../files.md#model-historyarraywrapper)

## Authorization

[Basic](../files.md#basic), [OAuth2](../files.md#oauth2) (scopes: read, write), [ApiKeyBearer](../files.md#apikeybearer) (scopes: read, write), [asc_auth_key](../files.md#asc_auth_key) (scopes: read, write), [Bearer](../files.md#bearer), [OpenId](../files.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
