# saveThirdParty

> ThirdPartyFolderWrapper saveThirdParty(ThirdPartyRequestDto)

`POST /api/2.0/files/thirdparty`

Connect a third-party account

Connects an account at a third-party storage service as room storage, or, with `providerId`, re-authenticates an  account the caller connected earlier, and returns the folder that stands for the account's root. Take  `providerKey` from `GET api/2.0/files/thirdparty/providers` and send `url` wherever it reports  `requiredConnectionUrl`; OAuth services take `token`, the authorization code from their consent screen, the  others `login` and `password`. The caller needs the right to create rooms, and the portal-wide third-party switch  has to be on. Credentials are checked before anything is stored; a call without `providerId` always adds a new  account, and a re-authenticated room account keeps its server address. The new account is used by  `POST api/2.0/files/rooms/thirdparty/{id}`; backup storage is connected by `POST api/2.0/files/thirdparty/backup`.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **ThirdPartyRequestDto** | body | [**ThirdPartyRequestDto**](../../models/third-party-request-dto.md) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The root folder of the connected account | [**ThirdPartyFolderWrapper**](../../models/third-party-folder-wrapper.md) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | The request body cannot be read or has no `customerTitle` or `providerKey`, `providerId` is neither a number nor a numeric string, or, for a new account, `providerKey` names no known storage service, the `token` or `password` the service needs is missing, or `url` is missing or is not an HTTP address for a service that needs it | - | - |
| **403** | The caller cannot create rooms, the portal-wide third-party switch is off or no storage service is enabled, the title of a new account is empty once invalid characters are removed, the service rejects the credentials, or `providerId` names an account connected by another member | - | - |
| **404** | `providerId` names no third-party account on the portal | - | - |
| **500** | The storage service cannot be reached or fails while the credentials are checked | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../../models/error-api-response.md) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../../models/error-api-response.md) | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**ThirdPartyFolderWrapper**](../../models/third-party-folder-wrapper.md)

## Authorization

[Basic](../files.md#basic), [OAuth2](../files.md#oauth2) (scopes: read, write), [ApiKeyBearer](../files.md#apikeybearer), [asc_auth_key](../files.md#asc_auth_key), [Bearer](../files.md#bearer), [OpenId](../files.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
