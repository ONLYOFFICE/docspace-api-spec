# createFile

Referenced types are defined in the [full reference](../files.md).

> FileWrapper createFile(folderId, CreateFileJsonElement)

`POST /api/2.0/files/{folderId}/file`

Create a file

Creates a file in the folder named in the route and answers with the stored file. The extension in the title  decides the format: an extension of a known text, spreadsheet or presentation format is rewritten to the  portal&#39;s own DOCX, XLSX or PPTX, a title with no extension at all gets DOCX added, while an unknown extension  and the few formats the portal keeps as they are stay untouched; &#x60;enableExternalExt&#x3D;true&#x60; stores the title  verbatim and skips that rewriting. The content comes from one of three sources, tried in this order: &#x60;formId&#x60;  copies a ready form out of the form gallery, &#x60;templateId&#x60; copies an existing file the caller can read - a  number for a file in the portal, a string for one in a connected third-party storage - and with neither of  them the portal&#39;s blank template for that format and the caller&#39;s language is used. The caller needs the right  to create files in the folder, and the room roots, Archive and the template sections are refused even to an  admin. The call is mutating and not idempotent. To create the file in the caller&#39;s own section use  &#x60;POST api/2.0/files/@my/file&#x60;.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **folderId** | path | **Integer** (int32) | The folder the file is created in. | [required] [example: 1] |
| **CreateFileJsonElement** | body | [**CreateFileJsonElement**](../files.md#model-createfilejsonelement) | The title of the new file and the source of its content. | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The created file | [**FileWrapper**](../files.md#model-filewrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **401** | Unauthorized | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**FileWrapper**](../files.md#model-filewrapper)

## Third-party storage

For a file or folder in a connected third-party storage the identifier is a string such as `sbox-42`, and the call differs in these parts only:

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **folderId** | path | **String** | The folder the file is created in. | [required] [example: 1] |

Return type: [**ThirdPartyFileWrapper**](../files.md#model-thirdpartyfilewrapper)

## Authorization

[Basic](../files.md#basic), [OAuth2](../files.md#oauth2) (scopes: read, write), [ApiKeyBearer](../files.md#apikeybearer), [asc_auth_key](../files.md#asc_auth_key), [Bearer](../files.md#bearer), [OpenId](../files.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
