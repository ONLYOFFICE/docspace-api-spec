# deleteInvitationLink

Referenced types are defined in the [full reference](../api.md).

> StringWrapper deleteInvitationLink(InvitationLinkDeleteRequestDto)

`DELETE /api/2.0/portal/users/invitationlink`

Deletes an invitation link.

Ensures that the current user has permission to delete the specified invitation link.  Throws security or not-found exceptions if required conditions are not met.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **InvitationLinkDeleteRequestDto** | body | [**InvitationLinkDeleteRequestDto**](../api.md#model-invitationlinkdeleterequestdto) | The data transfer object containing the details of the invitation link to be deleted. | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Invitation link | [**StringWrapper**](../api.md#model-stringwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**StringWrapper**](../api.md#model-stringwrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer) (scopes: read, write), [asc_auth_key](../api.md#asc_auth_key) (scopes: read, write), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
