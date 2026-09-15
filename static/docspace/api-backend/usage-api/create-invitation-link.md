# createInvitationLink

Referenced types are defined in the [full reference](../api.md).

> InvitationLinkWrapper createInvitationLink(InvitationLinkCreateRequestDto)

`POST /api/2.0/portal/users/invitationlink`

Create an invitation link

Creates the portal&#39;s invitation link for one role and returns it together with the URL to share. A portal  keeps at most one link per role, so a call for a role that already has one is refused - read the existing link  with &#x60;GET api/2.0/portal/users/invitationlink/{employeeType}&#x60; and change it with  &#x60;PUT api/2.0/portal/users/invitationlink&#x60; instead. Inviting members has to be enabled for the portal  (&#x60;GET api/2.0/settings/invitationsettings&#x60;), &#x60;employeeType&#x60; has to be &#x60;DocSpaceAdmin&#x60;, &#x60;RoomAdmin&#x60; or &#x60;User&#x60;,  and &#x60;expiration&#x60;, when given, has to lie in the future and is read in the portal time zone. The caller needs  the right to add users of that role, only the portal owner may create the DocSpace administrator link, and a  link for a paying role additionally needs a free paid seat in the portal quota. The call is mutating and not  idempotent. The answer carries the &#x60;id&#x60; needed to update or delete the link, the shortened &#x60;url&#x60;,  &#x60;maxUseCount&#x60; and &#x60;currentUseCount&#x60;, &#x60;expiration&#x60; in the portal time zone - empty for a link that never  expires - and &#x60;isExpired&#x60;.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **InvitationLinkCreateRequestDto** | body | [**InvitationLinkCreateRequestDto**](../api.md#model-invitationlinkcreaterequestdto) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The invitation link as it was created, with the &#x60;id&#x60; to address it later and the &#x60;url&#x60; to share | [**InvitationLinkWrapper**](../api.md#model-invitationlinkwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **401** | Unauthorized | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**InvitationLinkWrapper**](../api.md#model-invitationlinkwrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer), [asc_auth_key](../api.md#asc_auth_key), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
