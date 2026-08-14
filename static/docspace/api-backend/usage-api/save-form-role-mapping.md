# saveFormRoleMapping

Referenced types are defined in the [full reference](../files.md).

> saveFormRoleMapping(fileId, SaveFormRoleMappingDtoInteger)

`POST /api/2.0/files/file/{fileId}/formrolemapping`

Save form role mapping

Saves the form role mapping.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **fileId** | path | **String** |  | [required] |
| **SaveFormRoleMappingDtoInteger** | body | [**SaveFormRoleMappingDtoInteger**](../files.md#model-saveformrolemappingdtointeger) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Updated information about form role mappings | - | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | You do not have enough permissions to edit the file | - | - |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

null (empty response body)

## Authorization

[Basic](../files.md#basic), [OAuth2](../files.md#oauth2) (scopes: read, write), [ApiKeyBearer](../files.md#apikeybearer) (scopes: read, write), [asc_auth_key](../files.md#asc_auth_key) (scopes: read, write), [Bearer](../files.md#bearer), [OpenId](../files.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: Not defined
