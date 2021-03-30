# Protocol Documentation
<a name="top"></a>

## Table of Contents

- [auth/v1/auth.proto](#auth/v1/auth.proto)
    - [UserCreateRequest](#nitric.auth.v1.UserCreateRequest)
    - [UserCreateResponse](#nitric.auth.v1.UserCreateResponse)
  
    - [User](#nitric.auth.v1.User)
  
- [event/v1/event.proto](#event/v1/event.proto)
    - [EventPublishRequest](#nitric.event.v1.EventPublishRequest)
    - [EventPublishResponse](#nitric.event.v1.EventPublishResponse)
    - [NitricEvent](#nitric.event.v1.NitricEvent)
    - [NitricTopic](#nitric.event.v1.NitricTopic)
    - [TopicListRequest](#nitric.event.v1.TopicListRequest)
    - [TopicListResponse](#nitric.event.v1.TopicListResponse)
  
    - [Event](#nitric.event.v1.Event)
    - [Topic](#nitric.event.v1.Topic)
  
- [kv/v1/kv.proto](#kv/v1/kv.proto)
    - [KeyValueDeleteRequest](#nitric.kv.v1.KeyValueDeleteRequest)
    - [KeyValueDeleteResponse](#nitric.kv.v1.KeyValueDeleteResponse)
    - [KeyValueGetRequest](#nitric.kv.v1.KeyValueGetRequest)
    - [KeyValueGetResponse](#nitric.kv.v1.KeyValueGetResponse)
    - [KeyValuePutRequest](#nitric.kv.v1.KeyValuePutRequest)
    - [KeyValuePutResponse](#nitric.kv.v1.KeyValuePutResponse)
  
    - [KeyValue](#nitric.kv.v1.KeyValue)
  
- [queue/v1/queue.proto](#queue/v1/queue.proto)
    - [FailedTask](#nitric.queue.v1.FailedTask)
    - [NitricTask](#nitric.queue.v1.NitricTask)
    - [QueueCompleteRequest](#nitric.queue.v1.QueueCompleteRequest)
    - [QueueCompleteResponse](#nitric.queue.v1.QueueCompleteResponse)
    - [QueueReceiveRequest](#nitric.queue.v1.QueueReceiveRequest)
    - [QueueReceiveResponse](#nitric.queue.v1.QueueReceiveResponse)
    - [QueueSendBatchRequest](#nitric.queue.v1.QueueSendBatchRequest)
    - [QueueSendBatchResponse](#nitric.queue.v1.QueueSendBatchResponse)
    - [QueueSendRequest](#nitric.queue.v1.QueueSendRequest)
    - [QueueSendResponse](#nitric.queue.v1.QueueSendResponse)
  
    - [Queue](#nitric.queue.v1.Queue)
  
- [storage/v1/storage.proto](#storage/v1/storage.proto)
    - [StorageDeleteRequest](#nitric.storage.v1.StorageDeleteRequest)
    - [StorageDeleteResponse](#nitric.storage.v1.StorageDeleteResponse)
    - [StorageReadRequest](#nitric.storage.v1.StorageReadRequest)
    - [StorageReadResponse](#nitric.storage.v1.StorageReadResponse)
    - [StorageWriteRequest](#nitric.storage.v1.StorageWriteRequest)
    - [StorageWriteResponse](#nitric.storage.v1.StorageWriteResponse)
  
    - [Storage](#nitric.storage.v1.Storage)
  
- [Scalar Value Types](#scalar-value-types)



<a name="auth/v1/auth.proto"></a>
<p align="right"><a href="#top">Top</a></p>

## auth/v1/auth.proto



<a name="nitric.auth.v1.UserCreateRequest"></a>

### UserCreateRequest
Request to create a new user in the given tenant (user pool).


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| tenant | [string](#string) |  |  |
| id | [string](#string) |  |  |
| email | [string](#string) |  |  |
| password | [string](#string) |  |  |






<a name="nitric.auth.v1.UserCreateResponse"></a>

### UserCreateResponse
Successful create requests provide no response currently.





 

 

 


<a name="nitric.auth.v1.User"></a>

### User
Service for user management activities, such as creating and deleting users

| Method Name | Request Type | Response Type | Description |
| ----------- | ------------ | ------------- | ------------|
| Create | [UserCreateRequest](#nitric.auth.v1.UserCreateRequest) | [UserCreateResponse](#nitric.auth.v1.UserCreateResponse) | Create a new user in a tenant |

 



<a name="event/v1/event.proto"></a>
<p align="right"><a href="#top">Top</a></p>

## event/v1/event.proto



<a name="nitric.event.v1.EventPublishRequest"></a>

### EventPublishRequest
Request to publish an event to a topic


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| topic | [string](#string) |  | The name of the topic to publish the event to |
| event | [NitricEvent](#nitric.event.v1.NitricEvent) |  | The event to be published |






<a name="nitric.event.v1.EventPublishResponse"></a>

### EventPublishResponse
Result of publishing an event






<a name="nitric.event.v1.NitricEvent"></a>

### NitricEvent
Nitric Event Model


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | [string](#string) |  | A Unique ID for the Nitric Event |
| payloadType | [string](#string) |  | A content hint for the events payload |
| payload | [google.protobuf.Struct](#google.protobuf.Struct) |  | The payload of the event |






<a name="nitric.event.v1.NitricTopic"></a>

### NitricTopic
Represents an event topic


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| name | [string](#string) |  | The Nitric name for the topic |






<a name="nitric.event.v1.TopicListRequest"></a>

### TopicListRequest
Request for the Topic List method






<a name="nitric.event.v1.TopicListResponse"></a>

### TopicListResponse
Topic List Response


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| topics | [NitricTopic](#nitric.event.v1.NitricTopic) | repeated | The list of found topics |





 

 

 


<a name="nitric.event.v1.Event"></a>

### Event
Service for publishing asynchronous event

| Method Name | Request Type | Response Type | Description |
| ----------- | ------------ | ------------- | ------------|
| Publish | [EventPublishRequest](#nitric.event.v1.EventPublishRequest) | [EventPublishResponse](#nitric.event.v1.EventPublishResponse) | Publishes an message to a given topic |


<a name="nitric.event.v1.Topic"></a>

### Topic
Service for management of event topics

| Method Name | Request Type | Response Type | Description |
| ----------- | ------------ | ------------- | ------------|
| List | [TopicListRequest](#nitric.event.v1.TopicListRequest) | [TopicListResponse](#nitric.event.v1.TopicListResponse) | Return a list of existing topics in the provider environment |

 



<a name="kv/v1/kv.proto"></a>
<p align="right"><a href="#top">Top</a></p>

## kv/v1/kv.proto



<a name="nitric.kv.v1.KeyValueDeleteRequest"></a>

### KeyValueDeleteRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| collection | [string](#string) |  | The collection containing the existing keyValue to be deleted |
| key | [string](#string) |  | The unique key of the keyValue to delete |






<a name="nitric.kv.v1.KeyValueDeleteResponse"></a>

### KeyValueDeleteResponse







<a name="nitric.kv.v1.KeyValueGetRequest"></a>

### KeyValueGetRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| collection | [string](#string) |  | The collection to retrieve the keyValue from |
| key | [string](#string) |  | The unique key of the keyValue to retrieve |






<a name="nitric.kv.v1.KeyValueGetResponse"></a>

### KeyValueGetResponse



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| value | [google.protobuf.Struct](#google.protobuf.Struct) |  | The retrieved value |






<a name="nitric.kv.v1.KeyValuePutRequest"></a>

### KeyValuePutRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| collection | [string](#string) |  | The collection containing the existing keyValue to be inserted or updated. |
| key | [string](#string) |  | The unique key of the keyValue to put |
| value | [google.protobuf.Struct](#google.protobuf.Struct) |  | A simple JSON object |






<a name="nitric.kv.v1.KeyValuePutResponse"></a>

### KeyValuePutResponse






 

 

 


<a name="nitric.kv.v1.KeyValue"></a>

### KeyValue
Service for storage and retrieval of simple JSON keyValue

| Method Name | Request Type | Response Type | Description |
| ----------- | ------------ | ------------- | ------------|
| Get | [KeyValueGetRequest](#nitric.kv.v1.KeyValueGetRequest) | [KeyValueGetResponse](#nitric.kv.v1.KeyValueGetResponse) | Get an existing key |
| Put | [KeyValuePutRequest](#nitric.kv.v1.KeyValuePutRequest) | [KeyValuePutResponse](#nitric.kv.v1.KeyValuePutResponse) | Create a new or overwrite and existing key |
| Delete | [KeyValueDeleteRequest](#nitric.kv.v1.KeyValueDeleteRequest) | [KeyValueDeleteResponse](#nitric.kv.v1.KeyValueDeleteResponse) | Delete an existing |

 



<a name="queue/v1/queue.proto"></a>
<p align="right"><a href="#top">Top</a></p>

## queue/v1/queue.proto



<a name="nitric.queue.v1.FailedTask"></a>

### FailedTask



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| task | [NitricTask](#nitric.queue.v1.NitricTask) |  | The task that failed to be pushed |
| message | [string](#string) |  | A message describing the failure |






<a name="nitric.queue.v1.NitricTask"></a>

### NitricTask
A task to be sent or received from a queue.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | [string](#string) |  | A unique id for the task |
| leaseId | [string](#string) |  | The lease id unique to the pop request, this must be used to complete, extend the lease or release the task. |
| payloadType | [string](#string) |  | A content hint for the tasks payload |
| payload | [google.protobuf.Struct](#google.protobuf.Struct) |  | The payload of the task |






<a name="nitric.queue.v1.QueueCompleteRequest"></a>

### QueueCompleteRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| queue | [string](#string) |  | The nitric name for the queue this will automatically be resolved to the provider specific queue identifier. |
| leaseId | [string](#string) |  | Lease id of the task to be completed |






<a name="nitric.queue.v1.QueueCompleteResponse"></a>

### QueueCompleteResponse







<a name="nitric.queue.v1.QueueReceiveRequest"></a>

### QueueReceiveRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| queue | [string](#string) |  | The nitric name for the queue this will automatically be resolved to the provider specific queue identifier. |
| depth | [int32](#int32) |  | The max number of items to pop off the queue, may be capped by provider specific limitations |






<a name="nitric.queue.v1.QueueReceiveResponse"></a>

### QueueReceiveResponse



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| tasks | [NitricTask](#nitric.queue.v1.NitricTask) | repeated | Array of tasks popped off the queue |






<a name="nitric.queue.v1.QueueSendBatchRequest"></a>

### QueueSendBatchRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| queue | [string](#string) |  | The Nitric name for the queue this will automatically be resolved to the provider specific queue identifier. |
| tasks | [NitricTask](#nitric.queue.v1.NitricTask) | repeated | Array of tasks to push to the queue |






<a name="nitric.queue.v1.QueueSendBatchResponse"></a>

### QueueSendBatchResponse
Response for sending a collection of tasks


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| failedTasks | [FailedTask](#nitric.queue.v1.FailedTask) | repeated | A list of tasks that failed to be queued |






<a name="nitric.queue.v1.QueueSendRequest"></a>

### QueueSendRequest
Request to push a single event to a queue


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| queue | [string](#string) |  | The Nitric name for the queue this will automatically be resolved to the provider specific queue identifier. |
| task | [NitricTask](#nitric.queue.v1.NitricTask) |  | The task to push to the queue |






<a name="nitric.queue.v1.QueueSendResponse"></a>

### QueueSendResponse
Result of pushing a single task to a queue





 

 

 


<a name="nitric.queue.v1.Queue"></a>

### Queue
The Nitric Queue Service contract

| Method Name | Request Type | Response Type | Description |
| ----------- | ------------ | ------------- | ------------|
| Send | [QueueSendRequest](#nitric.queue.v1.QueueSendRequest) | [QueueSendResponse](#nitric.queue.v1.QueueSendResponse) | Send a single event to a queue |
| SendBatch | [QueueSendBatchRequest](#nitric.queue.v1.QueueSendBatchRequest) | [QueueSendBatchResponse](#nitric.queue.v1.QueueSendBatchResponse) | Send multiple events to a queue |
| Receive | [QueueReceiveRequest](#nitric.queue.v1.QueueReceiveRequest) | [QueueReceiveResponse](#nitric.queue.v1.QueueReceiveResponse) | Receive event(s) off a queue |
| Complete | [QueueCompleteRequest](#nitric.queue.v1.QueueCompleteRequest) | [QueueCompleteResponse](#nitric.queue.v1.QueueCompleteResponse) | Complete an event previously popped from a queue |

 



<a name="storage/v1/storage.proto"></a>
<p align="right"><a href="#top">Top</a></p>

## storage/v1/storage.proto



<a name="nitric.storage.v1.StorageDeleteRequest"></a>

### StorageDeleteRequest
Request to delete a storage item


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| bucketName | [string](#string) |  | Name of the bucket to delete from |
| key | [string](#string) |  | Key of item to delete |






<a name="nitric.storage.v1.StorageDeleteResponse"></a>

### StorageDeleteResponse
Result of deleting a storage item






<a name="nitric.storage.v1.StorageReadRequest"></a>

### StorageReadRequest
Request to retrieve a storage item


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| bucketName | [string](#string) |  | Nitric name of the bucket to retrieve from this will be automatically resolved to the provider specific bucket identifier. |
| key | [string](#string) |  | Key of item to retrieve |






<a name="nitric.storage.v1.StorageReadResponse"></a>

### StorageReadResponse
Returned storage item


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| body | [bytes](#bytes) |  | The body bytes of the retrieved storage item |






<a name="nitric.storage.v1.StorageWriteRequest"></a>

### StorageWriteRequest
Request to put (create/update) a storage item


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| bucketName | [string](#string) |  | Nitric name of the bucket to store in this will be automatically resolved to the provider specific bucket identifier. |
| key | [string](#string) |  | Key to store the item under |
| body | [bytes](#bytes) |  | bytes array to store |






<a name="nitric.storage.v1.StorageWriteResponse"></a>

### StorageWriteResponse
Result of putting a storage item





 

 

 


<a name="nitric.storage.v1.Storage"></a>

### Storage
Services for storage and retrieval of files in the form of byte arrays, such as text and binary files.

| Method Name | Request Type | Response Type | Description |
| ----------- | ------------ | ------------- | ------------|
| Read | [StorageReadRequest](#nitric.storage.v1.StorageReadRequest) | [StorageReadResponse](#nitric.storage.v1.StorageReadResponse) | Retrieve an item from a bucket |
| Write | [StorageWriteRequest](#nitric.storage.v1.StorageWriteRequest) | [StorageWriteResponse](#nitric.storage.v1.StorageWriteResponse) | Store an item to a bucket |
| Delete | [StorageDeleteRequest](#nitric.storage.v1.StorageDeleteRequest) | [StorageDeleteResponse](#nitric.storage.v1.StorageDeleteResponse) | Delete an item from a bucket |

 



## Scalar Value Types

| .proto Type | Notes | C++ | Java | Python | Go | C# | PHP | Ruby |
| ----------- | ----- | --- | ---- | ------ | -- | -- | --- | ---- |
| <a name="double" /> double |  | double | double | float | float64 | double | float | Float |
| <a name="float" /> float |  | float | float | float | float32 | float | float | Float |
| <a name="int32" /> int32 | Uses variable-length encoding. Inefficient for encoding negative numbers – if your field is likely to have negative values, use sint32 instead. | int32 | int | int | int32 | int | integer | Bignum or Fixnum (as required) |
| <a name="int64" /> int64 | Uses variable-length encoding. Inefficient for encoding negative numbers – if your field is likely to have negative values, use sint64 instead. | int64 | long | int/long | int64 | long | integer/string | Bignum |
| <a name="uint32" /> uint32 | Uses variable-length encoding. | uint32 | int | int/long | uint32 | uint | integer | Bignum or Fixnum (as required) |
| <a name="uint64" /> uint64 | Uses variable-length encoding. | uint64 | long | int/long | uint64 | ulong | integer/string | Bignum or Fixnum (as required) |
| <a name="sint32" /> sint32 | Uses variable-length encoding. Signed int value. These more efficiently encode negative numbers than regular int32s. | int32 | int | int | int32 | int | integer | Bignum or Fixnum (as required) |
| <a name="sint64" /> sint64 | Uses variable-length encoding. Signed int value. These more efficiently encode negative numbers than regular int64s. | int64 | long | int/long | int64 | long | integer/string | Bignum |
| <a name="fixed32" /> fixed32 | Always four bytes. More efficient than uint32 if values are often greater than 2^28. | uint32 | int | int | uint32 | uint | integer | Bignum or Fixnum (as required) |
| <a name="fixed64" /> fixed64 | Always eight bytes. More efficient than uint64 if values are often greater than 2^56. | uint64 | long | int/long | uint64 | ulong | integer/string | Bignum |
| <a name="sfixed32" /> sfixed32 | Always four bytes. | int32 | int | int | int32 | int | integer | Bignum or Fixnum (as required) |
| <a name="sfixed64" /> sfixed64 | Always eight bytes. | int64 | long | int/long | int64 | long | integer/string | Bignum |
| <a name="bool" /> bool |  | bool | boolean | boolean | bool | bool | boolean | TrueClass/FalseClass |
| <a name="string" /> string | A string must always contain UTF-8 encoded or 7-bit ASCII text. | string | String | str/unicode | string | string | string | String (UTF-8) |
| <a name="bytes" /> bytes | May contain any arbitrary sequence of bytes. | string | ByteString | str | []byte | ByteString | string | String (ASCII-8BIT) |

