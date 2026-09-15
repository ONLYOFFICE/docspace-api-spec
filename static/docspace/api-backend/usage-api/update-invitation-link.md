# updateInvitationLink

Referenced types are defined in the [full reference](../api.md).

> InvitationLinkWrapper updateInvitationLink(InvitationLinkUpdateRequestDto)

`PUT /api/2.0/portal/users/invitationlink`

Update an invitation link

Changes the deadline and the use limit of an existing invitation link, addressed by its &#x60;id&#x60;. The role of a  link cannot be changed - delete it and create a link for the other role instead. Inviting members has to be  enabled for the portal (&#x60;GET api/2.0/settings/invitationsettings&#x60;), the link has to exist, and &#x60;maxUseCount&#x60;  may not be lower than the number of uses the link already has, which  &#x60;GET api/2.0/portal/users/invitationlink/{employeeType}&#x60; reports as &#x60;currentUseCount&#x60;. An &#x60;expiration&#x60; in the  past is refused; the body is applied as a whole, so omitting &#x60;expiration&#x60; clears the deadline and omitting  &#x60;maxUseCount&#x60; removes the use limit. The caller needs the right to add users of the link&#39;s role and only the  portal owner may change the DocSpace administrator link. The call is mutating, and repeating it with the same  body leaves the link as it is. The whole link comes back as it now stands, with &#x60;url&#x60; signed for the calling  account - the URL therefore differs between administrators while the link behind it is the same.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **InvitationLinkUpdateRequestDto** | body | [**InvitationLinkUpdateRequestDto**](../api.md#model-invitationlinkupdaterequestdto) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The invitation link as it now stands, with the deadline and the use limit that were applied | [**InvitationLinkWrapper**](../api.md#model-invitationlinkwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
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

## SecurityAccessToDevToolsApi
