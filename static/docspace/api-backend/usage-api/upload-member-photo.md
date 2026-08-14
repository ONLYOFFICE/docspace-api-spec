# uploadMemberPhoto

Referenced types are defined in the [full reference](../people.md).

> FileUploadResultWrapper uploadMemberPhoto(userid, File, Autosave)

`POST /api/2.0/people/{userid}/photo`

Upload a user photo

Uploads a photo of the user with the ID specified in the request.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **userid** | path | **String** | The user ID. | [required] [example: 00000000-0000-0000-0000-000000000000] |
| **File** | form | **File** (binary) | The image data. | [required] |
| **Autosave** | form | **Boolean** | Specifies whether to autosave a photo or not. | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Result of file uploading | [**FileUploadResultWrapper**](../people.md#model-fileuploadresultwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | The uploaded file could not be found | - | - |
| **403** | No permissions to perform this action | - | - |
| **413** | Image size is too large | - | - |
| **415** | Unknown image file type | - | - |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**FileUploadResultWrapper**](../people.md#model-fileuploadresultwrapper)

## Authorization

[Basic](../people.md#basic), [OAuth2](../people.md#oauth2) (scopes: read, write), [ApiKeyBearer](../people.md#apikeybearer) (scopes: read, write), [asc_auth_key](../people.md#asc_auth_key) (scopes: read, write), [Bearer](../people.md#bearer), [OpenId](../people.md#openid)

## HTTP request headers

- **Content-Type**: multipart/form-data
- **Accept**: application/json

## PeopleProfilesApi
