# getInvitationLinkByEmployeeType

Referenced types are defined in the [full reference](../api.md).

> InvitationLinkWrapper getInvitationLinkByEmployeeType(employeeType)

`GET /api/2.0/portal/users/invitationlink/{employeeType}`

Get an invitation link by role

Returns the portal&#39;s invitation link for one role - the URL to share, how long it lasts and how often it has  already been used. Inviting members has to be enabled for the portal  (&#x60;GET api/2.0/settings/invitationsettings&#x60;) and &#x60;employeeType&#x60; has to be &#x60;DocSpaceAdmin&#x60;, &#x60;RoomAdmin&#x60; or  &#x60;User&#x60;; the caller needs the right to add users of that role, only the portal owner may read the DocSpace  administrator link, and a link for a paying role is shown only while the portal quota still has a free paid  seat. The call is read-only and idempotent, but the &#x60;url&#x60; it returns is signed for the calling account, so two  administrators are handed two different URLs for one and the same link. A role that has no link yet is  answered with an empty body and 200 rather than a 404 - create the link with  &#x60;POST api/2.0/portal/users/invitationlink&#x60;. &#x60;expiration&#x60; is in the portal time zone and empty for a link  without a deadline, &#x60;isExpired&#x60; says whether that deadline has passed, and &#x60;currentUseCount&#x60; counts how many  accounts have already joined through the link.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **employeeType** | path | **EmployeeType** | The role whoever follows the link joins with. Only &#x60;DocSpaceAdmin&#x60;, &#x60;RoomAdmin&#x60; and &#x60;User&#x60; have a link; any  other role is refused. The portal keeps at most one link per role, so this value alone identifies it. | [required] [example: 1] [enum: All, RoomAdmin, Guest, DocSpaceAdmin, User] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The invitation link of that role, or an empty body when the portal has no link for it | [**InvitationLinkWrapper**](../api.md#model-invitationlinkwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
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

- **Content-Type**: Not defined
- **Accept**: application/json
