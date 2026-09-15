# updateStorage

Referenced types are defined in the [full reference](../api.md).

> StorageSettingsWrapper updateStorage(StorageRequestsDto)

`PUT /api/2.0/settings/storage`

Switch the portal storage

Points the current portal at another storage and saves the credentials it needs: &#x60;module&#x60; is the identifier of  one of the storages listed by &#x60;GET api/2.0/settings/storage&#x60;, and &#x60;props&#x60; carries that provider&#39;s  authentication keys as name and value pairs, for example the bucket, region and access key of an Amazon S3  storage. The provider has to be available on the server, which the &#x60;isSet&#x60; flag of the listing tells,  otherwise the request is rejected as invalid. Sending the module the portal already uses changes nothing and  returns the saved settings as they are. Any other module starts an asynchronous migration of the portal data:  the portal moves into the migrating state and stays unavailable until the transfer ends, so follow it with  &#x60;GET api/2.0/settings/storage/progress&#x60; and do not send a second switch while it runs. The caller needs the  permission to edit portal settings, which in practice means the portal owner or a DocSpace admin, on a server  installation with an unrestricted access space. The response is the stored configuration, module and  properties, not the state of the migration. To return to the built-in local storage call  &#x60;DELETE api/2.0/settings/storage&#x60;, and for the CDN use &#x60;PUT api/2.0/settings/storage/cdn&#x60;.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **StorageRequestsDto** | body | [**StorageRequestsDto**](../api.md#model-storagerequestsdto) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The saved storage configuration; migration of the portal data to it has been started | [**StorageSettingsWrapper**](../api.md#model-storagesettingswrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | The requested storage module is not configured on this installation | - | - |
| **403** | The caller may not edit portal settings, or this installation does not allow changing the storage | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**StorageSettingsWrapper**](../api.md#model-storagesettingswrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer), [asc_auth_key](../api.md#asc_auth_key), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

## SettingsTFASettingsApi
