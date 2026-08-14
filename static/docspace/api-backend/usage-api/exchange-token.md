# exchangeToken

Referenced types are defined in the [full reference](../oauth.md).

> exchangeToken_200_response exchangeToken(grant\_type, code, redirect\_uri, client\_id, client\_secret)

`POST /oauth2/token`

OAuth2 Token Endpoint

Exchange authorization code for access token

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **grant\_type** | form | **String** | The OAuth2 grant type, must be &#39;authorization_code&#39; for the authorization code flow. | [optional] |
| **code** | form | **String** | A temporary authorization code that is sent to the client to be exchanged for a token. | [optional] |
| **redirect\_uri** | form | **String** | The URL where the user will be redirected after successful or unsuccessful authentication. | [optional] |
| **client\_id** | form | **String** | The client identifier issued to the client during registration. | [optional] |
| **client\_secret** | form | **String** | The client secret issued to the client during registration. | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Successfully exchanged authorization code for access token | [**exchangeToken_200_response**](../oauth.md#model-exchangetoken-200-response) | - |
| **400** | Invalid request parameters | - | - |

## Return type

[**exchangeToken_200_response**](../oauth.md#model-exchangetoken-200-response)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/x-www-form-urlencoded
- **Accept**: application/json
