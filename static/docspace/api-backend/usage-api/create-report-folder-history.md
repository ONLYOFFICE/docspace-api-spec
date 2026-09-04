# createReportFolderHistory

Referenced types are defined in the [full reference](../files.md).

> DocumentBuilderTaskWrapper createReportFolderHistory(folderId, format, from, to)

`POST /api/2.0/files/folder/{folderId}/log/report`

Start the folder history report generation

Starts generating the activity history report of a folder (XLSX by default, or CSV) and saves it to My documents.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **folderId** | path | **Integer** (int32) | The folder ID whose history is exported. | [required] [example: 1] |
| **format** | query | **AuditReportFormat** | The output file format of the report. Defaults to XLSX. | [optional] [example: Xlsx] [enum: 0, 1] |
| **from** | query | **Date** (date-time) | The start date of the history period to export. | [optional] [example: 2025-01-01T00:00:00] |
| **to** | query | **Date** (date-time) | The end date of the history period to export. | [optional] [example: 2025-12-31T23:59:59] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Operation execution status | [**DocumentBuilderTaskWrapper**](../files.md#model-documentbuildertaskwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | You don&#39;t have enough permission to perform the operation | - | - |
| **404** | The required folder was not found | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**DocumentBuilderTaskWrapper**](../files.md#model-documentbuildertaskwrapper)

## Authorization

[Basic](../files.md#basic), [OAuth2](../files.md#oauth2) (scopes: read, write), [ApiKeyBearer](../files.md#apikeybearer), [asc_auth_key](../files.md#asc_auth_key), [Bearer](../files.md#bearer), [OpenId](../files.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
