# deleteGuests

Referenced types are defined in the [full reference](../people.md).

> deleteGuests(UpdateMembersRequestDto)

`DELETE /api/2.0/people/guests`

Remove guest relations

Removes the listed guests from the caller&#39;s own list of guests and withdraws the access the caller had  granted them.  It does not delete the accounts: each guest keeps its profile and any access other members gave it, and only  the link to the caller and the caller&#39;s own shares disappear.  The caller has to be a room admin or a DocSpace admin, and every listed account has to exist, be an active  guest and be one of the caller&#39;s own guests - a single entry that is not rejects the whole call with 403 and  changes nothing.  The call returns no body; read &#x60;GET api/2.0/people/filter&#x60; with &#x60;area&#x60; set to &#x60;Guests&#x60; to see what is left.  To delete a guest account for good, disable it and then use &#x60;DELETE api/2.0/people/{userid}&#x60;.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **UpdateMembersRequestDto** | body | [**UpdateMembersRequestDto**](../people.md#model-updatemembersrequestdto) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The guests are no longer linked to the caller. No content is returned | - | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | The userIds field is missing | - | - |
| **403** | The caller is not an admin, or an entry is not an active guest of the caller | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../people.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../people.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../people.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

null (empty response body)

## Authorization

[Basic](../people.md#basic), [OAuth2](../people.md#oauth2) (scopes: read, write), [ApiKeyBearer](../people.md#apikeybearer), [asc_auth_key](../people.md#asc_auth_key), [Bearer](../people.md#bearer), [OpenId](../people.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

## PeoplePasswordApi
