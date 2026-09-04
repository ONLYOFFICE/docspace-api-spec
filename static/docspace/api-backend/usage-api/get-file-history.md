# getFileHistory

Referenced types are defined in the [full reference](../files.md).

> HistoryArrayWrapper getFileHistory(fileId, fromDate, toDate, count, startIndex)

`GET /api/2.0/files/file/{fileId}/log`

Get file history

Returns the list of actions performed on the file with the specified identifier.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **fileId** | path | **Integer** (int32) | The file ID of the history request. | [required] [example: 1] |
| **fromDate** | query | **Date** (date-time) | The start date of the history. | [optional] [example: 2025-01-01T00:00:00.0000000Z] |
| **toDate** | query | **Date** (date-time) | The end date of the history. | [optional] [example: 2025-12-31T23:59:59.0000000Z] |
| **count** | query | **Integer** (int32) | The number of history entries to retrieve for the file log. | [optional] [example: 25] [min: 1] [max: 100] |
| **startIndex** | query | **Integer** (int32) | The starting index for retrieving a subset of file history entries. | [optional] [example: 0] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | List of actions performed on the file | [**HistoryArrayWrapper**](../files.md#model-historyarraywrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | You don&#39;t have enough permission to perform the operation | - | - |
| **404** | The required file was not found | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**HistoryArrayWrapper**](../files.md#model-historyarraywrapper)

## Authorization

[Basic](../files.md#basic), [OAuth2](../files.md#oauth2) (scopes: read, write), [ApiKeyBearer](../files.md#apikeybearer), [asc_auth_key](../files.md#asc_auth_key), [Bearer](../files.md#bearer), [OpenId](../files.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
