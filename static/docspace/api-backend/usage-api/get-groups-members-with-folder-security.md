# getGroupsMembersWithFolderSecurity

Referenced types are defined in the [full reference](../files.md).

> GroupMemberSecurityRequestArrayWrapper getGroupsMembersWithFolderSecurity(folderId, groupId, count, startIndex, filterValue)

`GET /api/2.0/files/folder/{folderId}/group/{groupId}/share`

Get folder group members with security information

Returns the group members with their folder security information.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **folderId** | path | **Integer** (int32) | The folder ID. | [required] [example: 1] |
| **groupId** | path | **UUID** (uuid) | The group ID. | [required] [example: 00000000-0000-0000-0000-000000000000] |
| **count** | query | **Integer** (int32) | The number of items to be retrieved in the current query. | [optional] [example: 25] [min: 1] [max: 100] |
| **startIndex** | query | **Integer** (int32) | The starting index for the query result set. | [optional] [example: 0] |
| **filterValue** | query | **String** | The filter value used for searching or querying group members based on text input. | [optional] [example: My Document] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Ok | [**GroupMemberSecurityRequestArrayWrapper**](../files.md#model-groupmembersecurityrequestarraywrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**GroupMemberSecurityRequestArrayWrapper**](../files.md#model-groupmembersecurityrequestarraywrapper)

## Authorization

[Basic](../files.md#basic), [OAuth2](../files.md#oauth2) (scopes: read, write), [ApiKeyBearer](../files.md#apikeybearer) (scopes: read, write), [asc_auth_key](../files.md#asc_auth_key) (scopes: read, write), [Bearer](../files.md#bearer), [OpenId](../files.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
