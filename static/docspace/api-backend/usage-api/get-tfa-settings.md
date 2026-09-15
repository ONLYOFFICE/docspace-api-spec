# getTfaSettings

Referenced types are defined in the [full reference](../api.md).

> TfaSettingsArrayWrapper getTfaSettings()

`GET /api/2.0/settings/tfaapp`

Get the TFA settings

Lists the two-factor authentication methods this portal offers, with the state of each one. The list carries  at most two entries: &#x60;sms&#x60;, present only when the SMS method is enabled in the portal&#39;s configuration, and  &#x60;app&#x60;, present only when the authenticator-application method is enabled there, so an empty list means neither  method is offered here. Any authenticated member may call it, and what it returns is the portal-wide policy,  not the caller&#39;s own linked credential. This is a read-only, idempotent call. For every entry &#x60;enabled&#x60; says  whether that method is the current policy, &#x60;available&#x60; says whether it can actually be switched on (for &#x60;sms&#x60;  that also requires a configured SMS provider), &#x60;trustedIps&#x60; lists the addresses and ranges exempt from the  challenge, and &#x60;mandatoryUsers&#x60; and &#x60;mandatoryGroups&#x60; list the accounts that have to pass it even from a  trusted address. Change the policy with &#x60;PUT api/2.0/settings/tfaapp&#x60;, and read the caller&#39;s own backup codes  with &#x60;GET api/2.0/settings/tfaappcodes&#x60;.

## Parameters
This endpoint does not need any parameter.

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The TFA methods the portal offers, with the portal-wide state of each | [**TfaSettingsArrayWrapper**](../api.md#model-tfasettingsarraywrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **401** | Unauthorized | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**TfaSettingsArrayWrapper**](../api.md#model-tfasettingsarraywrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer), [asc_auth_key](../api.md#asc_auth_key), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
