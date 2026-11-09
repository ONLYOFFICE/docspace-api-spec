# getRoomMissingFileKeys

> RoomMissingFileKeysArrayWrapper getRoomMissingFileKeys(roomId, userIds)

`GET /api/2.0/privacyroom/{roomId}/access/missing`

Get missing file keys of a room

Reports which encrypted files of a private room each user cannot open yet, across all its folders, so that a  client can write exactly the missing keys with `PUT api/2.0/files/{fileId}/access` instead of trying every file.  The caller needs the right to change the room's access, which means its owner or a room manager; other members  and a DocSpace administrator who is not a member are refused, and an archived room, whose access cannot change,  is refused too. Listing `userIds` checks those people, members or not, which is what a client does before  `POST api/2.0/files/owner` answers 409 for a new owner; without it the members of the room are checked. The call  is read-only. The answer holds one entry per user who misses something and carries identifiers only, never a  key: an empty list means nothing is missing. A file stored in the clear needs no key and is never reported, and  an id that names nobody on this portal is ignored. A room that is not private, or a folder inside a room, is  rejected as invalid, as is a malformed id.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **roomId** | path | **Integer** (int32) | The private room to check. Take it from the `id` of the room returned by `POST api/2.0/files/rooms` or listed by  `GET api/2.0/files/rooms`. | [required] [example: `1234`] |
| **userIds** | query | **List** (uuid) | The people to check, repeated once per user (`userIds=...&userIds=...`). Take each from the `id` of a user  returned by `GET api/2.0/people`. | [optional] [example: `[9924256B-447C-4F19-9dbd-8ad8c39e8ff5]`] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The users who miss a file key and the files concerned | [**RoomMissingFileKeysArrayWrapper**](../../models/room-missing-file-keys-array-wrapper.md) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | The room is not a private room, or a user ID is malformed | - | - |
| **403** | The caller has no read access to the room or cannot change its access | - | - |
| **404** | The room is not found | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../../models/error-api-response.md) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../../models/error-api-response.md) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../../models/error-api-response.md) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**RoomMissingFileKeysArrayWrapper**](../../models/room-missing-file-keys-array-wrapper.md)

## Authorization

[Basic](../rooms.md#basic), [OAuth2](../rooms.md#oauth2) (scopes: read, write), [ApiKeyBearer](../rooms.md#apikeybearer), [asc_auth_key](../rooms.md#asc_auth_key), [Bearer](../rooms.md#bearer), [OpenId](../rooms.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
