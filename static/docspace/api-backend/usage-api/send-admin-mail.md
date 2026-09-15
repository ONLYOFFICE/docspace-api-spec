# sendAdminMail

Referenced types are defined in the [full reference](../api.md).

> StringWrapper sendAdminMail(AdminMessageSettingsRequestsDto)

`POST /api/2.0/settings/sendadmmail`

Send a message to the administrator

Sends a message from someone who cannot get into the portal to its administrators - the contact form the  sign-in page offers unauthenticated visitors. No token is needed. The form has to be published first with  &#x60;POST api/2.0/settings/messagesettings&#x60; unless the portal&#39;s payment has lapsed, otherwise nothing is sent;  &#x60;enableAdmMess&#x60; in &#x60;GET api/2.0/settings&#x60; reports whether the call is worth making. &#x60;email&#x60; is the address the  administrators answer to and has to be a real address, and &#x60;message&#x60; is reduced to plain text first, so a body  carrying nothing but markup counts as empty - either fault is refused with 400. When the caller is not signed  in and this installation has a CAPTCHA configured, &#x60;recaptchaResponse&#x60; has to carry a solved challenge of the  &#x60;recaptchaType&#x60; that &#x60;GET api/2.0/settings&#x60; publishes together with the site key, and a missing or stale  answer refuses the call. &#x60;culture&#x60; picks the language of the letter. Delivery is queued and reaches the  administrators subscribed to administrator notifications, so a confirmed call means accepted rather than read,  and the answer is a localized confirmation. Attempts are rate limited per address and per operation, and  further ones are refused with 429.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **AdminMessageSettingsRequestsDto** | body | [**AdminMessageSettingsRequestsDto**](../api.md#model-adminmessagesettingsrequestsdto) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | A localized message confirming that the message has been queued for the portal administrators | [**StringWrapper**](../api.md#model-stringwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | The email address is malformed, or the message is empty once its markup is stripped | - | - |
| **429** | Too many contact attempts came from the same address within the rate-limit window | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**StringWrapper**](../api.md#model-stringwrapper)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
