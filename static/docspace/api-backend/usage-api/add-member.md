# addMember

Referenced types are defined in the [full reference](../people.md).

> EmployeeFullWrapper addMember(MemberRequestDto)

`POST /api/2.0/people`

Add a user

Creates a portal profile, either by an administrator adding somebody directly or by a person accepting an  invitation link, which is why the operation accepts both an authenticated session and an invitation  confirmation token.  Set &#x60;fromInviteLink&#x60; to true and pass the invitation &#x60;key&#x60; for the second case: the resulting type then comes  from the link and the &#x60;type&#x60; in the request is ignored, and an invalid or expired link answers 403.  Without a link the caller needs the permission to add users of the requested type, cannot create a guest  through this operation at all, has to be a DocSpace admin to create a room admin and the portal owner to  create another DocSpace admin; either way the portal has to allow inviting members, or guests when the link  says so.  The password is optional: &#x60;passwordHash&#x60; is taken as it is, a plain &#x60;password&#x60; is checked against the portal  password policy and rejected with 400 when it is too weak, and when both are omitted a random password is  generated and the account is created without anybody knowing it.  When the portal has no free paid seat the account is still created, silently as a &#x60;User&#x60; instead of the  requested type, so read the &#x60;type&#x60; in the answer rather than assuming the request was honoured.  Creating a profile raises a &#x60;UserCreated&#x60; webhook, downloads the avatar named in &#x60;files&#x60; if one is given, and  answers with the new profile including its ID.  To invite several people by email at once instead, use &#x60;POST api/2.0/people/invite&#x60;.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **MemberRequestDto** | body | [**MemberRequestDto**](../people.md#model-memberrequestdto) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The new profile with its detailed information | [**EmployeeFullWrapper**](../people.md#model-employeefullwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | The password does not meet the portal password policy | - | - |
| **403** | The invitation link is invalid or has expired, the portal does not allow inviting this kind of account, or the caller may not create an account of the requested type | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../people.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../people.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../people.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**EmployeeFullWrapper**](../people.md#model-employeefullwrapper)

## Authorization

[Basic](../people.md#basic), [OAuth2](../people.md#oauth2) (scopes: read, write), [ApiKeyBearer](../people.md#apikeybearer), [asc_auth_key](../people.md#asc_auth_key), [Bearer](../people.md#bearer), [OpenId](../people.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
