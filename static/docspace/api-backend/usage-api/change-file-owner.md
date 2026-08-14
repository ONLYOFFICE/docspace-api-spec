# changeFileOwner

Referenced types are defined in the [full reference](../files.md).

> FileEntryBaseArrayWrapper changeFileOwner(ChangeOwnerRequestDto)

`POST /api/2.0/files/owner`

Change the file owner

Changes the owner of the file with the ID specified in the request.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **ChangeOwnerRequestDto** | body | [**ChangeOwnerRequestDto**](../files.md#model-changeownerrequestdto) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | File entry information | [**FileEntryBaseArrayWrapper**](../files.md#model-fileentrybasearraywrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**FileEntryBaseArrayWrapper**](../files.md#model-fileentrybasearraywrapper)

## Authorization

[Basic](../files.md#basic), [OAuth2](../files.md#oauth2) (scopes: read, write), [ApiKeyBearer](../files.md#apikeybearer) (scopes: read, write), [asc_auth_key](../files.md#asc_auth_key) (scopes: read, write), [Bearer](../files.md#bearer), [OpenId](../files.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
