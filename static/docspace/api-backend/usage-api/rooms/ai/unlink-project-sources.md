# unlinkProjectSources

> unlinkProjectSources(id, UnlinkAiProjectSourcesRequest)

`DELETE /api/2.0/files/rooms/{id}/sources`

Unlink sources from an AI project

Unlinks Instructions and Knowledge rooms from an AI project; project members lose the access the link gave them. The caller must manage the project, rights on the rooms are not checked; the rooms themselves are not changed.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **id** | path | **Integer** (int32) | ID of the project. | [required] [example: `1`] |
| **UnlinkAiProjectSourcesRequest** | body | [**UnlinkAiProjectSourcesRequest**](../../models/unlink-ai-project-sources-request.md) | The rooms to unlink. | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **204** | The rooms are unlinked | - | - |
| **400** | `roomIds` is empty or longer than 40 items | - | - |
| **403** | The caller may not edit the project, or the AI features are turned off on the portal | - | - |
| **404** | No AI project has this id | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../../models/error-api-response.md) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../../models/error-api-response.md) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../../models/error-api-response.md) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

null (empty response body)

## Authorization

[Basic](../rooms.md#basic), [OAuth2](../rooms.md#oauth2) (scopes: read, write), [ApiKeyBearer](../rooms.md#apikeybearer), [asc_auth_key](../rooms.md#asc_auth_key), [Bearer](../rooms.md#bearer), [OpenId](../rooms.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
