# restoreFileVersion

Referenced types are defined in the [full reference](../files.md).

> EditHistoryArrayWrapper restoreFileVersion(fileId, version, url)

`POST /api/2.0/files/file/{fileId}/restoreversion`

Restore a file version

Restores a file version specified in the request.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **fileId** | path | **Integer** (int32) | The file ID of the restore version. | [required] [example: 1] |
| **version** | query | **Integer** (int32) | The file version of the restore. | [optional] [example: 1] |
| **url** | query | **String** | The file version URL of the restore. | [optional] [example: https://example.com] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Version history data: file ID, key, file version, version group, a user who updated a file, creation time, history changes in the string format, list of history changes, server version | [**EditHistoryArrayWrapper**](../files.md#model-edithistoryarraywrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | No file id or folder id toFolderId determine provider | - | - |
| **403** | You do not have enough permissions to edit the file | - | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**EditHistoryArrayWrapper**](../files.md#model-edithistoryarraywrapper)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
