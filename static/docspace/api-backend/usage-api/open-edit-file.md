# openEditFile

Referenced types are defined in the [full reference](../files.md).

> ConfigurationIntegerWrapper openEditFile(fileId, version, view, editorType, edit, fill)

`GET /api/2.0/files/file/{fileId}/openedit`

Open a file configuration

Returns the initialization configuration of a file to open it in the editor.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **fileId** | path | **Integer** (int32) | The file ID to open. | [required] [example: 1] |
| **version** | query | **Integer** (int32) | The file version to open. | [optional] [example: 1] |
| **view** | query | **Boolean** | Specifies if the document will be opened for viewing only or not. | [optional] [example: false] |
| **editorType** | query | **EditorType** | The editor type to open the file. | [optional] [example: 1] [enum: 0, 1, 2] |
| **edit** | query | **Boolean** | Specifies if the document is opened in the editing mode or not. | [optional] [example: false] |
| **fill** | query | **Boolean** | Specifies if the document is opened in the form-filling mode or not. | [optional] [example: false] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Configuration parameters | [**ConfigurationIntegerWrapper**](../files.md#model-configurationintegerwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | You don&#39;t have enough permission to view the file | - | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**ConfigurationIntegerWrapper**](../files.md#model-configurationintegerwrapper)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
