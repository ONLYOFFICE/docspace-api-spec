# uploadDefaultTemplate

Referenced types are defined in the [full reference](../files.md).

> DefaultTemplateSettingsWrapper uploadDefaultTemplate(FileExtension, File)

`POST /api/2.0/files/settings/defaulttemplate`

Upload a file as the default template setting

Uploads a file to use as the default template setting.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **FileExtension** | query | **String** | File extension of a template to replace | [required] [example: .docx] |
| **File** | form | **File** (binary) | File to replace template with | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | New default template settings | [**DefaultTemplateSettingsWrapper**](../files.md#model-defaulttemplatesettingswrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | Incorrect or missing file | - | - |
| **403** | You don&#39;t have enough permission to perform the operation | - | - |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**DefaultTemplateSettingsWrapper**](../files.md#model-defaulttemplatesettingswrapper)

## Authorization

[Basic](../files.md#basic), [OAuth2](../files.md#oauth2) (scopes: read, write), [ApiKeyBearer](../files.md#apikeybearer) (scopes: read, write), [asc_auth_key](../files.md#asc_auth_key) (scopes: read, write), [Bearer](../files.md#bearer), [OpenId](../files.md#openid)

## HTTP request headers

- **Content-Type**: multipart/form-data
- **Accept**: application/json

## FilesSharingApi
