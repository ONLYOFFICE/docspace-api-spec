# getApiKey

Referenced types are defined in the [full reference](../people.md).

> ApiKeyResponseWrapper getApiKey()

`GET /api/2.0/keys/@self`

Get the current API key

Returns the API key that authenticated this very request, letting the holder of a key find out what it is  allowed to do without knowing its ID.  The key is identified by the &#x60;Authorization&#x60; header of the call itself, so the request has to be sent as  &#x60;Bearer sk-...&#x60;; a session authenticated in any other way has no key to report and this operation is not  usable for it.  The call is read-only and returns one entry, with the same fields as &#x60;GET api/2.0/keys&#x60; and without the  secret - read &#x60;permissions&#x60; for the granted scopes, &#x60;expiresAt&#x60; for the expiry and &#x60;isActive&#x60; for the state.  To look at a key other than the one in use, call &#x60;GET api/2.0/keys&#x60; instead.

## Parameters
This endpoint does not need any parameter.

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The API key that authenticated this request | [**ApiKeyResponseWrapper**](../people.md#model-apikeyresponsewrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **401** | Unauthorized | [**ErrorApiResponse**](../people.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../people.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../people.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**ApiKeyResponseWrapper**](../people.md#model-apikeyresponsewrapper)

## Authorization

[Basic](../people.md#basic), [OAuth2](../people.md#oauth2) (scopes: read, write), [ApiKeyBearer](../people.md#apikeybearer), [asc_auth_key](../people.md#asc_auth_key), [Bearer](../people.md#bearer), [OpenId](../people.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
