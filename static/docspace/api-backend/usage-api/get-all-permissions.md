# getAllPermissions

Referenced types are defined in the [full reference](../people.md).

> STRINGArrayWrapper getAllPermissions()

`GET /api/2.0/keys/permissions`

Get API key permissions

Returns every scope value the portal accepts in the &#x60;permissions&#x60; array of an API key.  Read it before &#x60;POST api/2.0/keys&#x60; or &#x60;PUT api/2.0/keys/{keyId}&#x60;, because any other value is rejected with  400.  Any portal member except a guest may call it, and the call is read-only.  The answer is a flat list sorted alphabetically, holding the per-area scopes such as &#x60;accounts:read&#x60;,  &#x60;files:write&#x60; and &#x60;rooms:write&#x60;, the portal-wide &#x60;*:read&#x60; and &#x60;*:write&#x60;, and &#x60;*&#x60; which stands for a key  without scope restrictions.  The list is fixed for the portal and identical for every caller, so it can be cached by the client.

## Parameters
This endpoint does not need any parameter.

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The scope values accepted in the permissions array of an API key | [**STRINGArrayWrapper**](../people.md#model-stringarraywrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | The caller is a guest | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../people.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../people.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../people.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**STRINGArrayWrapper**](../people.md#model-stringarraywrapper)

## Authorization

[Basic](../people.md#basic), [OAuth2](../people.md#oauth2) (scopes: read, write), [ApiKeyBearer](../people.md#apikeybearer), [asc_auth_key](../people.md#asc_auth_key), [Bearer](../people.md#bearer), [OpenId](../people.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
