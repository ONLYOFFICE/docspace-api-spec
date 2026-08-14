# sendEditorNotify

Referenced types are defined in the [full reference](../files.md).

> AceShortWrapperArrayWrapper sendEditorNotify(fileId, MentionMessageWrapper)

`POST /api/2.0/files/file/{fileId}/sendeditornotify`

Send the mention message

Sends a message to the users who are mentioned in the file with the ID specified in the request.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **fileId** | path | **Integer** (int32) | The file ID with the mention message. | [required] [example: file-id] |
| **MentionMessageWrapper** | body | [**MentionMessageWrapper**](../files.md#model-mentionmessagewrapper) | The mention message. | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | List of access rights information | [**AceShortWrapperArrayWrapper**](../files.md#model-aceshortwrapperarraywrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | The list of email addresses is empty | - | - |
| **403** | You don&#39;t have enough permission to perform the operation | - | - |
| **404** | The required file was not found | - | - |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**AceShortWrapperArrayWrapper**](../files.md#model-aceshortwrapperarraywrapper)

## Authorization

[Basic](../files.md#basic), [OAuth2](../files.md#oauth2) (scopes: read, write), [ApiKeyBearer](../files.md#apikeybearer) (scopes: read, write), [asc_auth_key](../files.md#asc_auth_key) (scopes: read, write), [Bearer](../files.md#bearer), [OpenId](../files.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
