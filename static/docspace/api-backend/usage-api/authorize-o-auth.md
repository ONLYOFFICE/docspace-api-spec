# authorizeOAuth

Referenced types are defined in the [full reference](../oauth.md).

> authorizeOAuth(response\_type, client\_id, redirect\_uri, scope)

`GET /oauth2/authorize`

OAuth2 Authorization Endpoint

Initiates the OAuth2 authorization flow.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **response\_type** | query | **String** | The OAuth 2.0 response type, must be &#39;code&#39; for authorization code flow. | [required] [example: code] |
| **client\_id** | query | **String** | The client identifier issued to the client during registration. | [required] [example: 6c7cf17b-1bd3-47d5-94c6-be2d3570e168] |
| **redirect\_uri** | query | **String** | The URL to redirect to after authorization is complete. | [required] [example: https://example.com] |
| **scope** | query | **String** | The space-separated list of requested scope permissions. | [required] [example: files:read] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Authorization page | - | - |
| **400** | Invalid request parameters | - | - |

## Return type

null (empty response body)

## Authorization

[x-signature](../oauth.md#x-signature)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: Not defined
