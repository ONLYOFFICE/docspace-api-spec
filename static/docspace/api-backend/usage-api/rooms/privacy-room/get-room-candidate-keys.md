# getRoomCandidateKeys

> EncryptionKeyArrayWrapper getRoomCandidateKeys(roomId, userIds)

`GET /api/2.0/privacyroom/{roomId}/access/candidates`

Get public keys of room invitees

Returns the public encryption keys of people who are about to be invited to a private room, so that a client can  encrypt the room's file keys for them before it grants the access. `GET api/2.0/privacyroom/{roomId}/access`  covers members only, which makes this the call that comes first when inviting. The room has to be an active  private room: an archived one cannot change its access and is refused, and an unknown one is reported as missing.  The caller needs the right to change the room's access, which means its owner or a room manager; other members  and a DocSpace administrator who is not a member are refused. The call is read-only and grants nothing, and  `PUT api/2.0/files/rooms/{id}/share` still does the inviting. The answer holds one entry per key, and no entry  ever carries `privateKeyEnc`, not even the caller's own. A listed user who is absent cannot be invited as they  are: they have no key yet and need to create one with `POST api/2.0/privacyroom/keys`, or they are a guest, a  terminated user, or nobody on this portal. A duplicate id counts once, and no ids answer an empty list. A  malformed id, a room that is not private, or a folder inside a room is rejected as invalid.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **roomId** | path | **Integer** (int32) | The private room the people are invited to. Take it from the `id` of the room returned by  `POST api/2.0/files/rooms` or listed by `GET api/2.0/files/rooms`. | [required] [example: `1234`] |
| **userIds** | query | **List** (uuid) | The people to read the keys of, repeated once per user (`userIds=...&userIds=...`). Take each from the `id` of  a user returned by `GET api/2.0/people`. | [optional] [example: `["9924256B-447C-4F19-9dbd-8ad8c39e8ff5"]`] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The public encryption keys of the listed users who can be invited | [**EncryptionKeyArrayWrapper**](../../models/encryption-key-array-wrapper.md) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | The room is not a private room, or a user ID is malformed | - | - |
| **403** | The caller has no read access to the room or cannot change its access | - | - |
| **404** | The room is not found | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../../models/error-api-response.md) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../../models/error-api-response.md) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../../models/error-api-response.md) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**EncryptionKeyArrayWrapper**](../../models/encryption-key-array-wrapper.md)

## Authorization

[Basic](../rooms.md#basic), [OAuth2](../rooms.md#oauth2) (scopes: read, write), [ApiKeyBearer](../rooms.md#apikeybearer), [asc_auth_key](../rooms.md#asc_auth_key), [Bearer](../rooms.md#bearer), [OpenId](../rooms.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
