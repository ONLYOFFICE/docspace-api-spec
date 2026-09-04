# ONLYOFFICE DocSpace AI API

The browsable version of this reference, with a request builder and code samples, is published at
<https://api.onlyoffice.com/docspace/api-backend/usage-api/>.

All URIs are relative to *https://yourportal.onlyoffice.com*, where the host is the address of your DocSpace instance.

## Endpoints

| Class | Method | HTTP request | Description |
|------------ | ------------- | ------------- | -------------|
| *AIAIApi* | [**aiAiApproveToolCall**](#aiaiapprovetoolcall) | **POST** /api/2.0/ai/ai/approve-tool-call | Approve tool call |
| *AIAIApi* | [**aiAiDenyToolCall**](#aiaidenytoolcall) | **POST** /api/2.0/ai/ai/deny-tool-call | Deny tool call |
| *AIAIApi* | [**aiAiRegenerateStream**](#aiairegeneratestream) | **POST** /api/2.0/ai/ai/regenerate-stream | Regenerate stream |
| *AIAIApi* | [**aiAiSend**](#aiaisend) | **POST** /api/2.0/ai/ai/send | Send |
| *AIAIApi* | [**aiAiSendCustom**](#aiaisendcustom) | **POST** /api/2.0/ai/ai/send-custom | Send custom |
| *AIAIApi* | [**aiAiSendWithStream**](#aiaisendwithstream) | **POST** /api/2.0/ai/ai/send-with-stream | Send with stream |
| *AIAIApi* | [**aiAiSendWithStreamOpenAI**](#aiaisendwithstreamopenai) | **POST** /api/2.0/ai/ai/send-with-stream-openai | Send with stream open ai |
| *AIAgentsApi* | [**aiAgentsCreate**](#aiagentscreate) | **POST** /api/2.0/ai/agents | Create an agent |
| *AIAgentsApi* | [**aiAgentsDelete**](#aiagentsdelete) | **DELETE** /api/2.0/ai/agents/{id} | Delete an agent |
| *AIAgentsApi* | [**aiAgentsGet**](#aiagentsget) | **GET** /api/2.0/ai/agents/{id} | Get an agent |
| *AIAgentsApi* | [**aiAgentsList**](#aiagentslist) | **GET** /api/2.0/ai/agents | List agents |
| *AIAgentsApi* | [**aiAgentsNews**](#aiagentsnews) | **GET** /api/2.0/ai/agents/news | List agent news items |
| *AIAgentsApi* | [**aiAgentsResetQuota**](#aiagentsresetquota) | **PUT** /api/2.0/ai/agents/resetquota | Reset agents' quota |
| *AIAgentsApi* | [**aiAgentsUpdate**](#aiagentsupdate) | **PUT** /api/2.0/ai/agents/{id} | Update an agent |
| *AIAgentsApi* | [**aiAgentsUpdateQuota**](#aiagentsupdatequota) | **PUT** /api/2.0/ai/agents/agentquota | Update agents' quota |
| *AIAssignmentsApi* | [**aiAssignmentsAssign**](#aiassignmentsassign) | **PUT** /api/2.0/ai/assignments/assign | Assign |
| *AIAssignmentsApi* | [**aiAssignmentsBulkAssign**](#aiassignmentsbulkassign) | **PUT** /api/2.0/ai/assignments/bulk-assign | Bulk assign |
| *AIAssignmentsApi* | [**aiAssignmentsCascadeProfileDelete**](#aiassignmentscascadeprofiledelete) | **DELETE** /api/2.0/ai/assignments/cascade-profile-delete | Cascade profile delete |
| *AIAssignmentsApi* | [**aiAssignmentsGetAllAssignments**](#aiassignmentsgetallassignments) | **GET** /api/2.0/ai/assignments/get-all-assignments | Get all assignments |
| *AIAssignmentsApi* | [**aiAssignmentsGetAssignment**](#aiassignmentsgetassignment) | **GET** /api/2.0/ai/assignments/get-assignment | Get assignment |
| *AIAssignmentsApi* | [**aiAssignmentsResolveForAction**](#aiassignmentsresolveforaction) | **GET** /api/2.0/ai/assignments/resolve-for-action | Resolve for action |
| *AIAssignmentsApi* | [**aiAssignmentsTryResolveForAction**](#aiassignmentstryresolveforaction) | **GET** /api/2.0/ai/assignments/try-resolve-for-action | Try resolve for action |
| *AIAssignmentsApi* | [**aiAssignmentsUnassign**](#aiassignmentsunassign) | **DELETE** /api/2.0/ai/assignments/unassign | Unassign |
| *AIAttachmentsApi* | [**aiAttachmentsDelete**](#aiattachmentsdelete) | **DELETE** /api/2.0/ai/attachments/delete | Delete |
| *AIAttachmentsApi* | [**aiAttachmentsDeleteMany**](#aiattachmentsdeletemany) | **DELETE** /api/2.0/ai/attachments/delete-many | Delete many |
| *AIAttachmentsApi* | [**aiAttachmentsGet**](#aiattachmentsget) | **POST** /api/2.0/ai/attachments/get | Get |
| *AIAttachmentsApi* | [**aiAttachmentsGetMany**](#aiattachmentsgetmany) | **POST** /api/2.0/ai/attachments/get-many | Get many |
| *AIAttachmentsApi* | [**aiAttachmentsLinkToMessage**](#aiattachmentslinktomessage) | **POST** /api/2.0/ai/attachments/link-to-message | Link to message |
| *AIAttachmentsApi* | [**aiAttachmentsSaveFile**](#aiattachmentssavefile) | **POST** /api/2.0/ai/attachments/save-file | Save file |
| *AIAttachmentsApi* | [**aiAttachmentsSaveFilesMany**](#aiattachmentssavefilesmany) | **POST** /api/2.0/ai/attachments/save-files-many | Save files many |
| *AIEditorToolsApi* | [**aiEditorToolsCall**](#aieditortoolscall) | **POST** /api/2.0/ai/editor-tools/call | Execute a DocSpace tool on behalf of the editor AI plugin |
| *AIEditorToolsApi* | [**aiEditorToolsList**](#aieditortoolslist) | **GET** /api/2.0/ai/editor-tools/list | Sanitized DocSpace tool catalog for the editor AI plugin |
| *AIExportApi* | [**aiExportTextToDocx**](#aiexporttexttodocx) | **POST** /api/2.0/ai/text-to-docx | Start markdown → docx export |
| *AIOpenAIPassthroughApi* | [**aiOpenaiChatCompletions**](#aiopenaichatcompletions) | **POST** /api/2.0/ai/openai/{profileId}/v1/chat/completions | OpenAI-compatible chat completions proxied to the profile's provider |
| *AIOpenAIPassthroughApi* | [**aiOpenaiImagesGenerations**](#aiopenaiimagesgenerations) | **POST** /api/2.0/ai/openai/{profileId}/v1/images/generations | OpenAI-compatible image generation proxied to the profile's provider |
| *AIPreferencesApi* | [**aiPreferencesClearDeepMode**](#aipreferencescleardeepmode) | **DELETE** /api/2.0/ai/preferences/clear-deep-mode | Clear deep mode |
| *AIPreferencesApi* | [**aiPreferencesGetDeepMode**](#aipreferencesgetdeepmode) | **GET** /api/2.0/ai/preferences/get-deep-mode | Get deep mode |
| *AIPreferencesApi* | [**aiPreferencesIsDeepModeSet**](#aipreferencesisdeepmodeset) | **GET** /api/2.0/ai/preferences/is-deep-mode-set | Is deep mode set |
| *AIPreferencesApi* | [**aiPreferencesSetDeepMode**](#aipreferencessetdeepmode) | **PUT** /api/2.0/ai/preferences/set-deep-mode | Set deep mode |
| *AIProfilesApi* | [**aiProfilesCreate**](#aiprofilescreate) | **POST** /api/2.0/ai/profiles/create | Create |
| *AIProfilesApi* | [**aiProfilesDelete**](#aiprofilesdelete) | **DELETE** /api/2.0/ai/profiles/delete | Delete |
| *AIProfilesApi* | [**aiProfilesGetById**](#aiprofilesgetbyid) | **GET** /api/2.0/ai/profiles/get-by-id | Get by id |
| *AIProfilesApi* | [**aiProfilesList**](#aiprofileslist) | **GET** /api/2.0/ai/profiles/list | List |
| *AIProfilesApi* | [**aiProfilesListModels**](#aiprofileslistmodels) | **GET** /api/2.0/ai/profiles/list-models | List models |
| *AIProfilesApi* | [**aiProfilesListProviderModels**](#aiprofileslistprovidermodels) | **POST** /api/2.0/ai/profiles/list-provider-models | List provider models |
| *AIProfilesApi* | [**aiProfilesTestConnection**](#aiprofilestestconnection) | **POST** /api/2.0/ai/profiles/test-connection | Test connection |
| *AIProfilesApi* | [**aiProfilesUpdate**](#aiprofilesupdate) | **PUT** /api/2.0/ai/profiles/update | Update |
| *AIPromptsApi* | [**aiPromptsCreate**](#aipromptscreate) | **POST** /api/2.0/ai/prompts/create | Create |
| *AIPromptsApi* | [**aiPromptsCreateFolder**](#aipromptscreatefolder) | **POST** /api/2.0/ai/prompts/create-folder | Create folder |
| *AIPromptsApi* | [**aiPromptsDelete**](#aipromptsdelete) | **DELETE** /api/2.0/ai/prompts/delete | Delete |
| *AIPromptsApi* | [**aiPromptsDeleteFolder**](#aipromptsdeletefolder) | **DELETE** /api/2.0/ai/prompts/delete-folder | Delete folder |
| *AIPromptsApi* | [**aiPromptsExport**](#aipromptsexport) | **GET** /api/2.0/ai/prompts/export | Export |
| *AIPromptsApi* | [**aiPromptsGetById**](#aipromptsgetbyid) | **GET** /api/2.0/ai/prompts/get-by-id | Get by id |
| *AIPromptsApi* | [**aiPromptsGetFolderById**](#aipromptsgetfolderbyid) | **GET** /api/2.0/ai/prompts/get-folder-by-id | Get folder by id |
| *AIPromptsApi* | [**aiPromptsImportBundle**](#aipromptsimportbundle) | **POST** /api/2.0/ai/prompts/import-bundle | Import bundle |
| *AIPromptsApi* | [**aiPromptsList**](#aipromptslist) | **GET** /api/2.0/ai/prompts/list | List |
| *AIPromptsApi* | [**aiPromptsListFolders**](#aipromptslistfolders) | **GET** /api/2.0/ai/prompts/list-folders | List folders |
| *AIPromptsApi* | [**aiPromptsMove**](#aipromptsmove) | **PUT** /api/2.0/ai/prompts/move | Move |
| *AIPromptsApi* | [**aiPromptsRenameFolder**](#aipromptsrenamefolder) | **PUT** /api/2.0/ai/prompts/rename-folder | Rename folder |
| *AIPromptsApi* | [**aiPromptsUpdate**](#aipromptsupdate) | **PUT** /api/2.0/ai/prompts/update | Update |
| *AISettingsApi* | [**aiSettingsGet**](#aisettingsget) | **GET** /api/2.0/ai/config | Get AI settings |
| *AISettingsApi* | [**aiSettingsGetUser**](#aisettingsgetuser) | **GET** /api/2.0/ai/config/user | Get user AI settings |
| *AISettingsApi* | [**aiSettingsGetVectorization**](#aisettingsgetvectorization) | **GET** /api/2.0/ai/config/vectorization | Get vectorization settings |
| *AISettingsApi* | [**aiSettingsSetUser**](#aisettingssetuser) | **PUT** /api/2.0/ai/config/user | Update user AI settings |
| *AISettingsApi* | [**aiSettingsSetVectorization**](#aisettingssetvectorization) | **PUT** /api/2.0/ai/config/vectorization | Update vectorization settings |
| *AIThreadsApi* | [**aiThreadsAppendUserMessage**](#aithreadsappendusermessage) | **POST** /api/2.0/ai/threads/append-user-message | Append user message |
| *AIThreadsApi* | [**aiThreadsClearMessages**](#aithreadsclearmessages) | **DELETE** /api/2.0/ai/threads/clear-messages | Clear messages |
| *AIThreadsApi* | [**aiThreadsCreate**](#aithreadscreate) | **POST** /api/2.0/ai/threads/create | Create |
| *AIThreadsApi* | [**aiThreadsDelete**](#aithreadsdelete) | **DELETE** /api/2.0/ai/threads/delete | Delete |
| *AIThreadsApi* | [**aiThreadsDeleteMessage**](#aithreadsdeletemessage) | **DELETE** /api/2.0/ai/threads/delete-message | Delete message |
| *AIThreadsApi* | [**aiThreadsGetById**](#aithreadsgetbyid) | **GET** /api/2.0/ai/threads/get-by-id | Get by id |
| *AIThreadsApi* | [**aiThreadsGetMessageById**](#aithreadsgetmessagebyid) | **GET** /api/2.0/ai/threads/get-message-by-id | Get message by id |
| *AIThreadsApi* | [**aiThreadsList**](#aithreadslist) | **GET** /api/2.0/ai/threads/list | List |
| *AIThreadsApi* | [**aiThreadsOpenOrCreate**](#aithreadsopenorcreate) | **POST** /api/2.0/ai/threads/open-or-create | Open or create |
| *AIThreadsApi* | [**aiThreadsReadMessages**](#aithreadsreadmessages) | **GET** /api/2.0/ai/threads/read-messages | Read messages |
| *AIThreadsApi* | [**aiThreadsRegenerateTitle**](#aithreadsregeneratetitle) | **POST** /api/2.0/ai/threads/regenerate-title | Regenerate title |
| *AIThreadsApi* | [**aiThreadsRename**](#aithreadsrename) | **PUT** /api/2.0/ai/threads/rename | Rename |
| *AIThreadsApi* | [**aiThreadsTouch**](#aithreadstouch) | **POST** /api/2.0/ai/threads/touch | Touch |
| *AIThreadsApi* | [**aiThreadsUpdateMessage**](#aithreadsupdatemessage) | **PUT** /api/2.0/ai/threads/update-message | Update message |
| *AIToolsApi* | [**aiToolsAddCustomServer**](#aitoolsaddcustomserver) | **POST** /api/2.0/ai/tools/add-custom-server | Add custom server |
| *AIToolsApi* | [**aiToolsGetAllowAlways**](#aitoolsgetallowalways) | **GET** /api/2.0/ai/tools/get-allow-always | Get allow always |
| *AIToolsApi* | [**aiToolsGetCustomServer**](#aitoolsgetcustomserver) | **GET** /api/2.0/ai/tools/get-custom-server | Get custom server |
| *AIToolsApi* | [**aiToolsGetDisabled**](#aitoolsgetdisabled) | **GET** /api/2.0/ai/tools/get-disabled | Get disabled |
| *AIToolsApi* | [**aiToolsIsAllowAlways**](#aitoolsisallowalways) | **GET** /api/2.0/ai/tools/is-allow-always | Is allow always |
| *AIToolsApi* | [**aiToolsIsToolDisabled**](#aitoolsistooldisabled) | **GET** /api/2.0/ai/tools/is-tool-disabled | Is tool disabled |
| *AIToolsApi* | [**aiToolsListCustomServers**](#aitoolslistcustomservers) | **GET** /api/2.0/ai/tools/list-custom-servers | List custom servers |
| *AIToolsApi* | [**aiToolsListSystemTools**](#aitoolslistsystemtools) | **GET** /api/2.0/ai/tools/list-system-tools | List system tools |
| *AIToolsApi* | [**aiToolsRemoveCustomServer**](#aitoolsremovecustomserver) | **DELETE** /api/2.0/ai/tools/remove-custom-server | Remove custom server |
| *AIToolsApi* | [**aiToolsReplaceAllCustomServers**](#aitoolsreplaceallcustomservers) | **PUT** /api/2.0/ai/tools/replace-all-custom-servers | Replace all custom servers |
| *AIToolsApi* | [**aiToolsSetAllowAlways**](#aitoolssetallowalways) | **PUT** /api/2.0/ai/tools/set-allow-always | Set allow always |
| *AIToolsApi* | [**aiToolsSetDisabled**](#aitoolssetdisabled) | **PUT** /api/2.0/ai/tools/set-disabled | Set disabled |
| *AIToolsApi* | [**aiToolsUpdateCustomServer**](#aitoolsupdatecustomserver) | **PUT** /api/2.0/ai/tools/update-custom-server | Update custom server |
| *AIVectorizationApi* | [**aiVectorizationStartTask**](#aivectorizationstarttask) | **POST** /api/2.0/ai/vectorization/tasks | Start a vectorization task |
| *AIWebSearchApi* | [**aiWebSearchClear**](#aiwebsearchclear) | **DELETE** /api/2.0/ai/web-search/clear | Clear |
| *AIWebSearchApi* | [**aiWebSearchConfigure**](#aiwebsearchconfigure) | **PUT** /api/2.0/ai/web-search/configure | Configure |
| *AIWebSearchApi* | [**aiWebSearchGetActiveConfig**](#aiwebsearchgetactiveconfig) | **GET** /api/2.0/ai/web-search/get-active-config | Get active config |
| *AIWebSearchApi* | [**aiWebSearchIsConfigured**](#aiwebsearchisconfigured) | **GET** /api/2.0/ai/web-search/is-configured | Is configured |
| *AIWebSearchApi* | [**aiWebSearchPassthroughContents**](#aiwebsearchpassthroughcontents) | **POST** /api/2.0/ai/websearch/v1/contents | Web page contents proxied to the portal's active web-search provider |
| *AIWebSearchApi* | [**aiWebSearchPassthroughSearch**](#aiwebsearchpassthroughsearch) | **POST** /api/2.0/ai/websearch/v1/search | Web search proxied to the portal's active web-search provider |
| *AIWebSearchApi* | [**aiWebSearchSetActiveConfig**](#aiwebsearchsetactiveconfig) | **PUT** /api/2.0/ai/web-search/set-active-config | Set active config |
| *AIWebSearchApi* | [**aiWebSearchTestConnection**](#aiwebsearchtestconnection) | **POST** /api/2.0/ai/web-search/test-connection | Test connection |



## AIAIApi

### aiAiApproveToolCall

> AiChatEvent aiAiApproveToolCall(aiAiApproveToolCall\_request)

`POST /api/2.0/ai/ai/approve-tool-call`

Approve tool call

Resumes a chat round paused on a tool call. The supplied result is persisted onto the assistant message that issued the call and the stream continues with the augmented history.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiAiApproveToolCall\_request** | body | [**aiAiApproveToolCall_request**](#model-aiaiapprovetoolcall-request-body) |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Newline-delimited stream of chat events — one JSON &#x60;ChatEvent&#x60; object per line. | [**AiChatEvent**](#model-aichatevent) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiChatEvent**](#model-aichatevent)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/x-ndjson, application/json

### aiAiDenyToolCall

> AiChatEvent aiAiDenyToolCall(AiAiToolCallData)

`POST /api/2.0/ai/ai/deny-tool-call`

Deny tool call

Denies the pending tool call and resumes the chat immediately, with &#x60;User deny tool call&#x60; standing in for the tool result.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **AiAiToolCallData** | body | [**AiAiToolCallData**](#model-aiaitoolcalldata) |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Newline-delimited stream of chat events — one JSON &#x60;ChatEvent&#x60; object per line. | [**AiChatEvent**](#model-aichatevent) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiChatEvent**](#model-aichatevent)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/x-ndjson, application/json

### aiAiRegenerateStream

> AiChatEvent aiAiRegenerateStream(aiAiRegenerateStream\_request)

`POST /api/2.0/ai/ai/regenerate-stream`

Regenerate stream

Re-rolls the last assistant reply in an existing thread: every message after the last user message (the previous reply plus any tool-call hops) is dropped and a fresh reply is streamed against the unchanged prompt. The thread must already exist and no title is generated.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiAiRegenerateStream\_request** | body | [**aiAiRegenerateStream_request**](#model-aiairegeneratestream-request-body) |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Newline-delimited stream of chat events — one JSON &#x60;ChatEvent&#x60; object per line. | [**AiChatEvent**](#model-aichatevent) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiChatEvent**](#model-aichatevent)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/x-ndjson, application/json

### aiAiSend

> AiThreadMessageLike aiAiSend(aiAiSend\_request)

`POST /api/2.0/ai/ai/send`

Send

Runs one AI action: the profile bound to &#x60;actionType&#x60; (falling back to the &#x60;Default&#x60; slot) is dispatched against a single-message history. Nothing is persisted - no thread, no title generation, no storage writes.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiAiSend\_request** | body | [**aiAiSend_request**](#model-aiaisend-request-body) |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiThreadMessageLike**](#model-aithreadmessagelike) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiThreadMessageLike**](#model-aithreadmessagelike)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

### aiAiSendCustom

> AiThreadMessageLike aiAiSendCustom(aiAiSendCustom\_request)

`POST /api/2.0/ai/ai/send-custom`

Send custom

Runs a free-form one-turn call against a caller-supplied system prompt. No thread, no history and no persistence. The profile is the explicit &#x60;profileId&#x60; when it resolves, otherwise the &#x60;Default&#x60; assignment slot.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiAiSendCustom\_request** | body | [**aiAiSendCustom_request**](#model-aiaisendcustom-request-body) |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiThreadMessageLike**](#model-aithreadmessagelike) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiThreadMessageLike**](#model-aithreadmessagelike)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

### aiAiSendWithStream

> AiChatEvent aiAiSendWithStream(AiAiSendStreamBody)

`POST /api/2.0/ai/ai/send-with-stream`

Send with stream

Starts a chat round and streams it back as newline-delimited &#x60;ChatEvent&#x60; objects. The thread is opened or created, the user message and the reply are persisted, a new thread gets a generated title, and a tool call pauses the round until it is approved or denied.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **AiAiSendStreamBody** | body | [**AiAiSendStreamBody**](#model-aiaisendstreambody) |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Newline-delimited stream of chat events — one JSON &#x60;ChatEvent&#x60; object per line. | [**AiChatEvent**](#model-aichatevent) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiChatEvent**](#model-aichatevent)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/x-ndjson, application/json

### aiAiSendWithStreamOpenAI

> AiOpenAIStreamChunk aiAiSendWithStreamOpenAI(AiAiSendStreamBody)

`POST /api/2.0/ai/ai/send-with-stream-openai`

Send with stream open ai

The same chat round as &#x60;send-with-stream&#x60;, re-encoded as an OpenAI Chat Completions stream of &#x60;chat.completion.chunk&#x60; objects. Storage, title generation and tool-call pauses are identical - only the wire shape differs; a tool call ends the stream with &#x60;finish_reason: tool_calls&#x60;.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **AiAiSendStreamBody** | body | [**AiAiSendStreamBody**](#model-aiaisendstreambody) |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Server-sent events stream of OpenAI &#x60;chat.completion.chunk&#x60; objects, terminated by a &#x60;[DONE]&#x60; sentinel. | [**AiOpenAIStreamChunk**](#model-aiopenaistreamchunk) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiOpenAIStreamChunk**](#model-aiopenaistreamchunk)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: text/event-stream, application/json

## AIAgentsApi

### aiAgentsCreate

> AiFolderIntegerWrapper aiAgentsCreate(aiAgentsCreate\_request)

`POST /api/2.0/ai/agents`

Create an agent

Creates an AI agent room in the .NET AI service and binds the supplied &#x60;profileId&#x60; to it as a &#x60;Chat&#x60; assignment. The instruction is stored on the room as a prompt-only chat setting; a failed binding is reported as an error even though the room already exists.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiAgentsCreate\_request** | body | [**aiAgentsCreate_request**](#model-aiagentscreate-request-body) |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiFolderIntegerWrapper**](#model-aifolderintegerwrapper) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiFolderIntegerWrapper**](#model-aifolderintegerwrapper)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

### aiAgentsDelete

> AiFileOperationWrapper aiAgentsDelete(id, aiAgentsDelete\_request)

`DELETE /api/2.0/ai/agents/{id}`

Delete an agent

Deletes an AI agent room.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **id** | path | **String** | The agent identifier. | [required] |
| **aiAgentsDelete\_request** | body | [**aiAgentsDelete_request**](#model-aiagentsdelete-request-body) |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiFileOperationWrapper**](#model-aifileoperationwrapper) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiFileOperationWrapper**](#model-aifileoperationwrapper)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

### aiAgentsGet

> AiFolderIntegerWrapper aiAgentsGet(id)

`GET /api/2.0/ai/agents/{id}`

Get an agent

Returns one AI agent room, enriched with the &#x60;profileId&#x60; bound to it so an edit form can prefill the profile selector. A missing assignment simply leaves &#x60;profileId&#x60; out.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **id** | path | **String** | The agent identifier. | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiFolderIntegerWrapper**](#model-aifolderintegerwrapper) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiFolderIntegerWrapper**](#model-aifolderintegerwrapper)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

### aiAgentsList

> AiFolderContentIntegerWrapper aiAgentsList()

`GET /api/2.0/ai/agents`

List agents

Lists the portal&#39;s AI agent rooms. Query parameters are forwarded unchanged to the .NET AI service, which answers with its folder-content payload.

#### Parameters
This endpoint does not need any parameter.

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiFolderContentIntegerWrapper**](#model-aifoldercontentintegerwrapper) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiFolderContentIntegerWrapper**](#model-aifoldercontentintegerwrapper)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

### aiAgentsNews

> AiNewItemsAgentNewItemsArrayWrapper aiAgentsNews()

`GET /api/2.0/ai/agents/news`

List agent news items

Lists the new items across the caller&#39;s AI agent rooms.

#### Parameters
This endpoint does not need any parameter.

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiNewItemsAgentNewItemsArrayWrapper**](#model-ainewitemsagentnewitemsarraywrapper) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiNewItemsAgentNewItemsArrayWrapper**](#model-ainewitemsagentnewitemsarraywrapper)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

### aiAgentsResetQuota

> AiFolderIntegerArrayWrapper aiAgentsResetQuota(aiAgentsResetQuota\_request)

`PUT /api/2.0/ai/agents/resetquota`

Reset agents&#39; quota

Resets the storage quota of the given AI agent rooms.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiAgentsResetQuota\_request** | body | [**aiAgentsResetQuota_request**](#model-aiagentsresetquota-request-body) |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiFolderIntegerArrayWrapper**](#model-aifolderintegerarraywrapper) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiFolderIntegerArrayWrapper**](#model-aifolderintegerarraywrapper)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

### aiAgentsUpdate

> AiFolderIntegerWrapper aiAgentsUpdate(id, aiAgentsUpdate\_request)

`PUT /api/2.0/ai/agents/{id}`

Update an agent

Updates an AI agent room - title, tags, instruction. &#x60;profileId&#x60; is not part of the room contract: it is stripped from the forwarded body and re-bound as the agent&#39;s assignment afterwards.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **id** | path | **String** | The agent identifier. | [required] |
| **aiAgentsUpdate\_request** | body | [**aiAgentsUpdate_request**](#model-aiagentsupdate-request-body) |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiFolderIntegerWrapper**](#model-aifolderintegerwrapper) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiFolderIntegerWrapper**](#model-aifolderintegerwrapper)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

### aiAgentsUpdateQuota

> AiFolderIntegerArrayWrapper aiAgentsUpdateQuota(aiAgentsUpdateQuota\_request)

`PUT /api/2.0/ai/agents/agentquota`

Update agents&#39; quota

Changes the storage quota of the given AI agent rooms.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiAgentsUpdateQuota\_request** | body | [**aiAgentsUpdateQuota_request**](#model-aiagentsupdatequota-request-body) |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiFolderIntegerArrayWrapper**](#model-aifolderintegerarraywrapper) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiFolderIntegerArrayWrapper**](#model-aifolderintegerarraywrapper)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

## AIAssignmentsApi

### aiAssignmentsAssign

> AiAssignmentMutationResult aiAssignmentsAssign(aiAssignmentsAssign\_request)

`PUT /api/2.0/ai/assignments/assign`

Assign

Binds a profile to an AI action, creating the assignment or updating it in place. The profile&#39;s declared capabilities are validated against the action, except for the &#x60;Default&#x60; slot.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiAssignmentsAssign\_request** | body | [**aiAssignmentsAssign_request**](#model-aiassignmentsassign-request-body) |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiAssignmentMutationResult**](#model-aiassignmentmutationresult) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiAssignmentMutationResult**](#model-aiassignmentmutationresult)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

### aiAssignmentsBulkAssign

> AiBulkAssignmentResult aiAssignmentsBulkAssign(request\_body)

`PUT /api/2.0/ai/assignments/bulk-assign`

Bulk assign

Applies many action-to-profile bindings at once. Every entry is validated first and nothing is written if any of them fails, so the assignment set is never left half-written.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **request\_body** | body | **Map** |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiBulkAssignmentResult**](#model-aibulkassignmentresult) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiBulkAssignmentResult**](#model-aibulkassignmentresult)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

### aiAssignmentsCascadeProfileDelete

> AiSuccessResponse aiAssignmentsCascadeProfileDelete(body)

`DELETE /api/2.0/ai/assignments/cascade-profile-delete`

Cascade profile delete

Cleans up the assignments pointing at a profile that is about to be deleted: the &#x60;Default&#x60; slot is promoted to the first remaining profile (or dropped when none is left), and every other slot holding that profile is unbound.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **body** | body | **String** |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiSuccessResponse**](#model-aisuccessresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiSuccessResponse**](#model-aisuccessresponse)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

### aiAssignmentsGetAllAssignments

> Map aiAssignmentsGetAllAssignments(entityId)

`GET /api/2.0/ai/assignments/get-all-assignments`

Get all assignments

Returns the full action-to-profile assignment map of the scope.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **entityId** | query | **String** | The DocSpace entity the request is scoped to - the room, folder or agent workspace the chat is invoked from. Omit for the portal-wide scope. | [optional] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | **Map** | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

**Map**

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

### aiAssignmentsGetAssignment

> String aiAssignmentsGetAssignment(actionType)

`GET /api/2.0/ai/assignments/get-assignment`

Get assignment

Returns the profile bound to one AI action, without the &#x60;Default&#x60; fallback.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **actionType** | query | **String** | The AI action the request applies to - one of Default, Chat, Code, Summarization, Translation, TextAnalyze, ImageGeneration, OCR, Vision. | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | **String** | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

**String**

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

### aiAssignmentsResolveForAction

> AiResolvedAssignment aiAssignmentsResolveForAction(actionType, entityId)

`GET /api/2.0/ai/assignments/resolve-for-action`

Resolve for action

Resolves the profile bound to an AI action, falling back to the &#x60;Default&#x60; slot when the action itself has none. Fails when neither slot is set or the bound profile no longer exists - use &#x60;try-resolve-for-action&#x60; for an empty answer instead.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **actionType** | query | **String** | The AI action the request applies to - one of Default, Chat, Code, Summarization, Translation, TextAnalyze, ImageGeneration, OCR, Vision. | [required] |
| **entityId** | query | **String** | The DocSpace entity the request is scoped to - the room, folder or agent workspace the chat is invoked from. Omit for the portal-wide scope. | [optional] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiResolvedAssignment**](#model-airesolvedassignment) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiResolvedAssignment**](#model-airesolvedassignment)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

### aiAssignmentsTryResolveForAction

> AiResolvedAssignment aiAssignmentsTryResolveForAction(actionType, entityId)

`GET /api/2.0/ai/assignments/try-resolve-for-action`

Try resolve for action

Resolves the profile bound to an AI action exactly like &#x60;resolve-for-action&#x60;, but answers with an empty result instead of failing when nothing is configured.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **actionType** | query | **String** | The AI action the request applies to - one of Default, Chat, Code, Summarization, Translation, TextAnalyze, ImageGeneration, OCR, Vision. | [required] |
| **entityId** | query | **String** | The DocSpace entity the request is scoped to - the room, folder or agent workspace the chat is invoked from. Omit for the portal-wide scope. | [optional] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiResolvedAssignment**](#model-airesolvedassignment) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiResolvedAssignment**](#model-airesolvedassignment)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

### aiAssignmentsUnassign

> AiSuccessResponse aiAssignmentsUnassign(body)

`DELETE /api/2.0/ai/assignments/unassign`

Unassign

Removes the profile binding of an AI action. Does nothing when that slot is already empty.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **body** | body | **String** |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiSuccessResponse**](#model-aisuccessresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiSuccessResponse**](#model-aisuccessresponse)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

## AIAttachmentsApi

### aiAttachmentsDelete

> AiSuccessResponse aiAttachmentsDelete(body)

`DELETE /api/2.0/ai/attachments/delete`

Delete

Permanently deletes one attachment, whether it is still a draft or already linked to a message.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **body** | body | **String** |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiSuccessResponse**](#model-aisuccessresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiSuccessResponse**](#model-aisuccessresponse)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

### aiAttachmentsDeleteMany

> AiSuccessResponse aiAttachmentsDeleteMany(request\_body)

`DELETE /api/2.0/ai/attachments/delete-many`

Delete many

Permanently deletes a batch of attachments in a single round trip.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **request\_body** | body | **List** |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiSuccessResponse**](#model-aisuccessresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiSuccessResponse**](#model-aisuccessresponse)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

### aiAttachmentsGet

> AiAttachment aiAttachmentsGet(body)

`POST /api/2.0/ai/attachments/get`

Get

Returns one attachment by identifier.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **body** | body | **String** |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiAttachment**](#model-aiattachment) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiAttachment**](#model-aiattachment)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

### aiAttachmentsGetMany

> List aiAttachmentsGetMany(request\_body)

`POST /api/2.0/ai/attachments/get-many`

Get many

Returns a batch of attachments, preserving the requested order; an identifier that no longer exists comes back empty.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **request\_body** | body | **List** |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**List**](#model-aiattachment) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**List**](#model-aiattachment)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

### aiAttachmentsLinkToMessage

> AiSuccessResponse aiAttachmentsLinkToMessage(aiAttachmentsLinkToMessage\_request)

`POST /api/2.0/ai/attachments/link-to-message`

Link to message

Binds draft attachments to the chat message that owns them, once that message has been persisted, so deleting the message removes them too. Identifiers that no longer exist are skipped.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiAttachmentsLinkToMessage\_request** | body | [**aiAttachmentsLinkToMessage_request**](#model-aiattachmentslinktomessage-request-body) |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiSuccessResponse**](#model-aisuccessresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiSuccessResponse**](#model-aisuccessresponse)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

### aiAttachmentsSaveFile

> AiAttachment aiAttachmentsSaveFile(aiAttachmentsSaveFile\_request)

`POST /api/2.0/ai/attachments/save-file`

Save file

Stores one file attachment as a draft, carrying the host-extracted text of the file. Prefer &#x60;save-files-many&#x60; when adding several files at once so they land as one round trip.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiAttachmentsSaveFile\_request** | body | [**aiAttachmentsSaveFile_request**](#model-aiattachmentssavefile-request-body) |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiAttachment**](#model-aiattachment) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiAttachment**](#model-aiattachment)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

### aiAttachmentsSaveFilesMany

> List aiAttachmentsSaveFilesMany(aiAttachmentsSaveFilesMany\_request)

`POST /api/2.0/ai/attachments/save-files-many`

Save files many

Stores a batch of file attachments as drafts in a single round trip. The returned records keep the order of the input.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiAttachmentsSaveFilesMany\_request** | body | [**aiAttachmentsSaveFilesMany_request**](#model-aiattachmentssavefilesmany-request-body) |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**List**](#model-aiattachment) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**List**](#model-aiattachment)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

## AIEditorToolsApi

### aiEditorToolsCall

> AiSuccessResponse aiEditorToolsCall(request\_body)

`POST /api/2.0/ai/editor-tools/call`

Execute a DocSpace tool on behalf of the editor AI plugin

Executes one DocSpace tool on behalf of the document editor&#39;s AI plugin, server-side and with the caller&#39;s forwarded credentials. Whatever the tool produced is returned for the plugin to relay to the model; a failure comes back as an error payload.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **request\_body** | body | **Map** |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiSuccessResponse**](#model-aisuccessresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiSuccessResponse**](#model-aisuccessresponse)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

### aiEditorToolsList

> AiSuccessResponse aiEditorToolsList()

`GET /api/2.0/ai/editor-tools/list`

Sanitized DocSpace tool catalog for the editor AI plugin

Returns the sanitized catalog of DocSpace tools available to the document editor&#39;s AI plugin - the same composed tool set the DocSpace chat sees, minus the web-search pair the editor already has through its own passthrough. Only the name, description, parameters and approval flag of each tool are exposed; transport details never reach the browser.

#### Parameters
This endpoint does not need any parameter.

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiSuccessResponse**](#model-aisuccessresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiSuccessResponse**](#model-aisuccessresponse)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

## AIExportApi

### aiExportTextToDocx

> aiExportTextToDocx_200_response aiExportTextToDocx(aiExportTextToDocx\_request)

`POST /api/2.0/ai/text-to-docx`

Start markdown → docx export

Starts an asynchronous markdown-to-docx export. The response only acknowledges the task: the AI Worker converts the content and saves the .docx into the target folder (an agent room resolves to its result-storage subfolder), and completion reaches the client as the usual folder-modified socket event.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiExportTextToDocx\_request** | body | [**aiExportTextToDocx_request**](#model-aiexporttexttodocx-request-body) |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**aiExportTextToDocx_200_response**](#model-aiexporttexttodocx-200-response) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**aiExportTextToDocx_200_response**](#model-aiexporttexttodocx-200-response)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

## AIOpenAIPassthroughApi

### aiOpenaiChatCompletions

> AiSuccessResponse aiOpenaiChatCompletions(profileId, request\_body)

`POST /api/2.0/ai/openai/{profileId}/v1/chat/completions`

OpenAI-compatible chat completions proxied to the profile&#39;s provider

OpenAI-compatible chat completions for the document editor&#39;s AI plugin. The profile is resolved server-side, its credentials are attached, and the body is forwarded to the provider verbatim - the payload is owned by the plugin&#39;s SDK on one end and the provider on the other. A client disconnect cancels the provider call.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **profileId** | path | **String** | The AI provider profile identifier. | [required] |
| **request\_body** | body | **Map** |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiSuccessResponse**](#model-aisuccessresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiSuccessResponse**](#model-aisuccessresponse)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

### aiOpenaiImagesGenerations

> AiSuccessResponse aiOpenaiImagesGenerations(profileId, request\_body)

`POST /api/2.0/ai/openai/{profileId}/v1/images/generations`

OpenAI-compatible image generation proxied to the profile&#39;s provider

OpenAI-compatible image generation for the document editor&#39;s AI plugin. As with the chat-completions passthrough, the profile&#39;s credentials are attached server-side and the body reaches the provider unchanged.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **profileId** | path | **String** | The AI provider profile identifier. | [required] |
| **request\_body** | body | **Map** |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiSuccessResponse**](#model-aisuccessresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiSuccessResponse**](#model-aisuccessresponse)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

## AIPreferencesApi

### aiPreferencesClearDeepMode

> AiSuccessResponse aiPreferencesClearDeepMode(body)

`DELETE /api/2.0/ai/preferences/clear-deep-mode`

Clear deep mode

Drops the persisted deep-mode toggle of the scope, so later reads fall back to the configured default.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **body** | body | **String** |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiSuccessResponse**](#model-aisuccessresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiSuccessResponse**](#model-aisuccessresponse)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

### aiPreferencesGetDeepMode

> Boolean aiPreferencesGetDeepMode(entityId)

`GET /api/2.0/ai/preferences/get-deep-mode`

Get deep mode

Returns the deep-mode toggle of the scope, falling back to the configured default when nothing has been persisted.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **entityId** | query | **String** | The DocSpace entity the request is scoped to - the room, folder or agent workspace the chat is invoked from. Omit for the portal-wide scope. | [optional] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | **Boolean** | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

**Boolean**

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

### aiPreferencesIsDeepModeSet

> Boolean aiPreferencesIsDeepModeSet(entityId)

`GET /api/2.0/ai/preferences/is-deep-mode-set`

Is deep mode set

Tells whether the scope has an explicitly persisted deep-mode value, whichever way that value is set.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **entityId** | query | **String** | The DocSpace entity the request is scoped to - the room, folder or agent workspace the chat is invoked from. Omit for the portal-wide scope. | [optional] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | **Boolean** | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

**Boolean**

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

### aiPreferencesSetDeepMode

> AiSuccessResponse aiPreferencesSetDeepMode(aiPreferencesSetDeepMode\_request)

`PUT /api/2.0/ai/preferences/set-deep-mode`

Set deep mode

Persists the deep-mode toggle of the scope. Idempotent - there is no need to check whether a value already exists.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiPreferencesSetDeepMode\_request** | body | [**aiPreferencesSetDeepMode_request**](#model-aipreferencessetdeepmode-request-body) |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiSuccessResponse**](#model-aisuccessresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiSuccessResponse**](#model-aisuccessresponse)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

## AIProfilesApi

### aiProfilesCreate

> AiProfileMutationResult aiProfilesCreate(AiCreateProfileInput)

`POST /api/2.0/ai/profiles/create`

Create

Creates an AI provider profile. The name must be unique and the credentials are validated against the provider before the profile is stored; the portal&#39;s first profile also takes the &#x60;Default&#x60; assignment slot.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **AiCreateProfileInput** | body | [**AiCreateProfileInput**](#model-aicreateprofileinput) |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiProfileMutationResult**](#model-aiprofilemutationresult) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiProfileMutationResult**](#model-aiprofilemutationresult)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

### aiProfilesDelete

> AiSuccessResponse aiProfilesDelete(body)

`DELETE /api/2.0/ai/profiles/delete`

Delete

Deletes an AI provider profile and cleans up the assignments pointing at it - the &#x60;Default&#x60; slot moves to the first remaining profile, the other slots are unbound.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **body** | body | **String** |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiSuccessResponse**](#model-aisuccessresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiSuccessResponse**](#model-aisuccessresponse)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

### aiProfilesGetById

> aiProfilesGetById_200_response aiProfilesGetById(id)

`GET /api/2.0/ai/profiles/get-by-id`

Get by id

Returns one AI provider profile, or an empty result when the identifier is unknown.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **id** | query | **String** | The AI provider profile identifier. | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**aiProfilesGetById_200_response**](#model-aiprofilesgetbyid-200-response) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**aiProfilesGetById_200_response**](#model-aiprofilesgetbyid-200-response)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

### aiProfilesList

> List aiProfilesList()

`GET /api/2.0/ai/profiles/list`

List

Lists the portal&#39;s AI provider profiles.

#### Parameters
This endpoint does not need any parameter.

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**List**](#model-aiprofile) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**List**](#model-aiprofile)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

### aiProfilesListModels

> List aiProfilesListModels(profileId)

`GET /api/2.0/ai/profiles/list-models`

List models

Lists the models the given profile&#39;s provider offers, as reported by the provider itself.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **profileId** | query | **String** | The AI provider profile identifier. | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**List**](#model-aimodel) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**List**](#model-aimodel)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

### aiProfilesListProviderModels

> List aiProfilesListProviderModels(aiProfilesListProviderModels\_request)

`POST /api/2.0/ai/profiles/list-provider-models`

List provider models

Lists the models a provider offers for the supplied endpoint and key, before any profile is created from them.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiProfilesListProviderModels\_request** | body | [**aiProfilesListProviderModels_request**](#model-aiprofileslistprovidermodels-request-body) |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**List**](#model-aimodel) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**List**](#model-aimodel)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

### aiProfilesTestConnection

> aiProfilesTestConnection_200_response aiProfilesTestConnection(body)

`POST /api/2.0/ai/profiles/test-connection`

Test connection

Checks a stored profile&#39;s credentials against its provider and reports the provider&#39;s own error when the call fails. Nothing is written.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **body** | body | **String** |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**aiProfilesTestConnection_200_response**](#model-aiprofilestestconnection-200-response) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**aiProfilesTestConnection_200_response**](#model-aiprofilestestconnection-200-response)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

### aiProfilesUpdate

> AiProfileMutationResult aiProfilesUpdate(AiProfile)

`PUT /api/2.0/ai/profiles/update`

Update

Updates an AI provider profile, re-checking name uniqueness and the provider credentials.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **AiProfile** | body | [**AiProfile**](#model-aiprofile) |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiProfileMutationResult**](#model-aiprofilemutationresult) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiProfileMutationResult**](#model-aiprofilemutationresult)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

## AIPromptsApi

### aiPromptsCreate

> AiPromptMutationResult aiPromptsCreate(AiCreatePromptInput)

`POST /api/2.0/ai/prompts/create`

Create

Saves a new prompt. The name must be non-empty and unique inside its folder, and &#x60;folderId&#x60; must point at an existing folder - omit it for the root.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **AiCreatePromptInput** | body | [**AiCreatePromptInput**](#model-aicreatepromptinput) |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiPromptMutationResult**](#model-aipromptmutationresult) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiPromptMutationResult**](#model-aipromptmutationresult)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

### aiPromptsCreateFolder

> AiFolderMutationResult aiPromptsCreateFolder(body)

`POST /api/2.0/ai/prompts/create-folder`

Create folder

Creates a prompt folder. The name must be non-empty and unique across the portal - prompt folders do not nest.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **body** | body | **String** |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiFolderMutationResult**](#model-aifoldermutationresult) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiFolderMutationResult**](#model-aifoldermutationresult)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

### aiPromptsDelete

> AiSuccessResponse aiPromptsDelete(body)

`DELETE /api/2.0/ai/prompts/delete`

Delete

Deletes a saved prompt. Does nothing when it no longer exists.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **body** | body | **String** |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiSuccessResponse**](#model-aisuccessresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiSuccessResponse**](#model-aisuccessresponse)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

### aiPromptsDeleteFolder

> AiSuccessResponse aiPromptsDeleteFolder(body)

`DELETE /api/2.0/ai/prompts/delete-folder`

Delete folder

Deletes a prompt folder together with the prompts inside it.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **body** | body | **String** |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiSuccessResponse**](#model-aisuccessresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiSuccessResponse**](#model-aisuccessresponse)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

### aiPromptsExport

> AiPromptBundle aiPromptsExport()

`GET /api/2.0/ai/prompts/export`

Export

Builds a self-contained, versioned bundle of every saved prompt and folder, ready for &#x60;import-bundle&#x60;.

#### Parameters
This endpoint does not need any parameter.

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiPromptBundle**](#model-aipromptbundle) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiPromptBundle**](#model-aipromptbundle)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

### aiPromptsGetById

> AiPrompt aiPromptsGetById(id)

`GET /api/2.0/ai/prompts/get-by-id`

Get by id

Returns one saved prompt, or an empty result when the identifier is unknown.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **id** | query | **String** | The saved prompt identifier. | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiPrompt**](#model-aiprompt) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiPrompt**](#model-aiprompt)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

### aiPromptsGetFolderById

> AiPromptFolder aiPromptsGetFolderById(id)

`GET /api/2.0/ai/prompts/get-folder-by-id`

Get folder by id

Returns one prompt folder, or an empty result when the identifier is unknown.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **id** | query | **String** | The prompt folder identifier. | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiPromptFolder**](#model-aipromptfolder) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiPromptFolder**](#model-aipromptfolder)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

### aiPromptsImportBundle

> AiImportResult aiPromptsImportBundle(aiPromptsImportBundle\_request)

`POST /api/2.0/ai/prompts/import-bundle`

Import bundle

Restores a prompt bundle. &#x60;replace&#x60; wipes the current prompts and folders before writing the bundle, &#x60;merge&#x60; writes the bundle on top of what is already there; both validate the folder references inside the bundle before any write, so a corrupt bundle is rejected whole.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiPromptsImportBundle\_request** | body | [**aiPromptsImportBundle_request**](#model-aipromptsimportbundle-request-body) |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiImportResult**](#model-aiimportresult) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiImportResult**](#model-aiimportresult)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

### aiPromptsList

> List aiPromptsList(folderId)

`GET /api/2.0/ai/prompts/list`

List

Lists saved prompts. Scope the answer to one folder, ask for the root-level prompts only, or omit the folder to get every prompt newest first.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **folderId** | query | **String** | The prompt folder identifier. Omit to list the prompts that sit outside any folder. | [optional] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**List**](#model-aiprompt) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**List**](#model-aiprompt)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

### aiPromptsListFolders

> List aiPromptsListFolders()

`GET /api/2.0/ai/prompts/list-folders`

List folders

Lists the prompt folders, newest first.

#### Parameters
This endpoint does not need any parameter.

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**List**](#model-aipromptfolder) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**List**](#model-aipromptfolder)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

### aiPromptsMove

> AiPromptMutationResult aiPromptsMove(aiPromptsMove\_request)

`PUT /api/2.0/ai/prompts/move`

Move

Moves a saved prompt into another folder, or to the root. The name is re-validated in the target folder, so the move fails when a prompt of that name is already there.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiPromptsMove\_request** | body | [**aiPromptsMove_request**](#model-aipromptsmove-request-body) |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiPromptMutationResult**](#model-aipromptmutationresult) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiPromptMutationResult**](#model-aipromptmutationresult)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

### aiPromptsRenameFolder

> AiFolderMutationResult aiPromptsRenameFolder(aiPromptsRenameFolder\_request)

`PUT /api/2.0/ai/prompts/rename-folder`

Rename folder

Renames a prompt folder, validating the new name against the existing folders.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiPromptsRenameFolder\_request** | body | [**aiPromptsRenameFolder_request**](#model-aipromptsrenamefolder-request-body) |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiFolderMutationResult**](#model-aifoldermutationresult) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiFolderMutationResult**](#model-aifoldermutationresult)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

### aiPromptsUpdate

> AiPromptMutationResult aiPromptsUpdate(aiPromptsUpdate\_request)

`PUT /api/2.0/ai/prompts/update`

Update

Updates a saved prompt. The name and the folder reference are re-validated whenever either of them changes.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiPromptsUpdate\_request** | body | [**aiPromptsUpdate_request**](#model-aipromptsupdate-request-body) |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiPromptMutationResult**](#model-aipromptmutationresult) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiPromptMutationResult**](#model-aipromptmutationresult)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

## AISettingsApi

### aiSettingsGet

> AiAiSettingsWrapper aiSettingsGet()

`GET /api/2.0/ai/config`

Get AI settings

Reports the portal&#39;s combined AI configuration and readiness.

#### Parameters
This endpoint does not need any parameter.

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiAiSettingsWrapper**](#model-aiaisettingswrapper) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiAiSettingsWrapper**](#model-aiaisettingswrapper)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

### aiSettingsGetUser

> AiAiUserSettingsWrapper aiSettingsGetUser()

`GET /api/2.0/ai/config/user`

Get user AI settings

Returns the current user&#39;s AI settings.

#### Parameters
This endpoint does not need any parameter.

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiAiUserSettingsWrapper**](#model-aiaiusersettingswrapper) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiAiUserSettingsWrapper**](#model-aiaiusersettingswrapper)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

### aiSettingsGetVectorization

> AiVectorizationSettingsWrapper aiSettingsGetVectorization()

`GET /api/2.0/ai/config/vectorization`

Get vectorization settings

Returns the portal&#39;s vectorization settings.

#### Parameters
This endpoint does not need any parameter.

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiVectorizationSettingsWrapper**](#model-aivectorizationsettingswrapper) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiVectorizationSettingsWrapper**](#model-aivectorizationsettingswrapper)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

### aiSettingsSetUser

> AiAiUserSettingsWrapper aiSettingsSetUser(request\_body)

`PUT /api/2.0/ai/config/user`

Update user AI settings

Updates the current user&#39;s AI settings.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **request\_body** | body | **Map** |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiAiUserSettingsWrapper**](#model-aiaiusersettingswrapper) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiAiUserSettingsWrapper**](#model-aiaiusersettingswrapper)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

### aiSettingsSetVectorization

> AiVectorizationSettingsWrapper aiSettingsSetVectorization(request\_body)

`PUT /api/2.0/ai/config/vectorization`

Update vectorization settings

Updates the portal&#39;s vectorization settings.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **request\_body** | body | **Map** |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiVectorizationSettingsWrapper**](#model-aivectorizationsettingswrapper) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiVectorizationSettingsWrapper**](#model-aivectorizationsettingswrapper)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

## AIThreadsApi

### aiThreadsAppendUserMessage

> AiThreadMessageLike aiThreadsAppendUserMessage(aiThreadsAppendUserMessage\_request)

`POST /api/2.0/ai/threads/append-user-message`

Append user message

Persists a user message in a thread and bumps the thread&#39;s last-edit date so it resurfaces in the sidebar. Optionally rebinds the thread to another profile when the model changed mid-conversation.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiThreadsAppendUserMessage\_request** | body | [**aiThreadsAppendUserMessage_request**](#model-aithreadsappendusermessage-request-body) |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiThreadMessageLike**](#model-aithreadmessagelike) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiThreadMessageLike**](#model-aithreadmessagelike)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

### aiThreadsClearMessages

> AiSuccessResponse aiThreadsClearMessages(body)

`DELETE /api/2.0/ai/threads/clear-messages`

Clear messages

Drops every message of a thread while keeping the thread itself, and bumps its last-edit date.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **body** | body | **String** |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiSuccessResponse**](#model-aisuccessresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiSuccessResponse**](#model-aisuccessresponse)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

### aiThreadsCreate

> AiThread aiThreadsCreate(aiThreadsCreate\_request)

`POST /api/2.0/ai/threads/create`

Create

Creates a chat thread with a caller-supplied title. Use &#x60;open-or-create&#x60; instead when the title should be generated from the first user message.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiThreadsCreate\_request** | body | [**aiThreadsCreate_request**](#model-aithreadscreate-request-body) |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiThread**](#model-aithread) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiThread**](#model-aithread)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

### aiThreadsDelete

> AiSuccessResponse aiThreadsDelete(body)

`DELETE /api/2.0/ai/threads/delete`

Delete

Deletes a chat thread together with its messages.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **body** | body | **String** |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiSuccessResponse**](#model-aisuccessresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiSuccessResponse**](#model-aisuccessresponse)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

### aiThreadsDeleteMessage

> AiSuccessResponse aiThreadsDeleteMessage(body)

`DELETE /api/2.0/ai/threads/delete-message`

Delete message

Deletes one chat message, leaving the rest of the thread untouched.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **body** | body | **String** |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiSuccessResponse**](#model-aisuccessresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiSuccessResponse**](#model-aisuccessresponse)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

### aiThreadsGetById

> AiThread aiThreadsGetById(threadId)

`GET /api/2.0/ai/threads/get-by-id`

Get by id

Returns one chat thread, or an empty result when the identifier is unknown.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **threadId** | query | **String** | The chat thread identifier. | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiThread**](#model-aithread) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiThread**](#model-aithread)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

### aiThreadsGetMessageById

> AiThreadMessageLike aiThreadsGetMessageById(messageId)

`GET /api/2.0/ai/threads/get-message-by-id`

Get message by id

Returns one chat message by its globally unique identifier.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **messageId** | query | **String** | The globally unique chat message identifier. | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiThreadMessageLike**](#model-aithreadmessagelike) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiThreadMessageLike**](#model-aithreadmessagelike)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

### aiThreadsList

> List aiThreadsList(entityId, count, cursor, query)

`GET /api/2.0/ai/threads/list`

List

Lists the chat threads of the scope, most recently edited first. Supports cursor pagination and a server-side case-insensitive title search.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **entityId** | query | **String** | The DocSpace entity the request is scoped to - the room, folder or agent workspace the chat is invoked from. Omit for the portal-wide scope. | [optional] |
| **count** | query | **String** | The maximum number of items to return in one page. | [optional] |
| **cursor** | query | **String** | The keyset pagination cursor: the JSON-encoded sort key of the last item already received. Omit for the first page. | [optional] |
| **query** | query | **String** | The full-text query the thread list is filtered by. | [optional] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**List**](#model-aithread) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**List**](#model-aithread)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

### aiThreadsOpenOrCreate

> AiOpenOrCreateResult aiThreadsOpenOrCreate(aiThreadsOpenOrCreate\_request)

`POST /api/2.0/ai/threads/open-or-create`

Open or create

Opens a chat thread and returns its history, or creates one with a title generated from the supplied first message. That first message is not persisted - the caller decides whether to follow up with &#x60;append-user-message&#x60;.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiThreadsOpenOrCreate\_request** | body | [**aiThreadsOpenOrCreate_request**](#model-aithreadsopenorcreate-request-body) |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiOpenOrCreateResult**](#model-aiopenorcreateresult) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiOpenOrCreateResult**](#model-aiopenorcreateresult)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

### aiThreadsReadMessages

> List aiThreadsReadMessages(threadId, count, cursor, direction)

`GET /api/2.0/ai/threads/read-messages`

Read messages

Reads the messages of a thread, with the same cursor pagination as the thread list.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **threadId** | query | **String** | The chat thread identifier. | [required] |
| **count** | query | **String** | The maximum number of items to return in one page. | [optional] |
| **cursor** | query | **String** | The keyset pagination cursor: the JSON-encoded sort key of the last item already received. Omit for the first page. | [optional] |
| **direction** | query | **String** | The order the message page is read in. Only desc turns the read around and pages back from the newest message; omit for the forward read. | [optional] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**List**](#model-aithreadmessagelike) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**List**](#model-aithreadmessagelike)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

### aiThreadsRegenerateTitle

> String aiThreadsRegenerateTitle(aiThreadsRegenerateTitle\_request)

`POST /api/2.0/ai/threads/regenerate-title`

Regenerate title

Generates a fresh title from the thread&#39;s first user message and persists it. Fails when the thread has no user message yet.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiThreadsRegenerateTitle\_request** | body | [**aiThreadsRegenerateTitle_request**](#model-aithreadsregeneratetitle-request-body) |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | **String** | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

**String**

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

### aiThreadsRename

> AiSuccessResponse aiThreadsRename(aiThreadsRename\_request)

`PUT /api/2.0/ai/threads/rename`

Rename

Renames a chat thread and bumps its last-edit date so the new title shows up in the sidebar.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiThreadsRename\_request** | body | [**aiThreadsRename_request**](#model-aithreadsrename-request-body) |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiSuccessResponse**](#model-aisuccessresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiSuccessResponse**](#model-aisuccessresponse)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

### aiThreadsTouch

> AiSuccessResponse aiThreadsTouch(aiThreadsTouch\_request)

`POST /api/2.0/ai/threads/touch`

Touch

Bumps a thread&#39;s last-edit date, and optionally rebinds it to another profile, when something other than a new message - a model switch, say - should resurface it.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiThreadsTouch\_request** | body | [**aiThreadsTouch_request**](#model-aithreadstouch-request-body) |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiSuccessResponse**](#model-aisuccessresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiSuccessResponse**](#model-aisuccessresponse)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

### aiThreadsUpdateMessage

> AiSuccessResponse aiThreadsUpdateMessage(aiThreadsUpdateMessage\_request)

`PUT /api/2.0/ai/threads/update-message`

Update message

Replaces the content of a chat message - used by the edit and regenerate flows that change a message outside the streaming lifecycle.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiThreadsUpdateMessage\_request** | body | [**aiThreadsUpdateMessage_request**](#model-aithreadsupdatemessage-request-body) |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiSuccessResponse**](#model-aisuccessresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiSuccessResponse**](#model-aisuccessresponse)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

## AIToolsApi

### aiToolsAddCustomServer

> AiToolsMutationResult aiToolsAddCustomServer(aiToolsAddCustomServer\_request)

`POST /api/2.0/ai/tools/add-custom-server`

Add custom server

Registers a custom MCP server in the scope under the given name.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiToolsAddCustomServer\_request** | body | [**aiToolsAddCustomServer_request**](#model-aitoolsaddcustomserver-request-body) |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiToolsMutationResult**](#model-aitoolsmutationresult) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiToolsMutationResult**](#model-aitoolsmutationresult)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

### aiToolsGetAllowAlways

> List aiToolsGetAllowAlways(entityId)

`GET /api/2.0/ai/tools/get-allow-always`

Get allow always

Lists the tools on the always-allow list of the scope.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **entityId** | query | **String** | The DocSpace entity the request is scoped to - the room, folder or agent workspace the chat is invoked from. Omit for the portal-wide scope. | [optional] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | **List** | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

**List**

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

### aiToolsGetCustomServer

> Object aiToolsGetCustomServer(name, entityId)

`GET /api/2.0/ai/tools/get-custom-server`

Get custom server

Returns the configuration of one custom MCP server, or an empty result when it is not registered.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **name** | query | **String** | The custom MCP server name. | [required] |
| **entityId** | query | **String** | The DocSpace entity the request is scoped to - the room, folder or agent workspace the chat is invoked from. Omit for the portal-wide scope. | [optional] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | **Object** | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

**Object**

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

### aiToolsGetDisabled

> Map aiToolsGetDisabled(entityId)

`GET /api/2.0/ai/tools/get-disabled`

Get disabled

Returns the switched-off tools of the scope, grouped by server type.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **entityId** | query | **String** | The DocSpace entity the request is scoped to - the room, folder or agent workspace the chat is invoked from. Omit for the portal-wide scope. | [optional] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | **Map** | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

**Map**

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

### aiToolsIsAllowAlways

> Boolean aiToolsIsAllowAlways(serverType, toolName, entityId)

`GET /api/2.0/ai/tools/is-allow-always`

Is allow always

Tells whether one tool is on the always-allow list.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **serverType** | query | **String** | The MCP server type the tool belongs to. | [required] |
| **toolName** | query | **String** | The tool name. | [required] |
| **entityId** | query | **String** | The DocSpace entity the request is scoped to - the room, folder or agent workspace the chat is invoked from. Omit for the portal-wide scope. | [optional] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | **Boolean** | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

**Boolean**

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

### aiToolsIsToolDisabled

> Boolean aiToolsIsToolDisabled(serverType, toolName, entityId)

`GET /api/2.0/ai/tools/is-tool-disabled`

Is tool disabled

Tells whether one tool of a server type is switched off.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **serverType** | query | **String** | The MCP server type the tool belongs to. | [required] |
| **toolName** | query | **String** | The tool name. | [required] |
| **entityId** | query | **String** | The DocSpace entity the request is scoped to - the room, folder or agent workspace the chat is invoked from. Omit for the portal-wide scope. | [optional] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | **Boolean** | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

**Boolean**

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

### aiToolsListCustomServers

> Map aiToolsListCustomServers(entityId)

`GET /api/2.0/ai/tools/list-custom-servers`

List custom servers

Lists the custom MCP servers registered in the scope, keyed by name.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **entityId** | query | **String** | The DocSpace entity the request is scoped to - the room, folder or agent workspace the chat is invoked from. Omit for the portal-wide scope. | [optional] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | **Map** | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

**Map**

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

### aiToolsListSystemTools

> Map aiToolsListSystemTools(entityId)

`GET /api/2.0/ai/tools/list-system-tools`

List system tools

Lists the tools of the host-configured system MCP servers, grouped by server type. The servers are connected and listed server-side, so the client renders its permission cards from one request and never opens an MCP connection of its own.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **entityId** | query | **String** | The DocSpace entity the request is scoped to - the room, folder or agent workspace the chat is invoked from. Omit for the portal-wide scope. | [optional] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**Map**](#model-aitmcpitem) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

**Map**

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

### aiToolsRemoveCustomServer

> AiSuccessResponse aiToolsRemoveCustomServer(aiToolsRemoveCustomServer\_request)

`DELETE /api/2.0/ai/tools/remove-custom-server`

Remove custom server

Removes a custom MCP server from the registry.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiToolsRemoveCustomServer\_request** | body | [**aiToolsRemoveCustomServer_request**](#model-aitoolsremovecustomserver-request-body) |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiSuccessResponse**](#model-aisuccessresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiSuccessResponse**](#model-aisuccessresponse)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

### aiToolsReplaceAllCustomServers

> AiToolsBulkResult aiToolsReplaceAllCustomServers(aiToolsReplaceAllCustomServers\_request)

`PUT /api/2.0/ai/tools/replace-all-custom-servers`

Replace all custom servers

Replaces the whole custom MCP server registry of the scope with the supplied map.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiToolsReplaceAllCustomServers\_request** | body | [**aiToolsReplaceAllCustomServers_request**](#model-aitoolsreplaceallcustomservers-request-body) |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiToolsBulkResult**](#model-aitoolsbulkresult) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiToolsBulkResult**](#model-aitoolsbulkresult)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

### aiToolsSetAllowAlways

> AiSuccessResponse aiToolsSetAllowAlways(aiToolsSetAllowAlways\_request)

`PUT /api/2.0/ai/tools/set-allow-always`

Set allow always

Adds a tool to the always-allow list, or removes it - the tools on that list run without an approval dialog.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiToolsSetAllowAlways\_request** | body | [**aiToolsSetAllowAlways_request**](#model-aitoolssetallowalways-request-body) |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiSuccessResponse**](#model-aisuccessresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiSuccessResponse**](#model-aisuccessresponse)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

### aiToolsSetDisabled

> AiSuccessResponse aiToolsSetDisabled(aiToolsSetDisabled\_request)

`PUT /api/2.0/ai/tools/set-disabled`

Set disabled

Marks the listed tools of one server type as switched off, so the model is no longer offered them.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiToolsSetDisabled\_request** | body | [**aiToolsSetDisabled_request**](#model-aitoolssetdisabled-request-body) |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiSuccessResponse**](#model-aisuccessresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiSuccessResponse**](#model-aisuccessresponse)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

### aiToolsUpdateCustomServer

> AiToolsMutationResult aiToolsUpdateCustomServer(aiToolsUpdateCustomServer\_request)

`PUT /api/2.0/ai/tools/update-custom-server`

Update custom server

Updates the configuration of a registered custom MCP server.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiToolsUpdateCustomServer\_request** | body | [**aiToolsUpdateCustomServer_request**](#model-aitoolsupdatecustomserver-request-body) |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiToolsMutationResult**](#model-aitoolsmutationresult) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiToolsMutationResult**](#model-aitoolsmutationresult)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

## AIVectorizationApi

### aiVectorizationStartTask

> AiSuccessResponse aiVectorizationStartTask(request\_body)

`POST /api/2.0/ai/vectorization/tasks`

Start a vectorization task

Starts a vectorization task over the supplied portal files. The indexing itself runs asynchronously on the .NET side.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **request\_body** | body | **Map** |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiSuccessResponse**](#model-aisuccessresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiSuccessResponse**](#model-aisuccessresponse)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

## AIWebSearchApi

### aiWebSearchClear

> AiSuccessResponse aiWebSearchClear(body)

`DELETE /api/2.0/ai/web-search/clear`

Clear

Removes the web-search configuration of the scope. Does nothing when web search was not configured there.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **body** | body | **String** |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiSuccessResponse**](#model-aisuccessresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiSuccessResponse**](#model-aisuccessresponse)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

### aiWebSearchConfigure

> AiWebSearchMutationResult aiWebSearchConfigure(aiWebSearchConfigure\_request)

`PUT /api/2.0/ai/web-search/configure`

Configure

Validates a web-search configuration against the live provider and stores it only when the provider answers, replacing the previous one in a single write.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiWebSearchConfigure\_request** | body | [**aiWebSearchConfigure_request**](#model-aiwebsearchconfigure-request-body) |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiWebSearchMutationResult**](#model-aiwebsearchmutationresult) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiWebSearchMutationResult**](#model-aiwebsearchmutationresult)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

### aiWebSearchGetActiveConfig

> AiWebSearchConfig aiWebSearchGetActiveConfig(entityId)

`GET /api/2.0/ai/web-search/get-active-config`

Get active config

Returns the web-search configuration active in the scope, or an empty result when web search is not configured.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **entityId** | query | **String** | The DocSpace entity the request is scoped to - the room, folder or agent workspace the chat is invoked from. Omit for the portal-wide scope. | [optional] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiWebSearchConfig**](#model-aiwebsearchconfig) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiWebSearchConfig**](#model-aiwebsearchconfig)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

### aiWebSearchIsConfigured

> Boolean aiWebSearchIsConfigured(entityId)

`GET /api/2.0/ai/web-search/is-configured`

Is configured

Tells whether web search is configured in the scope.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **entityId** | query | **String** | The DocSpace entity the request is scoped to - the room, folder or agent workspace the chat is invoked from. Omit for the portal-wide scope. | [optional] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | **Boolean** | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

**Boolean**

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

### aiWebSearchPassthroughContents

> AiSuccessResponse aiWebSearchPassthroughContents(request\_body)

`POST /api/2.0/ai/websearch/v1/contents`

Web page contents proxied to the portal&#39;s active web-search provider

Fetches web page contents on behalf of the document editor&#39;s AI plugin, against the portal&#39;s active web-search provider, the same way as the search passthrough.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **request\_body** | body | **Map** |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiSuccessResponse**](#model-aisuccessresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiSuccessResponse**](#model-aisuccessresponse)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

### aiWebSearchPassthroughSearch

> AiSuccessResponse aiWebSearchPassthroughSearch(request\_body)

`POST /api/2.0/ai/websearch/v1/search`

Web search proxied to the portal&#39;s active web-search provider

Runs a web search on behalf of the document editor&#39;s AI plugin. The plugin only holds a placeholder configuration; the portal&#39;s active provider and its key are resolved here and never reach the browser.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **request\_body** | body | **Map** |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiSuccessResponse**](#model-aisuccessresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiSuccessResponse**](#model-aisuccessresponse)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

### aiWebSearchSetActiveConfig

> AiSuccessResponse aiWebSearchSetActiveConfig(aiWebSearchConfigure\_request)

`PUT /api/2.0/ai/web-search/set-active-config`

Set active config

Stores a web-search configuration without contacting the provider first, for forms that validate locally.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiWebSearchConfigure\_request** | body | [**aiWebSearchConfigure_request**](#model-aiwebsearchconfigure-request-body) |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiSuccessResponse**](#model-aisuccessresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**AiSuccessResponse**](#model-aisuccessresponse)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

### aiWebSearchTestConnection

> aiProfilesTestConnection_200_response aiWebSearchTestConnection(AiWebSearchConfig)

`POST /api/2.0/ai/web-search/test-connection`

Test connection

Checks a web-search configuration against the live provider without storing it - for a Test button that must not commit on success.

#### Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **AiWebSearchConfig** | body | [**AiWebSearchConfig**](#model-aiwebsearchconfig) |  | [required] |

#### Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**aiProfilesTestConnection_200_response**](#model-aiprofilestestconnection-200-response) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](#model-aierrorresponse) | - |

#### Return type

[**aiProfilesTestConnection_200_response**](#model-aiprofilestestconnection-200-response)

#### Authorization

No authorization required

#### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json


## Models


### Model AiActionType
The AI action a request or an assignment applies to. Each action has its own assignment slot; &#x60;Default&#x60; is the profile used when an action&#39;s own slot is empty.

Possible values:

- `Default`
- `Chat`
- `Code`
- `Summarization`
- `Translation`
- `TextAnalyze`
- `ImageGeneration`
- `OCR`
- `Vision`


### Model AiAgentNewItemsDto
The agent new item&#39;s information.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **agent** | [**AiFileEntryBaseDto**](#model-aifileentrybasedto) | The agent file entry. | [required] |
| **items** | [**List**](#model-aifileentrybasedto) | The list of file entry items. | [required] [nullable] |


### Model AiAiActionArgs
Wire-serializable subset of the engine&#39;s &#x60;ActionArgs&#x60; — drops the engine-injected &#x60;signal&#x60;/&#x60;fetch&#x60;; &#x60;profile&#x60;/&#x60;messages&#x60; are owned by the engine and never sent by the caller.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **tools** | [**List**](#model-aitmcpitem) | Extra tools offered to the model for this request. | [optional] |
| **isReasoning** | **Boolean** | Enable extended thinking / reasoning for this request. | [optional] |
| **prompt** | [**AiAiActionArgs_prompt**](#model-aiaiactionargsprompt) |  | [optional] |


### Model AiAiActionArgs.prompt
Override the action&#39;s baked-in system prompt (replace or append).

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **mode** | **String** |  | [required] [enum: replace, append] |
| **text** | **String** |  | [required] |


### Model AiAiSendStreamBody
Shared body of the two streaming send endpoints (&#x60;sendWithStream&#x60; and its OpenAI-framed twin) — the &#x60;Chat&#x60; action is implied, so there is no &#x60;actionType&#x60;.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **threadId** | **String** | Target thread; a new one is created (with an auto title) when omitted. | [optional] |
| **userMessage** | [**AiThreadMessageLike**](#model-aithreadmessagelike) | The user turn to send. | [required] |
| **actionArgs** | [**AiAiActionArgs**](#model-aiaiactionargs) | Per-request engine options: extra tools, reasoning, prompt override. | [optional] |
| **entityId** | **String** | Optional entity (room) scope for profile resolution. | [optional] |
| **profileId** | **String** | Session-level profile override for this request only. | [optional] |


### Model AiAiSettingsDto
The AI module settings.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **vectorizationEnabled** | **Boolean** | Indicates whether document vectorization is enabled. | [optional] [example: true] |
| **vectorizationNeedReset** | **Boolean** | Indicates whether the embedding provider API key needs to be reconfigured. | [optional] [example: false] |
| **aiReady** | **Boolean** | Indicates whether the AI subsystem is fully configured and operational. | [optional] [example: true] |
| **embeddingModel** | **String** | The name of the embedding model used for document vectorization. | [required] [example: text-embedding-3-small] [nullable] |
| **systemAiEnabled** | **Boolean** | Indicates whether the system-level AI provider is enabled. | [optional] [example: true] |
| **recommendedModelForForms** | **String** | The identifier of the model recommended for form generation. | [optional] [example: gpt-5.4] [nullable] |


### Model AiAiSettingsWrapper
The successful API response containing the AiSettingsDto object.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **response** | [**AiAiSettingsDto**](#model-aiaisettingsdto) | The AiSettingsDto object returned by the operation. | [optional] |
| **count** | **Integer** (int32) | The total number of items in the response | [optional] |
| **links** | [**List**](#model-aiaiusersettingswrapperlinks-item) | List of links related to the response | [optional] |
| **status** | **Integer** (int32) | HTTP status code of the response | [optional] |
| **statusCode** | **Integer** (int32) | HTTP status code of the response (duplicate of status) | [optional] |


### Model AiAiToolCallData
Identifies a pending tool call to resume — mirrors the library &#x60;ToolCallData&#x60; (its serializable fields).

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **threadId** | **String** | Thread the assistant message belongs to. | [required] |
| **messageId** | **String** | Storage id of the assistant message holding the tool call. | [required] |
| **idx** | **BigDecimal** | Index of the tool-call content part inside &#x60;message.content&#x60;. | [required] |
| **message** | [**AiThreadMessageLike**](#model-aithreadmessagelike) | Snapshot of the assistant message at the time the tool call surfaced. | [required] |
| **actionArgs** | [**AiAiActionArgs**](#model-aiaiactionargs) | Per-request engine options: extra tools, reasoning, prompt override. | [optional] |
| **entityId** | **String** | Optional entity (room) scope for profile resolution. | [optional] |
| **profileId** | **String** | Session-level profile override for this request only. | [optional] |


### Model AiAiUserSettingsDto
The per-user AI settings.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **chatRecommendedModelVisible** | **Boolean** | Indicates whether the recommended model banner is visible in the AI chat for the current user. | [optional] [example: true] |


### Model AiAiUserSettingsWrapper
The successful API response containing the AiUserSettingsDto object.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **response** | [**AiAiUserSettingsDto**](#model-aiaiusersettingsdto) | The AiUserSettingsDto object returned by the operation. | [optional] |
| **count** | **Integer** (int32) | The total number of items in the response | [optional] |
| **links** | [**List**](#model-aiaiusersettingswrapperlinks-item) | List of links related to the response | [optional] |
| **status** | **Integer** (int32) | HTTP status code of the response | [optional] |
| **statusCode** | **Integer** (int32) | HTTP status code of the response (duplicate of status) | [optional] |


### Model AiAiUserSettingsWrapper.links item

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **href** | **String** | URL of the link | [optional] |
| **action** | **String** | Action associated with the link | [optional] |


### Model AiApiDateTime
The API date and time parameters.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **utcTime** | **Date** (date-time) | The time in UTC format. | [optional] [example: 2018-01-01T00:00:00.0000000Z] |
| **timeZoneOffset** | **String** (date-span) | The time zone offset. | [optional] [example: 00:00:00] |


### Model AiAssignmentMutationResult
Outcome of &#x60;AssignmentsEngine.assign&#x60; / &#x60;AssignmentsEngine.unassign&#x60;. Either a success or a field-scoped error suitable for displaying in the profile editor.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **success** | **Boolean** | True when the assignment was persisted. | [required] |
| **error** | [**AiTErrorData**](#model-aiterrordata) | Why the assignment was rejected. Present on failure. | [optional] |


### Model AiAttachment
Persistent record for a single attachment (file or image) referenced from a user message. Files carry extracted text in &#x60;content&#x60;; images carry base64 data in &#x60;base64&#x60;. Metadata (&#x60;title&#x60;, &#x60;path&#x60;, &#x60;type&#x60;) is always present for display purposes regardless of whether the heavy payload is loaded.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **id** | **String** | Storage-assigned UUID. | [required] |
| **kind** | **String** | file \| image. | [required] [enum: file, image] |
| **source** | **String** | Origin of the attachment. &#x60;user&#x60; — uploaded by the user in the composer (the default when unset, for backward compatibility). &#x60;tool&#x60; — produced by a tool call (e.g. &#x60;generate_image&#x60;). Lets the integrator&#39;s adapter route or apply policies (separate bucket, quotas, TTL, CDN) per source. | [optional] [enum: user, tool] |
| **title** | **String** | Display label (filename or user-visible title). | [required] |
| **content** | **String** | Extracted text for files. | [optional] |
| **base64** | **String** | Base64 data URL for images. | [optional] |
| **path** | **String** | Original host file path (for files). | [optional] |
| **type** | **BigDecimal** | ONLYOFFICE file type code (for files). | [optional] |
| **messageId** | **String** | Owning message id once linked. Unset while the attachment is a draft. | [optional] |
| **threadId** | **String** | Owning thread id once linked. Unset while the attachment is a draft. | [optional] |
| **entityId** | **String** | Opaque scope token (entity / room) the attachment was created in. Drafts carry it so an entity switch keeps in-flight composer state isolated; once linked to a message the field is redundant with the thread&#39;s own entity binding. | [optional] |
| **createdAt** | **BigDecimal** | Storage-assigned creation timestamp. | [required] |
| **canAnalyze** | **Boolean** | Whether the attached form can be analyzed. | [optional] |
| **formKeys** | [**List**](#model-aiattachmentformkeys-item) | Keys of the fields inside the form. &#x60;key&#x60; is the field identifier, &#x60;text&#x60; its human-readable label. | [optional] |


### Model AiAttachment.formKeys item

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **key** | **String** |  | [required] |
| **text** | **String** |  | [required] |


### Model AiBuiltinProviderType
Union of all 17 built-in AI provider type identifiers.  The &#x60;external&#x60; provider has no built-in transport — it delegates every HTTP request to &#x60;PlatformAdapter.externalFetch&#x60; and parses the response with the inner provider selected by &#x60;Profile.basedOn&#x60;.

Possible values:

- `anthropic`
- `ollama`
- `openai`
- `openaicompatible`
- `together`
- `openrouter`
- `genai`
- `deepseek`
- `xai`
- `lm-studio`
- `mistral`
- `groq`
- `zhipu`
- `stabilityai`
- `gpt4all`
- `onlyoffice`
- `external`


### Model AiBulkAssignmentResult
Outcome of &#x60;AssignmentsEngine.bulkAssign&#x60;. Either every entry persisted, or no entries persisted and a per-key error report. The engine validates first and writes second so a single bad entry never leaves the assignment table in a half-written state.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **success** | **Boolean** | True when every entry was persisted. | [required] |
| **errors** | [**List**](#model-aibulkassignmentresulterrors-item) | What was rejected, per action. Present on failure - and then no entry was persisted. | [optional] |


### Model AiBulkAssignmentResult.errors item

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **actionType** | [**AiActionType**](#model-aiactiontype) |  | [required] [enum: Default, Chat, Code, Summarization, Translation, TextAnalyze, ImageGeneration, OCR, Vision] |
| **error** | [**AiTErrorData**](#model-aiterrordata) |  | [required] |


### Model AiChatEvent
Discriminated event emitted by the streaming methods of &#x60;AIEngine&#x60;. The engine never invokes user-supplied middleware or callbacks directly — every observable side-effect is encoded as a &#x60;ChatEvent&#x60; so the same stream can be replayed over SSE, WebSocket, or in-process.  Pause point: &#x60;tool-call-pending&#x60; is the only stop. The UI must execute the tool itself (consulting &#x60;autoAllow&#x60; to decide between the silent path and the approve dialog) and resume via &#x60;AIEngine.approveToolCall&#x60; or &#x60;AIEngine.denyToolCall&#x60;.  Other variants are pure data:  - &#x60;message-start&#x60; / &#x60;message-delta&#x60; / &#x60;message-end&#x60; — assistant reply lifecycle. - &#x60;message-incomplete&#x60; — the provider returned an error or incomplete status. - &#x60;thread-title&#x60; — auto-generated title ready for a new thread.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **type** | **String** | Emitted once per &#x60;sendWithStream&#x60; call, immediately after the user message has been persisted by storage and before the assistant stream starts. Carries the storage-assigned &#x60;id&#x60; and &#x60;createdAt&#x60;. The UI uses it to render the user bubble — no client-side optimistic placeholder is needed, which keeps the runtime tree free of phantom nodes from index-fallback ids. | [required] [enum: user-message-stored, message-start, message-delta, message-end, message-incomplete, tool-call-pending, thread-title] |
| **message** | [**AiThreadMessageLike**](#model-aithreadmessagelike) | The message the event is about, in the state it has reached. | [optional] |
| **messageId** | **String** | The storage identifier of that message. | [optional] |
| **idx** | **BigDecimal** | The zero-based position of the pending tool call within the message. | [optional] |
| **threadId** | **String** | The thread the event belongs to. | [optional] |
| **autoAllow** | **Boolean** | The consumer should execute the tool without prompting the user. True when the tool is in the persisted always-allow list, or the tool itself opts in via &#x60;TMCPItem.requireApproval &#x3D;&#x3D;&#x3D; false&#x60; (host tools default to this). For a client-side tool with a server-side engine, this lets the engine return the pending call already flagged auto-allow so the client runs it and streams the result back without a dialog round-trip. | [optional] |
| **serverExecuted** | **Boolean** | Set when the tool is served by a server-side system source: the consumer must NOT execute it locally — only show the approval UI (unless &#x60;autoAllow&#x60;) and resume via &#x60;approveToolCall&#x60; (no &#x60;result&#x60; needed) / &#x60;denyToolCall&#x60;. The engine runs it in-engine. | [optional] |
| **title** | **String** | The generated thread title. | [optional] |
| **profileId** | **String** | The profile that generated the title, when one was used. | [optional] |


### Model AiChatSettingsDto
The chat settings parameters.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **prompt** | **String** | The system prompt for the chat. | [optional] [example: You are a helpful assistant.] [nullable] |


### Model AiCreateProfileInput
Input for creating a new profile — the same shape as &#x60;Profile&#x60; without the engine-generated fields (&#x60;id&#x60;, &#x60;createdAt&#x60;).

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **name** | **String** | User-defined profile display name. | [required] |
| **providerType** | [**AiProviderType**](#model-aiprovidertype) | Provider type for this profile. Use &#x60;external&#x60; to delegate all HTTP transport to &#x60;PlatformAdapter.externalFetch&#x60; while reusing an existing provider&#39;s response parser — see &#x60;Profile.basedOn&#x60; for the format selector. | [required] |
| **basedOn** | [**AiBuiltinProviderType**](#model-aibuiltinprovidertype) | Selects the response-format parser used by the &#x60;external&#x60; provider. Ignored for any other &#x60;providerType&#x60;.  Supported values are &#x60;openai&#x60;, &#x60;anthropic&#x60;, &#x60;mistral&#x60; and &#x60;openrouter&#x60;. Remaining values (&#x60;genai&#x60;, &#x60;stabilityai&#x60;, …) are accepted by the type but not yet implemented; passing one raises an error at request time. | [optional] [enum: anthropic, ollama, openai, openaicompatible, together, openrouter, genai, deepseek, xai, lm-studio, mistral, groq, zhipu, stabilityai, gpt4all, onlyoffice, external] |
| **baseUrl** | **String** | Base URL of the provider API. | [required] |
| **key** | **String** | API key or token. Optional for local providers. | [optional] |
| **headers** | **Map** | Extra HTTP headers sent with every request to this provider. Merged into the SDK client&#39;s default headers; an explicit &#x60;Authorization&#x60; here wins over the one derived from &#x60;key&#x60;. Honoured by the OpenAI-family providers. | [optional] |
| **modelId** | **String** | Selected model ID within this provider. | [required] |
| **reasoning** | **Boolean** | Whether extended thinking is enabled for this profile&#39;s model. | [optional] |
| **capabilities** | **BigDecimal** | Bitmask of capabilities supported by the selected model. | [optional] |
| **canUseTool** | **Boolean** | Result of the live tool-capability probe performed at create time and on changes to &#x60;modelId&#x60; / &#x60;providerType&#x60; / &#x60;baseUrl&#x60;. &#x60;undefined&#x60; means the probe has never run for this profile (legacy record). | [optional] |
| **useResponsesApi** | **Boolean** | Result of the live Responses-API probe (parallel to &#x60;canUseTool&#x60;). &#x60;true&#x60; means the model speaks &#x60;/v1/responses&#x60; and the OpenAI provider must route through &#x60;client.responses.create&#x60; — required for gpt-5+ reasoning models that reject &#x60;reasoning_effort&#x60; together with &#x60;tools&#x60; on &#x60;/v1/chat/completions&#x60;. Probed at create time and whenever &#x60;modelId&#x60; / &#x60;providerType&#x60; / &#x60;baseUrl&#x60; change. &#x60;undefined&#x60; means the probe never ran (legacy record) — readers treat that as &#x60;false&#x60;. | [optional] |
| **isCloudProvider** | **Boolean** | Whether this profile uses a cloud-hosted provider (e.g. ONLYOFFICE DocSpace). | [optional] |
| **useProxy** | **Boolean** | Route every provider request through the host&#39;s &#x60;fetchProxy&#x60; instead of the global &#x60;fetch&#x60;. Useful when the host runs the widget in a sandbox without direct network access (CORS, custom auth, etc.). Has no effect when the &#x60;PlatformAdapter.fetchProxy&#x60; is not configured. | [optional] |


### Model AiCreatePromptInput
Input for creating a prompt — the engine generates &#x60;id&#x60;/&#x60;createdAt&#x60;/&#x60;updatedAt&#x60;.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **name** | **String** | The prompt name. | [required] |
| **text** | **String** | The prompt body. | [required] |
| **folderId** | **String** | The folder to file the prompt under. Omit or send null to leave it outside any folder. | [optional] [nullable] |


### Model AiDistributedTaskStatus

Possible values:

- `0` — Created (`Created`)
- `1` — Running (`Running`)
- `2` — Completed (`Completed`)
- `3` — Canceled (`Canceled`)
- `4` — Failted (`Failted`)


### Model AiEmbeddingProviderType

Possible values:

- `0` — None (`None`)
- `1` — OpenAi (`OpenAi`)
- `2` — OpenRouter (`OpenRouter`)
- `3` — PortalAi (`PortalAi`)


### Model AiEmployeeDto
The user parameters.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **id** | **UUID** (uuid) | The user ID. | [optional] [example: 00000000-0000-0000-0000-000000000000] |
| **displayName** | **String** | The HTML-encoded user&#39;s display name formatted according to the default format for the current culture. | [optional] [example: Mike Zanyatski] [nullable] |
| **avatar** | **String** | The user avatar. | [optional] [example: https://example.com/avatar.jpg] [nullable] |
| **avatarOriginal** | **String** | The user original size avatar. | [optional] [example: https://example.com/avatar_original.jpg] [nullable] |
| **avatarMax** | **String** | The user maximum size avatar. | [optional] [example: https://example.com/avatar_max.jpg] [nullable] |
| **avatarMedium** | **String** | The user medium size avatar. | [optional] [example: https://example.com/avatar_medium.jpg] [nullable] |
| **avatarSmall** | **String** | The user small size avatar. | [optional] [example: https://example.com/avatar_small.jpg] [nullable] |
| **profileUrl** | **String** | The user profile URL. | [optional] [example: https://example.com/profile/user123] [nullable] |
| **hasAvatar** | **Boolean** | Specifies if the user has an avatar or not. | [optional] [example: true] |
| **isAnonim** | **Boolean** | Specifies if the user is anonymous or not. | [optional] [example: false] |


### Model AiErrorResponse
Error body — a single human-readable message.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **error** | **String** | The error message, ready to be shown to the caller. | [required] |


### Model AiFileEntryBaseDto
The file entry information.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **title** | **String** | The file entry title. | [optional] [example: Some title.txt] [nullable] |
| **access** | [**AiFileShare**](#model-aifileshare) | The access rights to the file entry. | [optional] [enum: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11] |
| **sharedBy** | [**AiEmployeeDto**](#model-aiemployeedto) | Provides information about the employee who shared the file or folder. | [optional] |
| **ownedBy** | [**AiEmployeeDto**](#model-aiemployeedto) | The information about the employee who owns the file entry. | [optional] |
| **shared** | **Boolean** | Specifies if the file entry is shared via link or not. | [optional] [example: false] |
| **sharedForUser** | **Boolean** | Specifies if the file entry is shared for user or not. | [optional] [example: false] |
| **sharedExternal** | **Boolean** | Specifies if the file entry is shared via a public (non-internal) external link. | [optional] [example: false] |
| **parentShared** | **Boolean** | Indicates whether the parent entity is shared. | [optional] [example: false] |
| **shortWebUrl** | **URI** (uri) | The short Web URL. | [optional] [example: http://localhost/s/abc123] [nullable] |
| **created** | [**AiApiDateTime**](#model-aiapidatetime) | The creation date and time of the file entry. | [optional] |
| **createdBy** | [**AiEmployeeDto**](#model-aiemployeedto) | The file entry author. | [optional] |
| **updated** | [**AiApiDateTime**](#model-aiapidatetime) | The last date and time when the file entry was updated. | [optional] |
| **autoDelete** | [**AiApiDateTime**](#model-aiapidatetime) | The date and time when the file entry will be automatically deleted. | [optional] |
| **rootFolderType** | [**AiFolderType**](#model-aifoldertype) | The root folder type of the file entry. | [optional] [enum: 0, 1, 2, 3, 5, 6, 8, 10, 11, 12, 13, 14, 15, 16, 19, 20, 21, 22, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36] |
| **parentRoomType** | [**AiFolderType**](#model-aifoldertype) | The parent room type of the file entry. | [optional] [enum: 0, 1, 2, 3, 5, 6, 8, 10, 11, 12, 13, 14, 15, 16, 19, 20, 21, 22, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36] |
| **updatedBy** | [**AiEmployeeDto**](#model-aiemployeedto) | The user who updated the file entry. | [optional] |
| **providerItem** | **Boolean** | Specifies if the file entry provider is specified or not. | [optional] [example: false] [nullable] |
| **providerKey** | **String** | The provider key of the file entry. | [optional] [example: google-drive] [nullable] |
| **providerId** | **Integer** (int32) | The provider ID of the file entry. | [optional] [example: 1] [nullable] |
| **order** | **String** | The order of the file entry. | [optional] [example: 1] [nullable] |
| **isFavorite** | **Boolean** | Specifies if the file is a favorite or not. | [optional] [example: false] [nullable] |
| **fileEntryType** | [**AiFileEntryType**](#model-aifileentrytype) | The file entry type. | [optional] [enum: 1, 2] |


### Model AiFileEntryDtoInteger
The generic file entry information.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **title** | **String** | The file entry title. | [optional] |
| **access** | [**AiFileShare**](#model-aifileshare) | The access rights to the file entry. | [optional] [enum: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11] |
| **sharedBy** | [**AiEmployeeDto**](#model-aiemployeedto) | Provides information about the employee who shared the file or folder. | [optional] |
| **ownedBy** | [**AiEmployeeDto**](#model-aiemployeedto) | The information about the employee who owns the file entry. | [optional] |
| **shared** | **Boolean** | Specifies if the file entry is shared via link or not. | [optional] |
| **sharedForUser** | **Boolean** | Specifies if the file entry is shared for user or not. | [optional] |
| **sharedExternal** | **Boolean** | Specifies if the file entry is shared via a public (non-internal) external link. | [optional] |
| **parentShared** | **Boolean** | Indicates whether the parent entity is shared. | [optional] |
| **shortWebUrl** | **URI** (uri) | The short Web URL. | [optional] |
| **created** | [**AiApiDateTime**](#model-aiapidatetime) | The creation date and time of the file entry. | [optional] |
| **createdBy** | [**AiEmployeeDto**](#model-aiemployeedto) | The file entry author. | [optional] |
| **updated** | [**AiApiDateTime**](#model-aiapidatetime) | The last date and time when the file entry was updated. | [optional] |
| **autoDelete** | [**AiApiDateTime**](#model-aiapidatetime) | The date and time when the file entry will be automatically deleted. | [optional] |
| **rootFolderType** | [**AiFolderType**](#model-aifoldertype) | The root folder type of the file entry. | [optional] [enum: 0, 1, 2, 3, 5, 6, 8, 10, 11, 12, 13, 14, 15, 16, 19, 20, 21, 22, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36] |
| **parentRoomType** | [**AiFolderType**](#model-aifoldertype) | The parent room type of the file entry. | [optional] [enum: 0, 1, 2, 3, 5, 6, 8, 10, 11, 12, 13, 14, 15, 16, 19, 20, 21, 22, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36] |
| **updatedBy** | [**AiEmployeeDto**](#model-aiemployeedto) | The user who updated the file entry. | [optional] |
| **providerItem** | **Boolean** | Specifies if the file entry provider is specified or not. | [optional] |
| **providerKey** | **String** | The provider key of the file entry. | [optional] |
| **providerId** | **Integer** (int32) | The provider ID of the file entry. | [optional] |
| **order** | **String** | The order of the file entry. | [optional] |
| **isFavorite** | **Boolean** | Specifies if the file is a favorite or not. | [optional] |
| **fileEntryType** | [**AiFileEntryType**](#model-aifileentrytype) | The file entry type. | [optional] [enum: 1, 2] |
| **id** | **Integer** (int32) | The file entry ID. | [optional] |
| **rootFolderId** | **Integer** (int32) | The root folder ID of the file entry. | [optional] |
| **originId** | **Integer** (int32) | The origin ID of the file entry. | [optional] |
| **originRoomId** | **Integer** (int32) | The origin room ID of the file entry. | [optional] |
| **originTitle** | **String** | The origin title of the file entry. | [optional] [nullable] |
| **originRoomTitle** | **String** | The origin room title of the file entry. | [optional] [nullable] |
| **canShare** | **Boolean** | Specifies if the file entry can be shared or not. | [optional] |
| **shareSettings** | [**AiFileEntryDtoInteger_allOf_shareSettings**](#model-aifileentrydtointegersharesettings) |  | [optional] [nullable] |
| **security** | [**AiFileEntryDtoInteger_allOf_security**](#model-aifileentrydtointegersecurity) |  | [optional] [nullable] |
| **availableShareRights** | [**AiFileEntryDtoInteger_allOf_availableShareRights**](#model-aifileentrydtointegeravailablesharerights) |  | [optional] [nullable] |
| **requestToken** | **String** | The request token of the file entry. | [optional] [nullable] |
| **external** | **Boolean** | Specifies if the folder can be accessed via an external link or not. | [optional] [nullable] |
| **expirationDate** | [**AiApiDateTime**](#model-aiapidatetime) | Represents the expiration date of the file entry. | [optional] |
| **isLinkExpired** | **Boolean** | Indicates whether the shareable link associated with the file or folder has expired. | [optional] [nullable] |


### Model AiFileEntryDtoInteger.availableShareRights
The available external rights of the file entry.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **User** | **List** |  | [optional] |
| **ExternalLink** | **List** |  | [optional] |
| **Group** | **List** |  | [optional] |
| **InvitationLink** | **List** |  | [optional] |
| **PrimaryExternalLink** | **List** |  | [optional] |


### Model AiFileEntryDtoInteger.security
The actions that can be performed with the file entry.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **Read** | **Boolean** |  | [optional] |
| **Comment** | **Boolean** |  | [optional] |
| **FillForms** | **Boolean** |  | [optional] |
| **Review** | **Boolean** |  | [optional] |
| **Create** | **Boolean** |  | [optional] |
| **CreateFrom** | **Boolean** |  | [optional] |
| **Edit** | **Boolean** |  | [optional] |
| **Delete** | **Boolean** |  | [optional] |
| **CustomFilter** | **Boolean** |  | [optional] |
| **EditRoom** | **Boolean** |  | [optional] |
| **Rename** | **Boolean** |  | [optional] |
| **ReadHistory** | **Boolean** |  | [optional] |
| **Lock** | **Boolean** |  | [optional] |
| **EditHistory** | **Boolean** |  | [optional] |
| **CopyTo** | **Boolean** |  | [optional] |
| **Copy** | **Boolean** |  | [optional] |
| **MoveTo** | **Boolean** |  | [optional] |
| **Move** | **Boolean** |  | [optional] |
| **Pin** | **Boolean** |  | [optional] |
| **Mute** | **Boolean** |  | [optional] |
| **EditAccess** | **Boolean** |  | [optional] |
| **Duplicate** | **Boolean** |  | [optional] |
| **SubmitToFormGallery** | **Boolean** |  | [optional] |
| **Download** | **Boolean** |  | [optional] |
| **Convert** | **Boolean** |  | [optional] |
| **CopySharedLink** | **Boolean** |  | [optional] |
| **ReadLinks** | **Boolean** |  | [optional] |
| **Reconnect** | **Boolean** |  | [optional] |
| **CreateRoomFrom** | **Boolean** |  | [optional] |
| **CopyLink** | **Boolean** |  | [optional] |
| **Embed** | **Boolean** |  | [optional] |
| **ChangeOwner** | **Boolean** |  | [optional] |
| **IndexExport** | **Boolean** |  | [optional] |
| **StartFilling** | **Boolean** |  | [optional] |
| **FillingStatus** | **Boolean** |  | [optional] |
| **ResetFilling** | **Boolean** |  | [optional] |
| **StopFilling** | **Boolean** |  | [optional] |
| **OpenForm** | **Boolean** |  | [optional] |
| **EditInternal** | **Boolean** |  | [optional] |
| **EditExpiration** | **Boolean** |  | [optional] |
| **Vectorization** | **Boolean** |  | [optional] |
| **AskAi** | **Boolean** |  | [optional] |
| **UseChat** | **Boolean** |  | [optional] |
| **UpdateXlsx** | **Boolean** |  | [optional] |
| **AnalyzeResponses** | **Boolean** |  | [optional] |
| **CanUseAi** | **Boolean** |  | [optional] |
| **HistoryExport** | **Boolean** |  | [optional] |


### Model AiFileEntryDtoInteger.shareSettings
A dictionary representing the sharing settings for the file entry.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **User** | **Integer** (int32) |  | [optional] |
| **ExternalLink** | **Integer** (int32) |  | [optional] |
| **Group** | **Integer** (int32) |  | [optional] |
| **InvitationLink** | **Integer** (int32) |  | [optional] |
| **PrimaryExternalLink** | **Integer** (int32) |  | [optional] |


### Model AiFileEntryType

Possible values:

- `1` — Folder (`Folder`)
- `2` — File (`File`)


### Model AiFileOperationDto
The file operation information.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **id** | **String** | The file operation ID. | [required] [example: 00000000-0000-0000-0000-000000000000] [nullable] |
| **Operation** | [**AiFileOperationType**](#model-aifileoperationtype) | The file operation type. | [required] [enum: 0, 1, 2, 3, 4, 5, 6, 7] |
| **progress** | **Integer** (int32) | The file operation progress in percentage. | [required] [example: 100] |
| **error** | **String** | The file operation error message. | [required] [example: File not found.] [nullable] |
| **processed** | **String** | The file operation processing status. | [required] [example: 1] [nullable] |
| **finished** | **Boolean** | Specifies if the file operation is finished or not. | [required] [example: true] |
| **url** | **URI** (uri) | The file operation URL. | [optional] [example: http://localhost/download] [nullable] |
| **files** | [**List**](#model-aifileentrybasedto) | The list of files of the file operation. | [optional] [example: [{id=10, title=document.docx}]] [nullable] |
| **folders** | [**List**](#model-aifileentrybasedto) | The list of folders of the file operation. | [optional] [example: [{id=20, title=My Folder}]] [nullable] |
| **status** | [**AiDistributedTaskStatus**](#model-aidistributedtaskstatus) | The status of the distributed task related to the file operation. | [optional] [enum: 0, 1, 2, 3, 4] |


### Model AiFileOperationType

Possible values:

- `0` — Move (`Move`)
- `1` — Copy (`Copy`)
- `2` — Delete (`Delete`)
- `3` — Download (`Download`)
- `4` — MarkAsRead (`MarkAsRead`)
- `5` — Import (`Import`)
- `6` — Convert (`Convert`)
- `7` — Duplicate (`Duplicate`)


### Model AiFileOperationWrapper
The successful API response containing the FileOperationDto object.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **response** | [**AiFileOperationDto**](#model-aifileoperationdto) | The FileOperationDto object returned by the operation. | [optional] |
| **count** | **Integer** (int32) | The total number of items in the response | [optional] |
| **links** | [**List**](#model-aiaiusersettingswrapperlinks-item) | List of links related to the response | [optional] |
| **status** | **Integer** (int32) | HTTP status code of the response | [optional] |
| **statusCode** | **Integer** (int32) | HTTP status code of the response (duplicate of status) | [optional] |


### Model AiFileShare

Possible values:

- `0` — None (`None`)
- `1` — Read and write (`ReadWrite`)
- `2` — Read (`Read`)
- `3` — Restrict (`Restrict`)
- `4` — Varies (`Varies`)
- `5` — Review (`Review`)
- `6` — Comment (`Comment`)
- `7` — Fill forms (`FillForms`)
- `8` — Custom filter (`CustomFilter`)
- `9` — Room manager (`RoomManager`)
- `10` — Editing (`Editing`)
- `11` — Content creator (`ContentCreator`)


### Model AiFolderContentDtoInteger
The folder content information.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **files** | [**List**](#model-aifileentrybasedto) | The list of files in the folder. | [optional] [example: [{id=10, title=document.docx}]] [nullable] |
| **folders** | [**List**](#model-aifileentrybasedto) | The list of folders in the folder. | [optional] [example: [{id=20, title=My Folder}]] [nullable] |
| **current** | [**AiFolderDtoInteger**](#model-aifolderdtointeger) | The current folder information. | [optional] |
| **pathParts** | **oas_any_type_not_mapped** |  | [required] [nullable] |
| **startIndex** | **Integer** (int32) | The folder start index. | [optional] [example: 0] |
| **count** | **Integer** (int32) | The number of folder elements. | [optional] [example: 4] |
| **total** | **Integer** (int32) | The total number of elements in the folder. | [required] [example: 4] |
| **new** | **Integer** (int32) | The new element index in the folder. | [optional] [example: 0] |


### Model AiFolderContentIntegerWrapper
The successful API response containing the FolderContentDtoInteger object.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **response** | [**AiFolderContentDtoInteger**](#model-aifoldercontentdtointeger) | The FolderContentDtoInteger object returned by the operation. | [optional] |
| **count** | **Integer** (int32) | The total number of items in the response | [optional] |
| **links** | [**List**](#model-aiaiusersettingswrapperlinks-item) | List of links related to the response | [optional] |
| **status** | **Integer** (int32) | HTTP status code of the response | [optional] |
| **statusCode** | **Integer** (int32) | HTTP status code of the response (duplicate of status) | [optional] |


### Model AiFolderDtoInteger
The folder parameters.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **title** | **String** | The file entry title. | [optional] |
| **access** | [**AiFileShare**](#model-aifileshare) | The access rights to the file entry. | [optional] [enum: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11] |
| **sharedBy** | [**AiEmployeeDto**](#model-aiemployeedto) | Provides information about the employee who shared the file or folder. | [optional] |
| **ownedBy** | [**AiEmployeeDto**](#model-aiemployeedto) | The information about the employee who owns the file entry. | [optional] |
| **shared** | **Boolean** | Specifies if the file entry is shared via link or not. | [optional] |
| **sharedForUser** | **Boolean** | Specifies if the file entry is shared for user or not. | [optional] |
| **sharedExternal** | **Boolean** | Specifies if the file entry is shared via a public (non-internal) external link. | [optional] |
| **parentShared** | **Boolean** | Indicates whether the parent entity is shared. | [optional] |
| **shortWebUrl** | **URI** (uri) | The short Web URL. | [optional] |
| **created** | [**AiApiDateTime**](#model-aiapidatetime) | The creation date and time of the file entry. | [optional] |
| **createdBy** | [**AiEmployeeDto**](#model-aiemployeedto) | The file entry author. | [optional] |
| **updated** | [**AiApiDateTime**](#model-aiapidatetime) | The last date and time when the file entry was updated. | [optional] |
| **autoDelete** | [**AiApiDateTime**](#model-aiapidatetime) | The date and time when the file entry will be automatically deleted. | [optional] |
| **rootFolderType** | [**AiFolderType**](#model-aifoldertype) | The root folder type of the file entry. | [optional] [enum: 0, 1, 2, 3, 5, 6, 8, 10, 11, 12, 13, 14, 15, 16, 19, 20, 21, 22, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36] |
| **parentRoomType** | [**AiFolderType**](#model-aifoldertype) | The parent room type of the file entry. | [optional] [enum: 0, 1, 2, 3, 5, 6, 8, 10, 11, 12, 13, 14, 15, 16, 19, 20, 21, 22, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36] |
| **updatedBy** | [**AiEmployeeDto**](#model-aiemployeedto) | The user who updated the file entry. | [optional] |
| **providerItem** | **Boolean** | Specifies if the file entry provider is specified or not. | [optional] |
| **providerKey** | **String** | The provider key of the file entry. | [optional] |
| **providerId** | **Integer** (int32) | The provider ID of the file entry. | [optional] |
| **order** | **String** | The order of the file entry. | [optional] |
| **isFavorite** | **Boolean** | Specifies if the file is a favorite or not. | [optional] |
| **fileEntryType** | [**AiFileEntryType**](#model-aifileentrytype) | The file entry type. | [optional] [enum: 1, 2] |
| **id** | **Integer** (int32) | The file entry ID. | [optional] |
| **rootFolderId** | **Integer** (int32) | The root folder ID of the file entry. | [optional] |
| **originId** | **Integer** (int32) | The origin ID of the file entry. | [optional] |
| **originRoomId** | **Integer** (int32) | The origin room ID of the file entry. | [optional] |
| **originTitle** | **String** | The origin title of the file entry. | [optional] |
| **originRoomTitle** | **String** | The origin room title of the file entry. | [optional] |
| **canShare** | **Boolean** | Specifies if the file entry can be shared or not. | [optional] |
| **shareSettings** | [**AiFileEntryDtoInteger_allOf_shareSettings**](#model-aifileentrydtointegersharesettings) |  | [optional] [nullable] |
| **security** | [**AiFileEntryDtoInteger_allOf_security**](#model-aifileentrydtointegersecurity) |  | [optional] [nullable] |
| **availableShareRights** | [**AiFileEntryDtoInteger_allOf_availableShareRights**](#model-aifileentrydtointegeravailablesharerights) |  | [optional] [nullable] |
| **requestToken** | **String** | The request token of the file entry. | [optional] |
| **external** | **Boolean** | Specifies if the folder can be accessed via an external link or not. | [optional] |
| **expirationDate** | [**AiApiDateTime**](#model-aiapidatetime) | Represents the expiration date of the file entry. | [optional] |
| **isLinkExpired** | **Boolean** | Indicates whether the shareable link associated with the file or folder has expired. | [optional] |
| **parentId** | **Integer** (int32) | The parent folder ID of the folder. | [optional] |
| **filesCount** | **Integer** (int32) | The number of files that the folder contains. | [optional] |
| **foldersCount** | **Integer** (int32) | The number of folders that the folder contains. | [optional] |
| **isShareable** | **Boolean** | Specifies if the folder can be shared or not. | [optional] [nullable] |
| **new** | **Integer** (int32) | The new element index in the folder. | [optional] |
| **mute** | **Boolean** | Specifies if the folder notifications are enabled or not. | [optional] |
| **tags** | **List** | The list of tags of the folder. | [optional] [nullable] |
| **logo** | [**AiLogo**](#model-ailogo) | The folder logo. | [optional] |
| **pinned** | **Boolean** | Specifies if the folder is pinned or not. | [optional] |
| **roomType** | [**AiRoomType**](#model-airoomtype) | The room type of the folder. | [optional] [enum: 1, 2, 5, 6, 8, 9] |
| **private** | **Boolean** | Specifies if the folder is private or not. | [optional] |
| **indexing** | **Boolean** | Specifies if the folder is indexed or not. | [optional] |
| **denyDownload** | **Boolean** | Specifies if the folder can be downloaded or not. | [optional] |
| **lifetime** | [**AiRoomDataLifetimeDto**](#model-airoomdatalifetimedto) | The room data lifetime settings of the folder. | [optional] |
| **watermark** | [**AiWatermarkDto**](#model-aiwatermarkdto) | The watermark settings of the folder. | [optional] |
| **type** | [**AiFolderType**](#model-aifoldertype) | The folder type. | [optional] [enum: 0, 1, 2, 3, 5, 6, 8, 10, 11, 12, 13, 14, 15, 16, 19, 20, 21, 22, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36] |
| **inRoom** | **Boolean** | Specifies if the folder is placed in the room or not. | [optional] [nullable] |
| **quotaLimit** | **Long** (int64) | The folder quota limit. | [optional] [nullable] |
| **isCustomQuota** | **Boolean** | Specifies if the folder room has a custom quota or not. | [optional] [nullable] |
| **usedSpace** | **Long** (int64) | How much folder space is used (counter). | [optional] [nullable] |
| **passwordProtected** | **Boolean** | Specifies if the folder is password protected or not. | [optional] [nullable] |
| **expired** | **Boolean** | Specifies if an external link to the folder is expired or not. | [optional] [nullable] |
| **chatSettings** | [**AiChatSettingsDto**](#model-aichatsettingsdto) | The AI chat settings for the folder room. Contains configuration for AI provider, model selection, and custom prompts.  Only applicable to rooms with AI chat functionality enabled. Null if the room does not have chat settings configured. | [optional] |
| **rootRoomType** | [**AiRoomType**](#model-airoomtype) | The room type of the root folder. Indicates the type of the parent room if the current folder is nested within a room hierarchy.  This property helps identify the context in which a nested folder exists. | [optional] [enum: 1, 2, 5, 6, 8, 9] |
| **saveFormAsXLSX** | **Boolean** | Specifies whether to save form data as XLSX file. | [optional] [nullable] |
| **sendFormToExternalDB** | **Boolean** | Specifies whether to send form data to external database. | [optional] [nullable] |
| **originalFormId** | **Integer** (int32) | The original form ID that corresponds to this FormFillingFolderDone folder. | [optional] [nullable] |


### Model AiFolderIntegerArrayWrapper
The successful API response containing the list of FolderDtoInteger objects.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **response** | [**List**](#model-aifolderdtointeger) | The list of FolderDtoInteger objects returned by the operation. | [optional] |
| **count** | **Integer** (int32) | The total number of items in the response | [optional] |
| **links** | [**List**](#model-aiaiusersettingswrapperlinks-item) | List of links related to the response | [optional] |
| **status** | **Integer** (int32) | HTTP status code of the response | [optional] |
| **statusCode** | **Integer** (int32) | HTTP status code of the response (duplicate of status) | [optional] |


### Model AiFolderIntegerWrapper
The successful API response containing the FolderDtoInteger object.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **response** | [**AiFolderDtoInteger**](#model-aifolderdtointeger) | The FolderDtoInteger object returned by the operation. | [optional] |
| **count** | **Integer** (int32) | The total number of items in the response | [optional] |
| **links** | [**List**](#model-aiaiusersettingswrapperlinks-item) | List of links related to the response | [optional] |
| **status** | **Integer** (int32) | HTTP status code of the response | [optional] |
| **statusCode** | **Integer** (int32) | HTTP status code of the response (duplicate of status) | [optional] |


### Model AiFolderMutationResult
Outcome of &#x60;createFolder&#x60; / &#x60;renameFolder&#x60; — either the persisted folder or a field-scoped error.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **success** | **Boolean** | True when the folder was persisted. | [required] |
| **folder** | [**AiPromptFolder**](#model-aipromptfolder) | The persisted folder. Present on success. | [optional] |
| **error** | [**AiTErrorData**](#model-aiterrordata) | Why the folder was rejected. Present on failure. | [optional] |


### Model AiFolderType

Possible values:

- `0` — Default (`DEFAULT`)
- `1` — Coomon (`COMMON`)
- `2` — Bunch (`BUNCH`)
- `3` — Trash (`TRASH`)
- `5` — User (`USER`)
- `6` — Share (`SHARE`)
- `8` — Projects (`Projects`)
- `10` — Favourites (`Favorites`)
- `11` — Recent (`Recent`)
- `12` — Templates (`Templates`)
- `13` — Privacy (`Privacy`)
- `14` — Virtual rooms (`VirtualRooms`)
- `15` — Filling forms room (`FillingFormsRoom`)
- `16` — Editing room (`EditingRoom`)
- `19` — Custom room (`CustomRoom`)
- `20` — Archive (`Archive`)
- `21` — Thirdparty backup (`ThirdpartyBackup`)
- `22` — Public room (`PublicRoom`)
- `25` — Ready form folder (`ReadyFormFolder`)
- `26` — In process form folder (`InProcessFormFolder`)
- `27` — Form filling folder done (`FormFillingFolderDone`)
- `28` — Form filling folder in progress (`FormFillingFolderInProgress`)
- `29` — Virtual Data Room (`VirtualDataRoom`)
- `30` — Room templates folder (`RoomTemplates`)
- `31` — AI Room (`AiRoom`)
- `32` — Knowledge (`Knowledge`)
- `33` — Result storage (`ResultStorage`)
- `34` — AI Agents (`AiAgents`)
- `35` — Default Templates (`DefaultTemplates`)
- `36` — Forms (`Forms`)


### Model AiImportError
Per-entry error reported by &#x60;PromptsEngine.importBundle&#x60;.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **kind** | **String** | &#x60;folder&#x60; or &#x60;prompt&#x60;, plus the offending name or id. | [required] [enum: folder, prompt] |
| **ref** | **String** | The offending entry - its name or its id. | [required] |
| **error** | [**AiTErrorData**](#model-aiterrordata) | Why the entry was rejected. | [required] |


### Model AiImportMode
Mode passed to &#x60;PromptsEngine.importBundle&#x60;.

Possible values:

- `replace`
- `merge`


### Model AiImportResult
Outcome of &#x60;PromptsEngine.importBundle&#x60;. Either every entry persisted with counts, or no entries persisted plus a per-entry error report.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **success** | **Boolean** | True when the whole bundle was imported. | [required] |
| **imported** | [**AiImportResult_imported**](#model-aiimportresultimported) |  | [optional] |
| **errors** | [**List**](#model-aiimporterror) | What was rejected, per entry. Present on failure - and then nothing was imported. | [optional] |


### Model AiImportResult.imported
How many folders and prompts were created. Present on success.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **folders** | **BigDecimal** |  | [required] |
| **prompts** | **BigDecimal** |  | [required] |


### Model AiLogo
The room logo information.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **original** | **String** | The original logo. | [required] [example: https://portal.example.com/logo/original.png] [nullable] |
| **large** | **String** | The large logo. | [required] [example: https://portal.example.com/logo/large.png] [nullable] |
| **medium** | **String** | The medium logo. | [required] [example: https://portal.example.com/logo/medium.png] [nullable] |
| **small** | **String** | The small logo. | [required] [example: https://portal.example.com/logo/small.png] [nullable] |
| **color** | **String** | The logo color. | [optional] [example: #4781D1] [nullable] |
| **cover** | [**AiLogoCover**](#model-ailogocover) | The logo cover. | [optional] |


### Model AiLogoCover
The logo cover information.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **id** | **String** | The logo cover ID. | [required] [example: default_cover] [nullable] |
| **data** | **String** | The logo cover data. | [required] [example: base64-image-data...] [nullable] |


### Model AiModel
AI model metadata. Describes a single model available from a provider.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **id** | **String** | Model identifier as used by the provider API (e.g. &#x60;gpt-4o&#x60;, &#x60;claude-sonnet-4-20250514&#x60;). | [required] |
| **name** | **String** | Human-readable model name for display in the UI. | [required] |
| **provider** | [**AiProviderType**](#model-aiprovidertype) | Provider that offers this model. | [required] |
| **reasoning** | **Boolean** | Whether this model supports extended thinking / chain-of-thought reasoning. | [optional] |
| **capabilities** | **BigDecimal** | Bitmask of model capabilities (Chat, Image, Vision, Tools, etc.). Used to filter models per &#x60;ActionType&#x60;. | [optional] |


### Model AiNewItemsAgentNewItemsArrayWrapper
The successful API response containing the list of NewItemsDtoAgentNewItemsDto objects.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **response** | [**List**](#model-ainewitemsdtoagentnewitemsdto) | The list of NewItemsDtoAgentNewItemsDto objects returned by the operation. | [optional] |
| **count** | **Integer** (int32) | The total number of items in the response | [optional] |
| **links** | [**List**](#model-aiaiusersettingswrapperlinks-item) | List of links related to the response | [optional] |
| **status** | **Integer** (int32) | HTTP status code of the response | [optional] |
| **statusCode** | **Integer** (int32) | HTTP status code of the response (duplicate of status) | [optional] |


### Model AiNewItemsDtoAgentNewItemsDto
The new item parameters.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **date** | [**AiApiDateTime**](#model-aiapidatetime) | The date and time when the new item was created. | [required] |
| **items** | [**List**](#model-aiagentnewitemsdto) | The list of items. | [required] [nullable] |


### Model AiOpenAIChatCompletionChunk
One &#x60;chat.completion.chunk&#x60; of an OpenAI-compatible streaming response. Only the fields this service can populate are emitted - an OpenAI client tolerates the rest as absent.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **id** | **String** | The completion identifier, stable across every chunk of one response. | [required] |
| **object** | **String** | Always &#x60;chat.completion.chunk&#x60;. | [required] [enum: chat.completion.chunk] |
| **created** | **BigDecimal** | When the completion started, in Unix seconds. | [required] |
| **model** | **String** | The model that produced the completion - the resolved profile&#39;s model. | [required] |
| **choices** | [**List**](#model-aiopenaichunkchoice) | The choices carried by this chunk. This service emits exactly one. | [required] |


### Model AiOpenAIChoiceDelta
The incremental part of one choice - what this chunk adds to the assistant message.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **role** | **String** | Sent on the first chunk only, always &#x60;assistant&#x60;. | [optional] [enum: assistant] |
| **content** | **String** | The text this chunk appends. Null when the chunk carries no text. | [optional] [nullable] |
| **tool\_calls** | [**List**](#model-aiopenaitoolcalldelta) | The tool calls the model requested, emitted in place of text. | [optional] |


### Model AiOpenAIChunkChoice
One choice of a streaming completion, carrying the part this chunk adds.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **index** | **BigDecimal** | The zero-based position of the choice. This service emits a single choice, so always 0. | [required] |
| **delta** | [**AiOpenAIChoiceDelta**](#model-aiopenaichoicedelta) | What this chunk adds to the choice. | [required] |
| **finish\_reason** | [**AiOpenAIFinishReason**](#model-aiopenaifinishreason) | Why the completion stopped, or null while it is still streaming. | [required] [enum: stop, length, tool_calls, content_filter, null] [nullable] |


### Model AiOpenAIFinishReason
OpenAI Chat Completions streaming shapes.   &#x60;toOpenAIChatCompletionStream&#x60; maps the engine&#39;s transport-agnostic &#x60;ChatEvent&#x60; stream onto these chunks so a host can expose an OpenAI-compatible &#x60;POST /v1/chat/completions&#x60; (&#x60;stream: true&#x60;) endpoint backed by the same chat pipeline as the in-app widget. Only the subset of fields the engine can populate is emitted; everything else an OpenAI client tolerates as absent.

Possible values:

- `stop`
- `length`
- `tool_calls`
- `content_filter`
- `null`


### Model AiOpenAIStreamChunk
A chunk or the terminal error envelope emitted on a failed stream.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **id** | **String** | The completion identifier, stable across every chunk of one response. | [required] |
| **object** | **String** | Always &#x60;chat.completion.chunk&#x60;. | [required] [enum: chat.completion.chunk] |
| **created** | **BigDecimal** | When the completion started, in Unix seconds. | [required] |
| **model** | **String** | The model that produced the completion - the resolved profile&#39;s model. | [required] |
| **choices** | [**List**](#model-aiopenaichunkchoice) | The choices carried by this chunk. This service emits exactly one. | [required] |
| **error** | [**AiOpenAIStreamError_error**](#model-aiopenaistreamerrorerror) |  | [required] |


### Model AiOpenAIStreamError
OpenAI streaming error envelope. When the upstream request fails mid-stream the OpenAI API emits a single &#x60;data:&#x60; line carrying an &#x60;error&#x60; object (no &#x60;choices&#x60;), then closes the stream — the official SDK turns this into a thrown &#x60;APIError&#x60;. Mirrors that shape so a host exposing an OpenAI-compatible endpoint stays wire-compatible.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **error** | [**AiOpenAIStreamError_error**](#model-aiopenaistreamerrorerror) |  | [required] |


### Model AiOpenAIStreamError.error
The error that ended the stream: its message, type, code and the offending parameter.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **message** | **String** |  | [required] |
| **type** | **String** |  | [required] |
| **code** | **String** |  | [required] [nullable] |
| **param** | **String** |  | [required] [nullable] |


### Model AiOpenAIToolCallDelta
The incremental part of one tool call the model requested.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **index** | **BigDecimal** | The zero-based position of the tool call within the message. | [required] |
| **id** | **String** | The tool call identifier, quoted back when its result is submitted. | [optional] |
| **type** | **String** | Always &#x60;function&#x60; - the only tool kind the API defines. | [optional] [enum: function] |
| **function** | [**AiOpenAIToolCallDelta_function**](#model-aiopenaitoolcalldeltafunction) |  | [optional] |


### Model AiOpenAIToolCallDelta.function
The call itself: the function name and its JSON-encoded arguments.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **name** | **String** |  | [optional] |
| **arguments** | **String** |  | [optional] |


### Model AiOpenOrCreateResult
Resolved thread state returned by &#x60;ThreadsEngine.openOrCreate&#x60;.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **threadId** | **String** | The thread that was opened, or the one just created. | [required] |
| **title** | **String** | Empty string for existing threads — the engine doesn&#39;t re-fetch. | [required] |
| **priorMessages** | [**List**](#model-aithreadmessagelike) | The messages already in the thread - empty for a thread that was just created. | [required] |


### Model AiProfile
Complete AI provider + model configuration saved by the user. Profiles are the primary way users save and reuse provider configurations.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **id** | **String** | Unique profile identifier (UUID). | [required] |
| **name** | **String** | User-defined profile display name. | [required] |
| **providerType** | [**AiProviderType**](#model-aiprovidertype) | Provider type for this profile. Use &#x60;external&#x60; to delegate all HTTP transport to &#x60;PlatformAdapter.externalFetch&#x60; while reusing an existing provider&#39;s response parser — see &#x60;Profile.basedOn&#x60; for the format selector. | [required] |
| **basedOn** | [**AiBuiltinProviderType**](#model-aibuiltinprovidertype) | Selects the response-format parser used by the &#x60;external&#x60; provider. Ignored for any other &#x60;providerType&#x60;.  Supported values are &#x60;openai&#x60;, &#x60;anthropic&#x60;, &#x60;mistral&#x60; and &#x60;openrouter&#x60;. Remaining values (&#x60;genai&#x60;, &#x60;stabilityai&#x60;, …) are accepted by the type but not yet implemented; passing one raises an error at request time. | [optional] [enum: anthropic, ollama, openai, openaicompatible, together, openrouter, genai, deepseek, xai, lm-studio, mistral, groq, zhipu, stabilityai, gpt4all, onlyoffice, external] |
| **baseUrl** | **String** | Base URL of the provider API. | [required] |
| **key** | **String** | API key or token. Optional for local providers. | [optional] |
| **headers** | **Map** | Extra HTTP headers sent with every request to this provider. Merged into the SDK client&#39;s default headers; an explicit &#x60;Authorization&#x60; here wins over the one derived from &#x60;key&#x60;. Honoured by the OpenAI-family providers. | [optional] |
| **modelId** | **String** | Selected model ID within this provider. | [required] |
| **reasoning** | **Boolean** | Whether extended thinking is enabled for this profile&#39;s model. | [optional] |
| **capabilities** | **BigDecimal** | Bitmask of capabilities supported by the selected model. | [optional] |
| **canUseTool** | **Boolean** | Result of the live tool-capability probe performed at create time and on changes to &#x60;modelId&#x60; / &#x60;providerType&#x60; / &#x60;baseUrl&#x60;. &#x60;undefined&#x60; means the probe has never run for this profile (legacy record). | [optional] |
| **useResponsesApi** | **Boolean** | Result of the live Responses-API probe (parallel to &#x60;canUseTool&#x60;). &#x60;true&#x60; means the model speaks &#x60;/v1/responses&#x60; and the OpenAI provider must route through &#x60;client.responses.create&#x60; — required for gpt-5+ reasoning models that reject &#x60;reasoning_effort&#x60; together with &#x60;tools&#x60; on &#x60;/v1/chat/completions&#x60;. Probed at create time and whenever &#x60;modelId&#x60; / &#x60;providerType&#x60; / &#x60;baseUrl&#x60; change. &#x60;undefined&#x60; means the probe never ran (legacy record) — readers treat that as &#x60;false&#x60;. | [optional] |
| **isCloudProvider** | **Boolean** | Whether this profile uses a cloud-hosted provider (e.g. ONLYOFFICE DocSpace). | [optional] |
| **useProxy** | **Boolean** | Route every provider request through the host&#39;s &#x60;fetchProxy&#x60; instead of the global &#x60;fetch&#x60;. Useful when the host runs the widget in a sandbox without direct network access (CORS, custom auth, etc.). Has no effect when the &#x60;PlatformAdapter.fetchProxy&#x60; is not configured. | [optional] |
| **createdAt** | **BigDecimal** | Creation timestamp (ms since epoch). Used to sort the AI models list newest-first. | [optional] |


### Model AiProfileMutationResult
Outcome of &#x60;create&#x60; / &#x60;update&#x60; — either a success carrying the persisted profile, or a failure with a field-level error description from the name check or the provider credential check.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **success** | **Boolean** | True when the profile was persisted. | [required] |
| **profile** | [**AiProfile**](#model-aiprofile) | The persisted profile. Present on success. | [optional] |
| **error** | [**AiTErrorData**](#model-aiterrordata) | Why the profile was rejected - the name check or the provider credential check. Present on failure. | [optional] |


### Model AiPrompt
Saved prompt template that users can quickly insert into the chat.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **id** | **String** | Unique prompt identifier (UUID). | [required] |
| **name** | **String** | Prompt display name shown in the prompt picker. | [required] |
| **text** | **String** | Prompt template text. May contain placeholder tokens. | [required] |
| **folderId** | **String** | Optional parent folder ID. &#x60;undefined&#x60; means the prompt is at the root level. | [optional] |
| **createdAt** | **BigDecimal** | Timestamp (ms since epoch) when the prompt was created. | [required] |
| **updatedAt** | **BigDecimal** | Timestamp (ms since epoch) of the last prompt modification. | [required] |


### Model AiPromptBundle
Versioned, self-contained bundle of every saved prompt and folder. Stable wire format — &#x60;version&#x60; lets the import path migrate older shapes if the schema ever changes.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **version** | **BigDecimal** | The bundle format version, so an import can migrate an older export. | [required] [enum: 1] |
| **folders** | [**List**](#model-aipromptfolder) | Every exported prompt folder. | [required] |
| **prompts** | [**List**](#model-aiprompt) | Every exported prompt. | [required] |


### Model AiPromptFolder
Folder for organizing saved prompts.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **id** | **String** | Unique folder identifier (UUID). | [required] |
| **name** | **String** | Folder display name. | [required] |
| **createdAt** | **BigDecimal** | Timestamp (ms since epoch) when the folder was created. | [required] |
| **updatedAt** | **BigDecimal** | Timestamp (ms since epoch) of the last folder modification. | [required] |


### Model AiPromptMutationResult
Outcome of &#x60;create&#x60; / &#x60;update&#x60; / &#x60;move&#x60; on a prompt — either the persisted prompt or a field-scoped error.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **success** | **Boolean** | True when the prompt was persisted. | [required] |
| **prompt** | [**AiPrompt**](#model-aiprompt) | The persisted prompt. Present on success. | [optional] |
| **error** | [**AiTErrorData**](#model-aiterrordata) | Why the prompt was rejected. Present on failure. | [optional] |


### Model AiProviderType
Provider type identifier. Accepts all 17 built-in types with autocomplete, plus any custom &#x60;string&#x60; for dynamically registered providers.


### Model AiResolvedAssignment
Resolved profile for an action — both the storage row and its ID.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **profileId** | **String** | The identifier of the resolved profile. | [required] |
| **profile** | [**AiProfile**](#model-aiprofile) | The resolved profile itself. | [required] |


### Model AiRoomDataLifetimeDto
The room data lifetime information.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **deletePermanently** | **Boolean** | Specifies whether to permanently delete the room data or not. | [optional] [example: true] |
| **period** | [**AiRoomDataLifetimePeriod**](#model-airoomdatalifetimeperiod) | Specifies the time period type of the room data lifetime. | [optional] [enum: 0, 1, 2] |
| **value** | **Integer** (int32) | Specifies the time period value of the room data lifetime. | [optional] [example: 33] [min: 1] [max: 999] [nullable] |
| **enabled** | **Boolean** | Specifies whether the room data lifetime setting is enabled or not. | [optional] [example: true] [nullable] |


### Model AiRoomDataLifetimePeriod

Possible values:

- `0` — Day (`Day`)
- `1` — Month (`Month`)
- `2` — Year (`Year`)


### Model AiRoomType

Possible values:

- `1` — Form filling room (`FillingFormsRoom`)
- `2` — Collaboration room (`EditingRoom`)
- `5` — Custom room (`CustomRoom`)
- `6` — Public room (`PublicRoom`)
- `8` — Virtual data room (`VirtualDataRoom`)
- `9` — AI Room (`AiRoom`)


### Model AiSuccessResponse
Generic success acknowledgement for mutations that return no data.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **success** | **Boolean** | Always true — the mutation completed. | [required] |


### Model AiTErrorData
A field-scoped validation error: which form field was rejected, and why.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **field** | **String** | The rejected field. | [required] [enum: key, url, name] |
| **message** | **String** | The human-readable reason the field was rejected. | [required] |


### Model AiTMCPItem
Descriptor for a tool exposed by an MCP server.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **name** | **String** | Tool name as registered on the MCP server (e.g. &#x60;web_search&#x60;, &#x60;insert_text&#x60;). | [required] |
| **description** | **String** | Human-readable description shown to the AI model and in the tools list UI. | [required] |
| **inputSchema** | **Object** | JSON Schema describing the tool&#39;s input parameters. | [required] |
| **enabled** | **Boolean** | Whether this tool is currently enabled. Disabled tools are hidden from the AI model. | [optional] |
| **serverType** | **String** | Server type (MCP server name / host tool group id) this tool belongs to — the key the persisted disabled map is stored under. Set by the source that enumerated the tool, so a caller-supplied tool can still be attributed to its group after being flattened into a single list: that is what lets the engine apply the disabled map to &#x60;actionArgs.tools&#x60; instead of trusting the caller to pre-filter. Wire-serializable, so it survives a remote (server-side) engine. | [optional] |
| **requireApproval** | **Boolean** | Whether the consumer must show an approval dialog before this tool runs. The engine reads it when deciding the &#x60;autoAllow&#x60; flag on a &#x60;tool-call-pending&#x60; event: &#x60;requireApproval &#x3D;&#x3D;&#x3D; false&#x60; auto-allows the call (no dialog), &#x60;true&#x60; always prompts. &#x60;undefined&#x60; leaves the decision to the persisted always-allow list alone — so MCP / custom-server tools (which never set it) keep prompting as before, while host tools opt into auto-allow by default. Wire-serializable, so it survives a remote (server-side) engine. | [optional] |


### Model AiTProvider
Minimal provider connection configuration. Used to connect to a provider API.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **type** | [**AiProviderType**](#model-aiprovidertype) | Provider type identifier. | [required] |
| **name** | **String** | User-defined display name for this provider connection. | [required] |
| **key** | **String** | API key or token. Optional for local providers (Ollama, LM Studio). | [optional] |
| **baseUrl** | **String** | Base URL of the provider API. | [required] |


### Model AiThread
Chat conversation metadata. Represents a single chat session (thread).

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **threadId** | **String** | Unique thread identifier (UUID). | [required] |
| **title** | **String** | Optional thread title. Auto-generated from the first message if not set. | [optional] |
| **lastEditDate** | **BigDecimal** | Timestamp (ms since epoch) of the last message in this thread. Used for sorting. | [optional] |
| **provider** | [**AiTProvider**](#model-aitprovider) | Provider configuration at the time of last message. Used for thread-level provider display. | [optional] |
| **model** | [**AiModel**](#model-aimodel) | Model info at the time of last message. | [optional] |
| **profileId** | **String** | ID of the profile used for this thread. Links to &#x60;Profile.id&#x60;. | [optional] |


### Model AiThreadMessageLike
A single chat message as it travels on the wire.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **id** | **String** | Storage-assigned message id (absent on inbound drafts). | [optional] |
| **role** | **String** | Message author role. | [required] [enum: user, assistant, system] |
| **content** | [**AiThreadMessageLike_content**](#model-aithreadmessagelikecontent) |  | [required] |
| **createdAt** | **String** | Creation timestamp, ISO-8601 on the wire. | [optional] |
| **status** | [**AiThreadMessageLike_status**](#model-aithreadmessagelikestatus) |  | [optional] |
| **metadata** | **Object** | Arbitrary per-message metadata. | [optional] |
| **attachments** | **List** | Attachments linked to the message. | [optional] |


### Model AiThreadMessageLike.content
Message content: either plain text or a list of typed content parts (text, image, tool-call, …). Parts are open-ended by content type.


### Model AiThreadMessageLike.content.anyOf item

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **type** | **String** |  | [required] |
| **text** | **String** |  | [optional] |


### Model AiThreadMessageLike.status
Delivery/generation status of the message.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **type** | **String** |  | [required] |


### Model AiToolsBulkResult
Outcome of &#x60;ToolsEngine.replaceAllCustomServers&#x60; — either every entry persisted, or no entries persisted plus a per-key error report.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **success** | **Boolean** | True when every custom MCP server was persisted. | [required] |
| **errors** | [**List**](#model-aitoolsbulkresulterrors-item) | What was rejected, per server. Present on failure - and then no server was persisted. | [optional] |


### Model AiToolsBulkResult.errors item

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **name** | **String** |  | [required] |
| **error** | [**AiTErrorData**](#model-aiterrordata) |  | [required] |


### Model AiToolsMutationResult
Outcome of an MCP-server CRUD call. Either success or a field-scoped error suitable for the settings form.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **success** | **Boolean** | True when the MCP server was persisted. | [required] |
| **error** | [**AiTErrorData**](#model-aiterrordata) | Why the MCP server was rejected. Present on failure. | [optional] |


### Model AiVectorizationSettingsDto
The vectorization settings.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **type** | [**AiEmbeddingProviderType**](#model-aiembeddingprovidertype) | The type of embedding provider configured for document vectorization. | [optional] [enum: 0, 1, 2, 3] |
| **needReset** | **Boolean** | Indicates whether the embedding provider API key needs to be reconfigured. | [optional] [example: false] |


### Model AiVectorizationSettingsWrapper
The successful API response containing the VectorizationSettingsDto object.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **response** | [**AiVectorizationSettingsDto**](#model-aivectorizationsettingsdto) | The VectorizationSettingsDto object returned by the operation. | [optional] |
| **count** | **Integer** (int32) | The total number of items in the response | [optional] |
| **links** | [**List**](#model-aiaiusersettingswrapperlinks-item) | List of links related to the response | [optional] |
| **status** | **Integer** (int32) | HTTP status code of the response | [optional] |
| **statusCode** | **Integer** (int32) | HTTP status code of the response (duplicate of status) | [optional] |


### Model AiWatermarkAdditions

Possible values:

- `1` — User name (`UserName`)
- `2` — User email (`UserEmail`)
- `4` — User ip adress (`UserIpAdress`)
- `8` — Current date (`CurrentDate`)
- `16` — Room name (`RoomName`)


### Model AiWatermarkDto
The watermark settings.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **additions** | [**AiWatermarkAdditions**](#model-aiwatermarkadditions) | Specifies whether to display in the watermark: username, user email, user ip-adress, current date, and room name. | [required] [enum: 1, 2, 4, 8, 16] |
| **text** | **String** | The watermark text. | [optional] [example: Confidential] [nullable] |
| **rotate** | **Integer** (int32) | The watermark text and image rotate. | [required] [example: 45] |
| **imageScale** | **Integer** (int32) | The watermark image scale. | [required] [example: 100] |
| **imageUrl** | **String** | The watermark image url. | [optional] [example: http://localhost/watermark.png] [nullable] |
| **imageHeight** | **Double** (double) | The watermark image height. | [required] [example: 100] |
| **imageWidth** | **Double** (double) | The watermark image width. | [required] [example: 200] |


### Model AiWebSearchConfig
Web-search provider configuration. Credentials and provider selection for the built-in web-search tool group.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **provider** | **String** | Provider identifier (e.g. &#x60;exa&#x60;). | [required] |
| **key** | **String** | API key for the provider. Optional for self-hosted or keyless setups. | [optional] |
| **baseUrl** | **String** | Optional override for the provider&#39;s base URL. | [optional] |
| **isCloudProvider** | **Boolean** | Whether this provider is cloud-hosted (vs. self-hosted). | [optional] |
| **headers** | **Map** | Extra HTTP headers sent with each request to the ONLYOFFICE / cloud backend (e.g. &#x60;X-Tenant&#x60;). Merged after the derived &#x60;Authorization&#x60; header, so a custom header of the same name wins. | [optional] |


### Model AiWebSearchMutationResult
Outcome of &#x60;WebSearchEngine.configure&#x60; — either the persisted config or a field-scoped error suitable for the settings form.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **success** | **Boolean** | True when the configuration was persisted. | [required] |
| **config** | [**AiWebSearchConfig**](#model-aiwebsearchconfig) | The persisted web-search configuration. Present on success. | [optional] |
| **error** | [**AiTErrorData**](#model-aiterrordata) | Why the configuration was rejected. Present on failure. | [optional] |


### Model aiAgentsCreate request body

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **profileId** | **String** | Profile id bound to the agent. | [required] |
| **prompt** | **String** | Agent system prompt; stored as the room&#39;s &#x60;chatSettings.prompt&#x60;. | [required] |
| **private** | **Boolean** | Whether the agent room is private. | [optional] |
| **share** | **List** | Initial share entries (&#x60;FileShareParams&#x60;). | [optional] |
| **attachDefaultTools** | **Boolean** | Whether to attach the default DocSpace MCP tool server. | [optional] |
| **title** | **String** | Agent (room) title. | [optional] |
| **quota** | **BigDecimal** | Room quota in bytes. | [optional] |
| **indexing** | **Boolean** | Whether room content is indexed for search. | [optional] |
| **denyDownload** | **Boolean** | Whether downloading room content is denied. | [optional] |
| **lifetime** | **Object** | Room data lifetime policy (&#x60;RoomDataLifetimeDto&#x60;). | [optional] |
| **watermark** | **Object** | Watermark settings (&#x60;WatermarkRequestDto&#x60;). | [optional] |
| **logo** | **Object** | Room logo (&#x60;LogoRequest&#x60;). | [optional] |
| **tags** | **List** | Room tags. | [optional] |
| **color** | **String** | Room accent color. | [optional] |
| **cover** | **String** | Room cover image id. | [optional] |


### Model aiAgentsDelete request body

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **deleteAfter** | **Boolean** | Delete the room after the editing session finishes. | [optional] |


### Model aiAgentsResetQuota request body

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **roomIds** | [**List**](#model-aiagentsupdatequotarequestroomids-item) | Agent (room) ids to reset to the tenant default quota. | [required] |


### Model aiAgentsUpdateQuota request body

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **roomIds** | [**List**](#model-aiagentsupdatequotarequestroomids-item) | Agent (room) ids to update. | [required] |
| **quota** | **BigDecimal** | New quota in bytes; a negative value disables the custom quota. | [required] |


### Model aiAgentsUpdateQuota.request.roomIds item
A DocSpace room id: an integer for native rooms, a string for third-party-backed ones.


### Model aiAgentsUpdate request body

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **profileId** | **String** | Profile id to rebind (optional). | [optional] |
| **chatSettings** | **Object** | Chat settings (&#x60;ChatSettings&#x60;); requires a valid provider/model. | [optional] |
| **sendFormToExternalDB** | **Boolean** | Whether form results are sent to an external DB. | [optional] |
| **saveFormAsXLSX** | **Boolean** | Whether forms are saved as XLSX. | [optional] |
| **title** | **String** | Agent (room) title. | [optional] |
| **quota** | **BigDecimal** | Room quota in bytes. | [optional] |
| **indexing** | **Boolean** | Whether room content is indexed for search. | [optional] |
| **denyDownload** | **Boolean** | Whether downloading room content is denied. | [optional] |
| **lifetime** | **Object** | Room data lifetime policy (&#x60;RoomDataLifetimeDto&#x60;). | [optional] |
| **watermark** | **Object** | Watermark settings (&#x60;WatermarkRequestDto&#x60;). | [optional] |
| **logo** | **Object** | Room logo (&#x60;LogoRequest&#x60;). | [optional] |
| **tags** | **List** | Room tags. | [optional] |
| **color** | **String** | Room accent color. | [optional] |
| **cover** | **String** | Room cover image id. | [optional] |


### Model aiAiApproveToolCall request body

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **result** | **oas_any_type_not_mapped** |  | [required] [nullable] |
| **allowAlways** | **Boolean** | Persist auto-approve for this tool&#39;s name. | [optional] |
| **threadId** | **String** | Thread the assistant message belongs to. | [required] |
| **messageId** | **String** | Storage id of the assistant message holding the tool call. | [required] |
| **idx** | **BigDecimal** | Index of the tool-call content part inside &#x60;message.content&#x60;. | [required] |
| **message** | [**AiThreadMessageLike**](#model-aithreadmessagelike) | Snapshot of the assistant message at the time the tool call surfaced. | [required] |
| **actionArgs** | [**AiAiActionArgs**](#model-aiaiactionargs) | Per-request engine options: extra tools, reasoning, prompt override. | [optional] |
| **entityId** | **String** | Optional entity (room) scope for profile resolution. | [optional] |
| **profileId** | **String** | Session-level profile override for this request only. | [optional] |


### Model aiAiRegenerateStream request body

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **threadId** | **String** | Target thread (must already exist). | [required] |
| **actionArgs** | [**AiAiActionArgs**](#model-aiaiactionargs) | Per-request engine options: extra tools, reasoning, prompt override. | [optional] |
| **entityId** | **String** | Optional entity (room) scope for profile resolution. | [optional] |
| **profileId** | **String** | Session-level profile override for this request only. | [optional] |


### Model aiAiSendCustom request body

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **isStream** | **Boolean** | Stream the reply (ndjson) when true, else return a single message. | [required] |
| **systemPrompt** | **String** | Caller-supplied system prompt for this one-turn call. | [required] |
| **userMessage** | [**AiThreadMessageLike**](#model-aithreadmessagelike) |  | [required] |
| **actionArgs** | [**AiAiActionArgs**](#model-aiaiactionargs) | Per-request engine options: extra tools, reasoning, prompt override. | [optional] |


### Model aiAiSend request body

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **actionType** | [**AiActionType**](#model-aiactiontype) | Which AI action to run — selects the assignment slot and action. | [required] [enum: Default, Chat, Code, Summarization, Translation, TextAnalyze, ImageGeneration, OCR, Vision] |
| **userMessage** | [**AiThreadMessageLike**](#model-aithreadmessagelike) | The user turn to send. | [required] |
| **actionArgs** | [**AiAiActionArgs**](#model-aiaiactionargs) | Per-request engine options: extra tools, reasoning, prompt override. | [optional] |
| **entityId** | **String** | Optional entity (room) scope for profile resolution. | [optional] |


### Model aiAssignmentsAssign request body

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **actionType** | [**AiActionType**](#model-aiactiontype) | Action the assignment applies to. | [required] [enum: Default, Chat, Code, Summarization, Translation, TextAnalyze, ImageGeneration, OCR, Vision] |
| **profileId** | **String** | Profile id to bind. | [required] |


### Model aiAttachmentsLinkToMessage request body

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **ids** | **List** | Attachment ids to bind. | [required] |
| **messageId** | **String** | Owning message id. | [required] |
| **threadId** | **String** | Owning thread id. | [required] |


### Model aiAttachmentsSaveFile request body

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **input** | [**aiAttachmentsSaveFile_request_input**](#model-aiattachmentssavefilerequestinput) |  | [required] |
| **entityId** | **String** | Optional entity (room) scope. | [optional] |


### Model aiAttachmentsSaveFile.request.input
A file attachment draft to persist.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **path** | **String** | Storage path/key of the file. | [required] |
| **content** | **String** | File contents. | [required] |
| **type** | **BigDecimal** | File type discriminator. | [required] |
| **title** | **String** | Optional display title. | [optional] |


### Model aiAttachmentsSaveFilesMany request body

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **inputs** | [**List**](#model-aiattachmentssavefilerequestinput) |  | [required] |
| **entityId** | **String** |  | [optional] |


### Model aiExportTextToDocx 200 response
Accepted-for-processing acknowledgement (conversion is asynchronous).

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **success** | **Boolean** |  | [required] |


### Model aiExportTextToDocx request body

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **title** | **String** | Document title (also the file name). | [required] |
| **content** | **String** | Markdown content to convert. | [required] |
| **folderId** | [**aiExportTextToDocx_request_folderId**](#model-aiexporttexttodocxrequestfolderid) |  | [required] |


### Model aiExportTextToDocx.request.folderId
Target folder id (int or string).


### Model aiPreferencesSetDeepMode request body

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **value** | **Boolean** | New deep-mode value. | [required] |
| **entityId** | **String** |  | [optional] |


### Model aiProfilesGetById 200 response

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **id** | **String** | Unique profile identifier (UUID). | [required] |
| **name** | **String** | User-defined profile display name. | [required] |
| **providerType** | [**AiProviderType**](#model-aiprovidertype) | Provider type for this profile. Use &#x60;external&#x60; to delegate all HTTP transport to &#x60;PlatformAdapter.externalFetch&#x60; while reusing an existing provider&#39;s response parser — see &#x60;Profile.basedOn&#x60; for the format selector. | [required] |
| **basedOn** | [**AiBuiltinProviderType**](#model-aibuiltinprovidertype) | Selects the response-format parser used by the &#x60;external&#x60; provider. Ignored for any other &#x60;providerType&#x60;.  Supported values are &#x60;openai&#x60;, &#x60;anthropic&#x60;, &#x60;mistral&#x60; and &#x60;openrouter&#x60;. Remaining values (&#x60;genai&#x60;, &#x60;stabilityai&#x60;, …) are accepted by the type but not yet implemented; passing one raises an error at request time. | [optional] [enum: anthropic, ollama, openai, openaicompatible, together, openrouter, genai, deepseek, xai, lm-studio, mistral, groq, zhipu, stabilityai, gpt4all, onlyoffice, external] |
| **baseUrl** | **String** | Base URL of the provider API. | [required] |
| **modelId** | **String** | Selected model ID within this provider. | [required] |
| **reasoning** | **Boolean** | Whether extended thinking is enabled for this profile&#39;s model. | [optional] |
| **capabilities** | **BigDecimal** | Bitmask of capabilities supported by the selected model. | [optional] |
| **canUseTool** | **Boolean** | Result of the live tool-capability probe performed at create time and on changes to &#x60;modelId&#x60; / &#x60;providerType&#x60; / &#x60;baseUrl&#x60;. &#x60;undefined&#x60; means the probe has never run for this profile (legacy record). | [optional] |
| **useResponsesApi** | **Boolean** | Result of the live Responses-API probe (parallel to &#x60;canUseTool&#x60;). &#x60;true&#x60; means the model speaks &#x60;/v1/responses&#x60; and the OpenAI provider must route through &#x60;client.responses.create&#x60; — required for gpt-5+ reasoning models that reject &#x60;reasoning_effort&#x60; together with &#x60;tools&#x60; on &#x60;/v1/chat/completions&#x60;. Probed at create time and whenever &#x60;modelId&#x60; / &#x60;providerType&#x60; / &#x60;baseUrl&#x60; change. &#x60;undefined&#x60; means the probe never ran (legacy record) — readers treat that as &#x60;false&#x60;. | [optional] |
| **isCloudProvider** | **Boolean** | Whether this profile uses a cloud-hosted provider (e.g. ONLYOFFICE DocSpace). | [optional] |
| **useProxy** | **Boolean** | Route every provider request through the host&#39;s &#x60;fetchProxy&#x60; instead of the global &#x60;fetch&#x60;. Useful when the host runs the widget in a sandbox without direct network access (CORS, custom auth, etc.). Has no effect when the &#x60;PlatformAdapter.fetchProxy&#x60; is not configured. | [optional] |
| **createdAt** | **BigDecimal** | Creation timestamp (ms since epoch). Used to sort the AI models list newest-first. | [optional] |


### Model aiProfilesListProviderModels request body

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **providerType** | [**AiProviderType**](#model-aiprovidertype) | Provider whose catalog to list. | [required] |
| **baseUrl** | **String** | Provider API base URL. | [required] |
| **apiKey** | **String** | Provider API key. | [required] |


### Model aiProfilesTestConnection 200 response

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **message** | **String** |  | [optional] |


### Model aiProfilesTestConnection 200 response.anyOf

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **message** | **String** |  | [optional] |


### Model aiPromptsImportBundle request body

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **bundle** | [**AiPromptBundle**](#model-aipromptbundle) | Bundle to restore. | [required] |
| **options** | [**aiPromptsImportBundle_request_options**](#model-aipromptsimportbundlerequestoptions) |  | [optional] |


### Model aiPromptsImportBundle.request.options
Import options.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **mode** | [**AiImportMode**](#model-aiimportmode) |  | [optional] [enum: replace, merge] |


### Model aiPromptsMove request body

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **id** | **String** | Prompt id to move. | [required] |
| **folderId** | **String** | Target folder id, or &#x60;null&#x60; for root. | [required] [nullable] |


### Model aiPromptsRenameFolder request body

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **id** | **String** | Folder id to rename. | [required] |
| **name** | **String** | New folder name. | [required] |


### Model aiPromptsUpdate request body

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **id** | **String** | Prompt id to update. | [required] |
| **updates** | [**aiPromptsUpdate_request_updates**](#model-aipromptsupdaterequestupdates) |  | [required] |


### Model aiPromptsUpdate.request.updates
Fields to change.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **name** | **String** |  | [optional] |
| **text** | **String** |  | [optional] |
| **folderId** | **String** |  | [optional] [nullable] |


### Model aiThreadsAppendUserMessage request body

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **threadId** | **String** |  | [required] |
| **message** | [**AiThreadMessageLike**](#model-aithreadmessagelike) | Message to persist (id/createdAt are storage-assigned). | [required] |
| **profileId** | **String** |  | [optional] |


### Model aiThreadsCreate request body

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **title** | **String** | Thread title. | [required] |
| **profileId** | **String** | Optional profile to bind. | [optional] |
| **entityId** | **String** | Optional entity (room) scope. | [optional] |


### Model aiThreadsOpenOrCreate request body

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **threadId** | **String** |  | [optional] |
| **profile** | [**AiProfile**](#model-aiprofile) | Profile the title generation runs on. | [required] |
| **profileId** | **String** |  | [required] |
| **firstMessage** | [**AiThreadMessageLike**](#model-aithreadmessagelike) | First user message a fresh thread derives its title from. | [required] |
| **entityId** | **String** | Opaque scope token persisted on a freshly created thread. | [optional] |
| **entityMeta** | [**aiThreadsOpenOrCreate_request_entityMeta**](#model-aithreadsopenorcreaterequestentitymeta) |  | [optional] |


### Model aiThreadsOpenOrCreate.request.entityMeta
Optional entity hint (lib 0.5.64): only &#x60;entityId&#x60; is read; the pair is re-resolved server-side before reaching the provider as metadata.

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **entityId** | **String** |  | [optional] |
| **entityTitle** | **String** |  | [optional] |


### Model aiThreadsRegenerateTitle request body

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **threadId** | **String** |  | [required] |
| **profile** | [**AiProfile**](#model-aiprofile) | Profile used to regenerate the title. | [required] |
| **entityMeta** | [**aiThreadsOpenOrCreate_request_entityMeta**](#model-aithreadsopenorcreaterequestentitymeta) |  | [optional] |


### Model aiThreadsRename request body

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **threadId** | **String** |  | [required] |
| **title** | **String** | New thread title. | [required] |


### Model aiThreadsTouch request body

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **threadId** | **String** |  | [required] |
| **profileId** | **String** |  | [optional] |


### Model aiThreadsUpdateMessage request body

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **messageId** | **String** |  | [required] |
| **message** | [**AiThreadMessageLike**](#model-aithreadmessagelike) | Replacement message content. | [required] |


### Model aiToolsAddCustomServer request body

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **name** | **String** | Server name (unique within scope). | [required] |
| **config** | **Object** | Server transport configuration. | [required] |
| **entityId** | **String** |  | [optional] |


### Model aiToolsRemoveCustomServer request body

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **name** | **String** |  | [required] |
| **entityId** | **String** |  | [optional] |


### Model aiToolsReplaceAllCustomServers request body

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **map** | **Map** | Full replacement set, keyed by server name. | [required] |
| **entityId** | **String** |  | [optional] |


### Model aiToolsSetAllowAlways request body

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **serverType** | **String** |  | [required] |
| **toolName** | **String** |  | [required] |
| **value** | **Boolean** | Whether the tool is always allowed. | [required] |
| **entityId** | **String** |  | [optional] |


### Model aiToolsSetDisabled request body

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **serverType** | **String** |  | [required] |
| **toolNames** | **List** | Tool names to disable. | [required] |
| **entityId** | **String** |  | [optional] |


### Model aiToolsUpdateCustomServer request body

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **name** | **String** |  | [required] |
| **config** | **Object** | One MCP server configuration. The shape is intentionally open — MCP allows per-transport fields (&#x60;command&#x60;/&#x60;args&#x60; for stdio, &#x60;url&#x60; for HTTP, plus env, headers, etc.) and the storage layer stays agnostic to which transport is in use. | [required] |
| **entityId** | **String** |  | [optional] |


### Model aiWebSearchConfigure request body

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **config** | [**AiWebSearchConfig**](#model-aiwebsearchconfig) |  | [required] |
| **entityId** | **String** |  | [optional] |


## Authorization


### asc_auth_key
- **Type**: API key
- **API key parameter name**: asc_auth_key
- **Location**: 


### Basic

- **Type**: HTTP basic authentication


### Bearer

- **Type**: HTTP Bearer Token authentication (JWT)


### ApiKeyBearer
- **Type**: API key
- **API key parameter name**: ApiKeyBearer
- **Location**: HTTP header


### OAuth2

- **Type**: OAuth
- **Flow**: accessCode
- **Authorization URL**: 
- **Scopes**: 
  - read: Read access to protected resources
  - write: Write access to protected resources


### OpenId


### cookieAuth
- **Type**: API key
- **API key parameter name**: asc_auth_key
- **Location**: 


### bearerAuth

- **Type**: HTTP Bearer Token authentication


### x-signature
- **Type**: API key
- **API key parameter name**: x-signature
- **Location**: 

