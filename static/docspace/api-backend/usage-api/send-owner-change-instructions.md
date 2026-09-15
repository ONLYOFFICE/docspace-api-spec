# sendOwnerChangeInstructions

Referenced types are defined in the [full reference](../api.md).

> OwnerChangeInstructionsWrapper sendOwnerChangeInstructions(OwnerIdSettingsRequestDto)

`POST /api/2.0/settings/owner`

Start the portal owner change

Starts handing this portal over to another of its members: the confirmation letter goes to the current owner&#39;s  address, and nothing changes until the link in it is used. The owner&#39;s own email address has to be confirmed  first, otherwise the call is answered with 400; &#x60;GET api/2.0/people/@self&#x60; reports it as &#x60;activationStatus&#x60;.  The caller needs the portal-settings right of a DocSpace administrator, so a room administrator, an ordinary  member or a guest is refused with 403, as is naming a guest in &#x60;ownerId&#x60;. Only the portal owner can actually  start a transfer: an administrator who is not the owner, or a named user who is inactive or unknown here, gets  200 with &#x60;status&#x60; 0 and a localized refusal instead of an error, so read &#x60;status&#x60; and not the HTTP code. A  started transfer answers &#x60;status&#x60; 1 and a &#x60;message&#x60; carrying the owner&#39;s address inside an HTML &#x60;mailto:&#x60;  anchor rather than as plain text. Ownership itself does not move here; every call issues a fresh link usable  for a limited period, seven days by default, and the attempt is recorded in the audit trail. Complete the  transfer with &#x60;PUT api/2.0/settings/owner&#x60;; changing what a member may do is &#x60;PUT api/2.0/people/type/{type}&#x60;.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **OwnerIdSettingsRequestDto** | body | [**OwnerIdSettingsRequestDto**](../api.md#model-owneridsettingsrequestdto) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The outcome of the request: &#x60;status&#x60; 1 with the address the instructions were sent to, or &#x60;status&#x60; 0 with a localized refusal when the transfer cannot be started | [**OwnerChangeInstructionsWrapper**](../api.md#model-ownerchangeinstructionswrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | The portal owner&#39;s own email address has not been confirmed yet, so no instructions can be sent | - | - |
| **403** | The caller does not hold the portal-settings right of a DocSpace administrator, or the user named as the new owner is a guest | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**OwnerChangeInstructionsWrapper**](../api.md#model-ownerchangeinstructionswrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer), [asc_auth_key](../api.md#asc_auth_key), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
