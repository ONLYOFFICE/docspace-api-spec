# regenerateSecret

Referenced types are defined in the [full reference](../oauth.md).

> ClientSecretResponse regenerateSecret(clientId)

`PATCH /api/2.0/clients/{clientId}/regenerate`

Regenerate client secret

Generates a new client secret for the specified OAuth2 client. The old secret will be immediately invalidated. This operation should be used with caution as it requires updating the secret in all client applications.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **clientId** | path | **String** | ID of the client to regenerate secret for | [required] [example: 6c7cf17b-1bd3-47d5-94c6-be2d3570e168] [minLength: 1] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Client secret successfully regenerated | [**ClientSecretResponse**](../oauth.md#model-clientsecretresponse) | - |
| **400** | Invalid client ID format | [**ProblemDetail**](../oauth.md#model-problemdetail) | - |
| **403** | Insufficient permissions to regenerate client secret | [**ProblemDetail**](../oauth.md#model-problemdetail) | - |
| **404** | Client not found | [**ProblemDetail**](../oauth.md#model-problemdetail) | - |
| **429** | Too many requests - rate limit exceeded | [**ProblemDetail**](../oauth.md#model-problemdetail) | - |
| **500** | Internal server error occurred | [**ProblemDetail**](../oauth.md#model-problemdetail) | - |

## Return type

[**ClientSecretResponse**](../oauth.md#model-clientsecretresponse)

## Authorization

[x-signature](../oauth.md#x-signature)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
