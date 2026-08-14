# submitConsent

Referenced types are defined in the [full reference](../oauth.md).

> submitConsent(client\_id, state, scope)

`POST /oauth2/authorize`

OAuth2 consent endpoint

Sends consent approval

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **client\_id** | form | **String** | The client identifier issued to the client during registration. | [optional] |
| **state** | form | **String** | The random string used to solve the CSRF vulnerability problem. | [optional] |
| **scope** | form | **String** | The space-separated list of requested scope permissions. | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **302** | Redirect to the client&#39;s redirect URI with authorization code | - | - |
| **400** | Invalid request parameters | - | - |

## Return type

null (empty response body)

## Authorization

[x-signature](../oauth.md#x-signature)

## HTTP request headers

- **Content-Type**: multipart/form-data
- **Accept**: Not defined

## OAuth20ClientManagementApi
