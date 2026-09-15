# getPortalCapabilities

Referenced types are defined in the [full reference](../api.md).

> CapabilitiesWrapper getPortalCapabilities()

`GET /api/2.0/capabilities`

Get portal capabilities

Returns the sign-in methods this portal offers, which a login client needs before anyone has signed in: LDAP  authentication and its domain, the external identity providers to show, the SAML single sign-on URL and its  label, and whether the built-in identity server is available. No token is needed and nothing has to be called  first - the operation is open to unauthenticated callers, answers even while the portal&#39;s payment has lapsed,  and is read-only and idempotent. &#x60;providers&#x60; holds provider keys such as &#x60;google&#x60; or &#x60;facebook&#x60;, ordered for  the country detected from the caller&#39;s IP address and reduced to the ones this installation has configured;  pass one of them as &#x60;provider&#x60; to &#x60;POST api/2.0/authentication&#x60;. An empty &#x60;providers&#x60; means external sign-in  is off and an empty &#x60;ssoUrl&#x60; means single sign-on is off; a capability whose settings cannot be read is  reported as disabled rather than failing the call, so a false flag means the method is not offered, not that  it is unknown. The answer describes the portal and never a user, and carries none of the configuration behind  these methods: an administrator reads that from &#x60;GET api/2.0/settings/ssov2&#x60; and  &#x60;GET api/2.0/settings/authservice&#x60;.

## Parameters
This endpoint does not need any parameter.

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The sign-in methods the portal offers: LDAP, the external identity providers, single sign-on and the identity server, each with the state it has for this portal | [**CapabilitiesWrapper**](../api.md#model-capabilitieswrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**CapabilitiesWrapper**](../api.md#model-capabilitieswrapper)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

## MigrationApi
