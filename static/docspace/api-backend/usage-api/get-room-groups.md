# getRoomGroups

Referenced types are defined in the [full reference](../files.md).

> RoomGroupArrayWrapper getRoomGroups(includeMembers)

`GET /api/2.0/files/group`

List room groups

Returns every room group of the calling account, each with the rooms it gathers. Only groups the caller  created are listed: groups of other members never appear here, and an account that has never made one gets an  empty array back. Set &#x60;includeMembers&#x60; to false to leave the &#x60;rooms&#x60; array out of every entry and keep the  name, the icon and &#x60;totalRooms&#x60; alone, which is the cheaper form when the list is only being shown as a menu.  Archived rooms are skipped in both the &#x60;rooms&#x60; array and the &#x60;totalRooms&#x60; count, and reappear once the room is  taken out of the archive. The listing is neither paged nor filtered - it always carries the whole set - and  the order of the entries is not contractual, so sort them on the client when the order matters. The call is  read-only. Use &#x60;GET api/2.0/files/group/{id}&#x60; when the identifier of a single group is already known, and  &#x60;POST api/2.0/files/group&#x60; to add one.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **includeMembers** | query | **Boolean** | Whether the rooms of each group are listed in the answer: true fills the &#x60;rooms&#x60; array of every entry, false  leaves it out and reports only how many there are in &#x60;totalRooms&#x60;. | [optional] [example: true] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The room groups of the calling account | [**RoomGroupArrayWrapper**](../files.md#model-roomgrouparraywrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **401** | Unauthorized | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**RoomGroupArrayWrapper**](../files.md#model-roomgrouparraywrapper)

## Authorization

[Basic](../files.md#basic), [OAuth2](../files.md#oauth2) (scopes: read, write), [ApiKeyBearer](../files.md#apikeybearer), [asc_auth_key](../files.md#asc_auth_key), [Bearer](../files.md#bearer), [OpenId](../files.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
