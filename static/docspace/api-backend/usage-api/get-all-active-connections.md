# getAllActiveConnections

Referenced types are defined in the [full reference](../api.md).

> ActiveConnectionsWrapper getAllActiveConnections()

`GET /api/2.0/security/activeconnections`

Get active connections

Lists the connections the calling user currently has open on this portal - one item per successful sign-in  that is still active - so a client can show where the account is signed in and close what does not belong  there. Any signed-in user may call it, nothing has to be called first, and the answer always covers the caller  alone: the operation is read-only, idempotent and cannot show another user&#39;s connections. Items cover the last  year and are ordered newest sign-in first, with the caller&#39;s own connection moved to the top and its browser,  platform, IP address and location refreshed from the current request. &#x60;loginEvent&#x60; is the ID of that own  connection and is &#x60;0&#x60; when the request was authenticated with a token in the &#x60;Authorization&#x60; header instead of  the portal cookie; nothing is then marked as current, and a user with no stored connections gets a single item  describing the current request. &#x60;country&#x60; and &#x60;city&#x60; are resolved from the IP address and stay empty when it  cannot be located. Pass an item&#39;s &#x60;id&#x60; to &#x60;PUT api/2.0/security/activeconnections/logout/{loginEventId}&#x60; to  end that one connection.

## Parameters
This endpoint does not need any parameter.

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The caller&#39;s active connections, newest sign-in first, with &#x60;loginEvent&#x60; pointing at the connection the request itself was made with | [**ActiveConnectionsWrapper**](../api.md#model-activeconnectionswrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **401** | Unauthorized | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**ActiveConnectionsWrapper**](../api.md#model-activeconnectionswrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer), [asc_auth_key](../api.md#asc_auth_key), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
