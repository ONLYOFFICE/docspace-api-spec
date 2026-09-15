# sendJoinInviteMail

Referenced types are defined in the [full reference](../api.md).

> StringWrapper sendJoinInviteMail(AdminMessageBaseSettingsRequestsDto)

`POST /api/2.0/settings/sendjoininvite`

Send an invitation email

Sends an invitation email with a join link to the address in the request - the self-registration the sign-in  page&#39;s register link performs. No token is needed. The portal has to publish a trusted-domain policy first,  saved with &#x60;POST api/2.0/settings/maildomainsettings&#x60;: without one there is nothing to join and every caller  alike is answered with 405 - the same condition &#x60;GET api/2.0/settings&#x60; reports as &#x60;enabledJoin&#x60;. &#x60;email&#x60; has  to be a real address written in ASCII rather than an internationalized one, must not already belong to a  portal member, and, when the policy names domains rather than accepting all of them, has to end with one of  them - each of those faults is refused with 400. &#x60;culture&#x60; picks the language of the letter. The invitation is  not an account: the invitee becomes a member only after following the link, and the role it grants, user or  room administrator, follows the trusted-domain settings and drops to user once the portal&#39;s paid places are  taken. Where the installation caps invitations, an accepted call spends one of those counted by  &#x60;invitationLimit&#x60;, and only about a dozen calls from one address in two minutes are accepted. What comes back  is a localized confirmation.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **AdminMessageBaseSettingsRequestsDto** | body | [**AdminMessageBaseSettingsRequestsDto**](../api.md#model-adminmessagebasesettingsrequestsdto) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | A localized message confirming that the invitation with the join link has been sent | [**StringWrapper**](../api.md#model-stringwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | The email address is malformed or internationalized, lies outside the trusted domains, or already belongs to a member of the portal | - | - |
| **403** | The portal is not accepting requests while it is being restored, transferred or encrypted | - | - |
| **405** | The portal publishes no trusted-domain policy, so it has nothing to join | - | - |
| **429** | Too many invitation requests came from the same network address | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | `Retry-After` |
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

## SettingsNotificationsApi
