# getSmtpSettings

Referenced types are defined in the [full reference](../api.md).

> SmtpSettingsWrapper getSmtpSettings()

`GET /api/2.0/smtpsettings/smtp`

Get SMTP settings

Returns the SMTP relay this portal sends its own mail through - host, port, sender identity and authentication  flags - as it is stored for the portal. Nothing has to be called first; the caller needs the portal-settings  right of a DocSpace administrator, and the SMTP settings section has to be enabled for the portal, otherwise  the call is answered with 402. The call is read-only and safe to repeat. &#x60;isDefaultSettings&#x60; is true when the  portal has no settings of its own and runs on the mail configuration of the installation: a standalone  installation then shows those server-wide values, while a cloud portal is answered with an empty settings  object instead, so an empty &#x60;host&#x60; together with &#x60;isDefaultSettings&#x60; true means nothing was ever saved here.  &#x60;credentialsUserPassword&#x60; always comes back empty - the stored password cannot be read back, and a client that  saves the settings again has to ask the user for it once more. &#x60;port&#x60; is the port that was saved, and settings  saved without one are stored with &#x60;25&#x60;. To find out whether the returned relay actually accepts mail, queue a  test with &#x60;GET api/2.0/smtpsettings/smtp/test&#x60;.

## Parameters
This endpoint does not need any parameter.

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The SMTP settings stored for the portal, with an empty password and &#x60;isDefaultSettings&#x60; telling whether the configuration of the installation is in use | [**SmtpSettingsWrapper**](../api.md#model-smtpsettingswrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **402** | The SMTP settings section is not enabled for this portal | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**SmtpSettingsWrapper**](../api.md#model-smtpsettingswrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer), [asc_auth_key](../api.md#asc_auth_key), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
