# getScopes

Referenced types are defined in the [full reference](../oauth.md).

> ScopeResponse getScopes()

`GET /api/2.0/scopes`

List available OAuth2 scopes

Retrieves a list of all available OAuth2 scopes for the specified tenant. The scopes define the permissions that can be requested by OAuth2 clients. The list is ordered alphabetically, with the &#39;openid&#39; scope always appearing first.

## Parameters
This endpoint does not need any parameter.

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Scopes successfully retrieved | [**ScopeResponse**](../oauth.md#model-scoperesponse) | - |
| **400** | Invalid request parameters | [**ProblemDetail**](../oauth.md#model-problemdetail) | - |
| **403** | Insufficient permissions to list scopes | [**ProblemDetail**](../oauth.md#model-problemdetail) | - |
| **429** | Too many requests - rate limit exceeded | [**ProblemDetail**](../oauth.md#model-problemdetail) | - |
| **500** | Internal server error occurred | [**ProblemDetail**](../oauth.md#model-problemdetail) | - |

## Return type

[**ScopeResponse**](../oauth.md#model-scoperesponse)

## Authorization

[x-signature](../oauth.md#x-signature)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
