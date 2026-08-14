# updateUserType

Referenced types are defined in the [full reference](../people.md).

> EmployeeFullArrayWrapper updateUserType(type, UpdateMembersRequestDto)

`PUT /api/2.0/people/type/{type}`

Change a user type

Changes a type of the users with the IDs specified in the request.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **type** | path | **EmployeeType** | The new user type. | [required] [example: 1] [enum: All, RoomAdmin, Guest, DocSpaceAdmin, User] |
| **UpdateMembersRequestDto** | body | [**UpdateMembersRequestDto**](../people.md#model-updatemembersrequestdto) | The request parameters for updating the user information. | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | List of users with the detailed information | [**EmployeeFullArrayWrapper**](../people.md#model-employeefullarraywrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | No permissions to perform this action | - | - |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**EmployeeFullArrayWrapper**](../people.md#model-employeefullarraywrapper)

## Authorization

[Basic](../people.md#basic), [OAuth2](../people.md#oauth2) (scopes: read, write), [ApiKeyBearer](../people.md#apikeybearer) (scopes: read, write), [asc_auth_key](../people.md#asc_auth_key) (scopes: read, write), [Bearer](../people.md#bearer), [OpenId](../people.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

## PortalGuestsApi
