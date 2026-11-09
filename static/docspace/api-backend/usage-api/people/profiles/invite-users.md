# inviteUsers

> EmployeeArrayWrapper inviteUsers(InviteUsersRequestDto)

`POST /api/2.0/people/invite`

Invite users

Invites people to the portal by email, creating a pending profile for each address and mailing it an invitation  link. The caller has to be a room admin or a DocSpace admin and the portal has to allow inviting members; only a  DocSpace admin invites a room admin, only the owner a DocSpace admin, and `Guest` is not accepted. An address  that already has a profile is not mailed: the account is only related to the caller and raised to a higher type  when asked, while a disabled account rejects the call with 400. Nothing is sent when the invitations need more  paid seats than the tariff has left, or for a malformed or punycode address (400); otherwise the addresses are  applied one by one, so a failure partway leaves earlier invitations sent. The answer lists every pending profile  the caller may see, not only this call's. Inviting an address again shortly after its invitation went out -  after its pending profile was deleted - sends no second letter, and the link already sent still opens. Repeated  calls are throttled. Use `PUT api/2.0/people/invite` to resend the invitation, and `POST api/2.0/people` to  create a profile without mailing anybody.  Raises the `user.invited` webhook for every address that does not belong to a profile yet.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **InviteUsersRequestDto** | body | [**InviteUsersRequestDto**](../../models/invite-users-request-dto.md) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Every pending profile the caller may see, not only the ones just invited | [**EmployeeArrayWrapper**](../../models/employee-array-wrapper.md) | - |
| **400** | An address is malformed or written in punycode, or it belongs to a disabled account | - | - |
| **402** | The invitations would need more paid seats than the tariff has left | - | - |
| **403** | No permissions to perform this action | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../../models/error-api-response.md) | - |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../../models/error-api-response.md) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**EmployeeArrayWrapper**](../../models/employee-array-wrapper.md)

## Authorization

[Basic](../people.md#basic), [OAuth2](../people.md#oauth2) (scopes: read, write), [ApiKeyBearer](../people.md#apikeybearer), [asc_auth_key](../people.md#asc_auth_key), [Bearer](../people.md#bearer), [OpenId](../people.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
