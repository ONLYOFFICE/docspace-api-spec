# getClient

Referenced types are defined in the [full reference](../oauth.md).

> ClientResponse getClient(clientId)

`GET /api/2.0/clients/{clientId}`

Get client details

Retrieves detailed information about a specific OAuth2 client including its name, description, redirect URIs, and scopes.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **clientId** | path | **String** | ID of the client to retrieve | [required] [example: 6c7cf17b-1bd3-47d5-94c6-be2d3570e168] [minLength: 1] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Client details successfully retrieved | [**ClientResponse**](../oauth.md#model-clientresponse) | - |
| **400** | Invalid client ID format | [**ProblemDetail**](../oauth.md#model-problemdetail) | - |
| **403** | Insufficient permissions to view client | [**ProblemDetail**](../oauth.md#model-problemdetail) | - |
| **404** | Client not found | [**ProblemDetail**](../oauth.md#model-problemdetail) | - |
| **429** | Too many requests - rate limit exceeded | [**ProblemDetail**](../oauth.md#model-problemdetail) | - |
| **500** | Internal server error occurred | [**ProblemDetail**](../oauth.md#model-problemdetail) | - |

## Return type

[**ClientResponse**](../oauth.md#model-clientresponse)

## Authorization

[x-signature](../oauth.md#x-signature)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
