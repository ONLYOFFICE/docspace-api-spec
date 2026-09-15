# deleteInvitationLink

Referenced types are defined in the [full reference](../api.md).

> StringWrapper deleteInvitationLink(InvitationLinkDeleteRequestDto)

`DELETE /api/2.0/portal/users/invitationlink`

Delete an invitation link

Deletes the portal&#39;s invitation link with the given &#x60;id&#x60;, so the URL shared from it stops letting anyone in;  accounts that already joined through it are not touched. Inviting members has to be enabled for the portal  (&#x60;GET api/2.0/settings/invitationsettings&#x60;) and the link has to exist - a second call with the same &#x60;id&#x60; is  answered as not found. The caller needs the right to add users of the link&#39;s role, and only the portal owner  may delete the DocSpace administrator link. The call is destructive and cannot be undone: a link for the same  role has to be created again with &#x60;POST api/2.0/portal/users/invitationlink&#x60;, and it gets a new &#x60;id&#x60;, a new  URL and a &#x60;currentUseCount&#x60; that starts from zero. Nothing is returned in the body. To stop invitations  without losing the links, switch inviting members off for the whole portal with  &#x60;PUT api/2.0/settings/invitationsettings&#x60; - the links then stay stored but are refused until it is switched on  again.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **InvitationLinkDeleteRequestDto** | body | [**InvitationLinkDeleteRequestDto**](../api.md#model-invitationlinkdeleterequestdto) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The invitation link is deleted and its URL no longer lets anyone join the portal | [**StringWrapper**](../api.md#model-stringwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **401** | Unauthorized | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**StringWrapper**](../api.md#model-stringwrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer), [asc_auth_key](../api.md#asc_auth_key), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
