# startUserTypeUpdate

Referenced types are defined in the [full reference](../people.md).

> TaskProgressResponseWrapper startUserTypeUpdate(StartUpdateUserTypeDto)

`POST /api/2.0/people/type`

Start updating user type

Starts updating the type of the user or guest when reassigning rooms and shared files.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **StartUpdateUserTypeDto** | body | [**StartUpdateUserTypeDto**](../people.md#model-startupdateusertypedto) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Update type progress | [**TaskProgressResponseWrapper**](../people.md#model-taskprogressresponsewrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | Can not update user type | - | - |
| **403** | Access denied | - | - |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**TaskProgressResponseWrapper**](../people.md#model-taskprogressresponsewrapper)

## Authorization

[Basic](../people.md#basic), [OAuth2](../people.md#oauth2) (scopes: read, write), [ApiKeyBearer](../people.md#apikeybearer) (scopes: read, write), [asc_auth_key](../people.md#asc_auth_key) (scopes: read, write), [Bearer](../people.md#bearer), [OpenId](../people.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
