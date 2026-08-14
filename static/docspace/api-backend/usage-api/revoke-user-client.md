# revokeUserClient

Referenced types are defined in the [full reference](../oauth.md).

> Object revokeUserClient(clientId)

`DELETE /api/2.0/clients/{clientId}/revoke`

Revoke client consent

Revokes all user consents for the specified OAuth2 client. This will invalidate all access tokens and refresh tokens issued to this client for the current user. The user will need to re-authorize the client to access their resources.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **clientId** | path | **String** | ID of the client to revoke consent for | [required] [example: 6c7cf17b-1bd3-47d5-94c6-be2d3570e168] [minLength: 1] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Client consent successfully revoked | **Object** | - |
| **400** | Invalid client ID format | [**ProblemDetail**](../oauth.md#model-problemdetail) | - |
| **403** | Insufficient permissions to revoke consent | [**ProblemDetail**](../oauth.md#model-problemdetail) | - |
| **404** | Client not found | [**ProblemDetail**](../oauth.md#model-problemdetail) | - |
| **429** | Too many requests - rate limit exceeded | [**ProblemDetail**](../oauth.md#model-problemdetail) | - |
| **500** | Internal server error occurred | [**ProblemDetail**](../oauth.md#model-problemdetail) | - |
| **503** | Authorization service unavailable | [**ProblemDetail**](../oauth.md#model-problemdetail) | - |

## Return type

**Object**

## Authorization

[x-signature](../oauth.md#x-signature)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
