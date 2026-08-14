# changeActivation

Referenced types are defined in the [full reference](../oauth.md).

> Object changeActivation(clientId, ChangeClientActivationRequest)

`PATCH /api/2.0/clients/{clientId}/activation`

Change client activation status

Activates or deactivates an OAuth2 client. When deactivated, the client cannot request new access tokens, but existing tokens will remain valid until they expire.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **clientId** | path | **String** | ID of the client to change activation for | [required] [example: 6c7cf17b-1bd3-47d5-94c6-be2d3570e168] [minLength: 1] |
| **ChangeClientActivationRequest** | body | [**ChangeClientActivationRequest**](../oauth.md#model-changeclientactivationrequest) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Client activation status successfully changed | **Object** | - |
| **400** | Invalid client ID format or activation status | [**ProblemDetail**](../oauth.md#model-problemdetail) | - |
| **403** | Insufficient permissions to change client activation | [**ProblemDetail**](../oauth.md#model-problemdetail) | - |
| **404** | Client not found | [**ProblemDetail**](../oauth.md#model-problemdetail) | - |
| **415** | Unsupported media type | [**ProblemDetail**](../oauth.md#model-problemdetail) | - |
| **429** | Too many requests - rate limit exceeded | [**ProblemDetail**](../oauth.md#model-problemdetail) | - |
| **500** | Internal server error occurred | [**ProblemDetail**](../oauth.md#model-problemdetail) | - |

## Return type

**Object**

## Authorization

[x-signature](../oauth.md#x-signature)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
