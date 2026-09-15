# docRegisterPusnNotificationDevice

Referenced types are defined in the [full reference](../api.md).

> FireBaseUserWrapper docRegisterPusnNotificationDevice(FirebaseRequestsDto)

`POST /api/2.0/settings/push/docregisterdevice`

Register a push device

Registers one mobile device of the calling user for the push notifications of the Documents application, by  storing the Firebase token that device was issued together with the initial &#x60;isSubscribed&#x60; state. The token is  handed out by Firebase to the mobile client, so obtain it there before calling: nothing here checks it, and it  is kept as an opaque string of up to 255 characters. Every signed-in member registers its own devices,  whatever its role - owner, administrator, user or guest - and a registration is bound to the caller and the  current portal, so another member&#39;s devices cannot be touched. The call is safe to repeat, but it is not an  update: a token already registered comes back as it stands and &#x60;isSubscribed&#x60; from the request is ignored, so  switch an existing registration on or off with &#x60;PUT api/2.0/settings/push/docsubscribe&#x60; instead. What comes  back is the stored registration, with &#x60;application&#x60; always &#x60;doc&#x60; and &#x60;isSubscribed&#x60; as stored. Only a  subscribed device is sent the room activity messages, such as an invitation to a room, a role change, an  archived room or a new document in a room, and only while the installation itself is configured with Firebase  credentials.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **FirebaseRequestsDto** | body | [**FirebaseRequestsDto**](../api.md#model-firebaserequestsdto) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The stored device registration of the calling user, with the Firebase token, the &#x60;doc&#x60; application and the subscription state as they are kept | [**FireBaseUserWrapper**](../api.md#model-firebaseuserwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **401** | Unauthorized | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**FireBaseUserWrapper**](../api.md#model-firebaseuserwrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer), [asc_auth_key](../api.md#asc_auth_key), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
