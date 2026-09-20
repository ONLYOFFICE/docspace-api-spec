# getIsAuthentificated

Referenced types are defined in the [full reference](../api.md).

> BooleanWrapper getIsAuthentificated()

`GET /api/2.0/authentication`

Check authentication

Reports whether the credentials that came with this very request identify a signed-in user of the current  portal - the authentication cookie, or the token in the &#x60;Authorization&#x60; header. Nothing has to be called  first: the operation is open to unauthenticated callers, who simply get &#x60;false&#x60;, it is read-only and  idempotent, and it answers even while the portal&#39;s payment has lapsed. The result is a bare boolean that  carries no reason, so &#x60;false&#x60; covers a missing, malformed, expired and revoked token alike; the way to recover  from it is to sign in again with &#x60;POST api/2.0/authentication&#x60;. It says nothing about who the caller is or how  long the session still lasts - read &#x60;GET api/2.0/people/@self&#x60; for the profile behind the token.

## Parameters
This endpoint does not need any parameter.

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | &#x60;true&#x60; when the request carries a valid token or cookie of an active portal user, &#x60;false&#x60; in every other case | [**BooleanWrapper**](../api.md#model-booleanwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**BooleanWrapper**](../api.md#model-booleanwrapper)

## Authorization

[cookieAuth](../api.md#cookieauth), [bearerAuth](../api.md#bearerauth)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
