# getIsDefaultGreetingSettings

Referenced types are defined in the [full reference](../api.md).

> BooleanWrapper getIsDefaultGreetingSettings()

`GET /api/2.0/settings/greetingsettings/isdefault`

Check the default greeting settings

Reports whether the current portal still shows the built-in greeting caption instead of a title of its own.  The check is read-only and open to any authenticated user, with no administrative right required. It answers  &#x60;true&#x60; while no title is stored for the portal - the state after  &#x60;POST api/2.0/settings/greetingsettings/restore&#x60; on an installation that configures no portal name, and also  after saving an empty &#x60;title&#x60; - and &#x60;false&#x60; as soon as a non-empty title has been saved. Use it together with  &#x60;GET api/2.0/settings/greetingsettings&#x60;: that operation substitutes the localized default caption for a  missing title, so only these two calls together separate a default greeting from a custom one that happens to  repeat the default wording. The answer covers the greeting title alone; whether the white-label logos and logo  text are still the default ones is reported by &#x60;GET api/2.0/settings/whitelabel/logos/isdefault&#x60; and  &#x60;GET api/2.0/settings/whitelabel/logotext/isdefault&#x60;.

## Parameters
This endpoint does not need any parameter.

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Boolean value: true if the portal has no greeting title of its own and the built-in default caption is shown | [**BooleanWrapper**](../api.md#model-booleanwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **401** | Unauthorized | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**BooleanWrapper**](../api.md#model-booleanwrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer), [asc_auth_key](../api.md#asc_auth_key), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
