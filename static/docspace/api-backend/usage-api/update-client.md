# updateClient

Referenced types are defined in the [full reference](../oauth.md).

> Object updateClient(clientId, UpdateClientRequest)

`PUT /api/2.0/clients/{clientId}`

Update an existing OAuth2 client

Updates the configuration of an existing OAuth2 client. Allows modification of client name, description, redirect URIs, and other settings. The client ID cannot be modified.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **clientId** | path | **String** | ID of the client to update | [required] [example: 6c7cf17b-1bd3-47d5-94c6-be2d3570e168] [minLength: 1] |
| **UpdateClientRequest** | body | [**UpdateClientRequest**](../oauth.md#model-updateclientrequest) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Client successfully updated | **Object** | - |
| **400** | Invalid request - missing required fields or validation failed | [**ProblemDetail**](../oauth.md#model-problemdetail) | - |
| **403** | Insufficient permissions to update client | [**ProblemDetail**](../oauth.md#model-problemdetail) | - |
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

## OAuth20ClientQueryingApi
