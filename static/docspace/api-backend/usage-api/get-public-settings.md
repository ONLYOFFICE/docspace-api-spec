# getPublicSettings

Referenced types are defined in the [full reference](../files.md).

> BooleanWrapper getPublicSettings(id)

`GET /api/2.0/files/roomtemplate/{id}/public`

Get room template public access

Reports whether the room template addressed by &#x60;id&#x60; is shared with everyone or is reachable only by the  accounts it was explicitly shared with. True means the Everyone group holds read access, so any member allowed  to create rooms can build one from the template with &#x60;POST api/2.0/files/rooms/fromtemplate&#x60;; false means only  the owner and the named recipients can. The identifier has to belong to a room template — take it from  &#x60;templateId&#x60; of &#x60;GET api/2.0/files/roomtemplate/status&#x60;, or from the folder list of &#x60;GET api/2.0/files/rooms&#x60;  called with &#x60;searchArea&#x60; set to 4 — while an ordinary room, a deleted template or an unknown value is answered  as missing. The caller needs read access to the template, so somebody else&#39;s private template is refused even  for a portal administrator, and members who cannot reach the Templates section at all are refused whatever the  template&#39;s state. The call only reads state; use &#x60;PUT api/2.0/files/roomtemplate/public&#x60; to change it.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **id** | path | **Integer** (int32) | The identifier of the room template. Take it from &#x60;templateId&#x60; of &#x60;GET api/2.0/files/roomtemplate/status&#x60;, or  from the folder list of &#x60;GET api/2.0/files/rooms&#x60; called with &#x60;searchArea&#x60; set to 4; an identifier of an  ordinary room is not accepted. | [required] [example: 1234] [min: 1] [max: 2147483647] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Ok | [**BooleanWrapper**](../files.md#model-booleanwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **401** | Unauthorized | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**BooleanWrapper**](../files.md#model-booleanwrapper)

## Authorization

[Basic](../files.md#basic), [OAuth2](../files.md#oauth2) (scopes: read, write), [ApiKeyBearer](../files.md#apikeybearer), [asc_auth_key](../files.md#asc_auth_key), [Bearer](../files.md#bearer), [OpenId](../files.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
