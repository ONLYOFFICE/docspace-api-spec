# createClient

Referenced types are defined in the [full reference](../oauth.md).

> ClientResponse createClient(CreateClientRequest)

`POST /api/2.0/clients`

Create a new OAuth2 client

Creates a new OAuth2 client with the specified configuration. The client will be created with the provided scopes, redirect URIs, and other settings. Returns the created client details including the generated client ID.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **CreateClientRequest** | body | [**CreateClientRequest**](../oauth.md#model-createclientrequest) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **201** | Client successfully created | [**ClientResponse**](../oauth.md#model-clientresponse) | - |
| **400** | Invalid request - missing required fields or validation failed | [**ProblemDetail**](../oauth.md#model-problemdetail) | - |
| **403** | Insufficient permissions to create client | [**ProblemDetail**](../oauth.md#model-problemdetail) | - |
| **415** | Unsupported media type | [**ProblemDetail**](../oauth.md#model-problemdetail) | - |
| **429** | Too many requests - rate limit exceeded | [**ProblemDetail**](../oauth.md#model-problemdetail) | - |
| **500** | Internal server error occurred | [**ProblemDetail**](../oauth.md#model-problemdetail) | - |

## Return type

[**ClientResponse**](../oauth.md#model-clientresponse)

## Authorization

[x-signature](../oauth.md#x-signature)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
