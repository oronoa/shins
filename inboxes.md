---
title: Inboxes Developer API
language_tabs:
  - ruby: Ruby
  - python: Python
toc_footers:
  - '<a href="http://swagger.io">Find out more about Swagger</a>'
includes: []
search: false
highlight_theme: darkula
headingLevel: 2

---

<h1 id="inboxes-developer-api">Inboxes Developer API v1.0.0</h1>

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

This is a sample server Petstore server.  You can find out more about     Swagger at [http://swagger.io](http://swagger.io) or on [irc.freenode.net, #swagger](http://swagger.io/irc/).      For this sample, you can use the api key `special-key` to test the authorization     filters.

Base URLs:

* <a href="https://api.inboxes.com/v2">https://api.inboxes.com/v2</a>

* <a href="http://api.inboxes.com/v2">http://api.inboxes.com/v2</a>

<a href="http://inboces.com/terms/">Terms of service</a>
Email: <a href="mailto:info@inboxes.com">Support</a> 

# Authentication

* API Key (api_key)
    - Parameter Name: **api_key**, in: header. 

<h1 id="inboxes-developer-api-domain">domain</h1>

Everything about your Pets

## Add a new domain to be used by inboxes

<a id="opIdaddDomain"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'api_key' => 'API_KEY'
}

result = RestClient.post 'https://api.inboxes.com/v2/domain',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'api_key': 'API_KEY'
}

r = requests.post('https://api.inboxes.com/v2/domain', params={

}, headers = headers)

print r.json()

```

`POST /domain`

> Body parameter

```json
{
  "name": "mydomain.com"
}
```

<h3 id="add-a-new-domain-to-be-used-by-inboxes-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[DomainIn](#schemadomainin)|true|Domain object that you would like to add|

<h3 id="add-a-new-domain-to-be-used-by-inboxes-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|405|[Method Not Allowed](https://tools.ietf.org/html/rfc7231#section-6.5.5)|Invalid input|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
api_key
</aside>

<h1 id="inboxes-developer-api-pet">pet</h1>

## Update an existing pet

<a id="opIdupdatePet"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'api_key' => 'API_KEY'
}

result = RestClient.put 'https://api.inboxes.com/v2/domain',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'api_key': 'API_KEY'
}

r = requests.put('https://api.inboxes.com/v2/domain', params={

}, headers = headers)

print r.json()

```

`PUT /domain`

> Body parameter

```json
{
  "id": 0,
  "category": {
    "name": "mydomain.com"
  },
  "name": "doggie",
  "photoUrls": [
    "string"
  ],
  "tags": [
    {
      "id": 0,
      "name": "string"
    }
  ],
  "status": "available"
}
```

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<Pet>
  <id>0</id>
  <category>
    <name>mydomain.com</name>
  </category>
  <name>doggie</name>
  <photoUrls>string</photoUrls>
  <tags>
    <id>0</id>
    <name>string</name>
  </tags>
  <status>available</status>
</Pet>
```

<h3 id="update-an-existing-pet-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[Pet](#schemapet)|true|Pet object that needs to be added to the store|

<h3 id="update-an-existing-pet-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid ID supplied|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Pet not found|None|
|405|[Method Not Allowed](https://tools.ietf.org/html/rfc7231#section-6.5.5)|Validation exception|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
api_key
</aside>

## Finds Pets by status

<a id="opIdfindPetsByStatus"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/xml',
  'api_key' => 'API_KEY'
}

result = RestClient.get 'https://api.inboxes.com/v2/pet/findByStatus',
  params: {
  'status' => 'array[string]'
}, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/xml',
  'api_key': 'API_KEY'
}

r = requests.get('https://api.inboxes.com/v2/pet/findByStatus', params={
  'status': [
  "available"
]
}, headers = headers)

print r.json()

```

`GET /pet/findByStatus`

Multiple status values can be provided with comma separated strings

<h3 id="finds-pets-by-status-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|status|query|array[string]|true|Status values that need to be considered for filter|

#### Enumerated Values

|Parameter|Value|
|---|---|
|status|available|
|status|pending|
|status|sold|

> Example responses

> 200 Response

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<id>0</id>
<category>
  <name>mydomain.com</name>
</category>
<name>doggie</name>
<photoUrls>string</photoUrls>
<tags>
  <id>0</id>
  <name>string</name>
</tags>
<status>available</status>
```

```json
[
  {
    "id": 0,
    "category": {
      "name": "mydomain.com"
    },
    "name": "doggie",
    "photoUrls": [
      "string"
    ],
    "tags": [
      {
        "id": 0,
        "name": "string"
      }
    ],
    "status": "available"
  }
]
```

<h3 id="finds-pets-by-status-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid status value|None|

<h3 id="finds-pets-by-status-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[Pet](#schemapet)]|false|none|none|
|» id|integer(int64)|false|none|none|
|» category|[DomainIn](#schemadomainin)|false|none|none|
|»» name|string|false|none|name of the domain|
|» name|string|true|none|none|
|» photoUrls|[string]|true|none|none|
|» tags|[[Tag](#schematag)]|false|none|none|
|»» id|integer(int64)|false|none|none|
|»» name|string|false|none|none|
|» status|string|false|none|pet status in the store|

#### Enumerated Values

|Property|Value|
|---|---|
|status|available|
|status|pending|
|status|sold|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
api_key
</aside>

## Finds Pets by tags

<a id="opIdfindPetsByTags"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/xml',
  'api_key' => 'API_KEY'
}

result = RestClient.get 'https://api.inboxes.com/v2/pet/findByTags',
  params: {
  'tags' => 'array[string]'
}, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/xml',
  'api_key': 'API_KEY'
}

r = requests.get('https://api.inboxes.com/v2/pet/findByTags', params={
  'tags': [
  "string"
]
}, headers = headers)

print r.json()

```

`GET /pet/findByTags`

Muliple tags can be provided with comma separated strings. Use         tag1, tag2, tag3 for testing.

<h3 id="finds-pets-by-tags-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|tags|query|array[string]|true|Tags to filter by|

> Example responses

> 200 Response

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<id>0</id>
<category>
  <name>mydomain.com</name>
</category>
<name>doggie</name>
<photoUrls>string</photoUrls>
<tags>
  <id>0</id>
  <name>string</name>
</tags>
<status>available</status>
```

```json
[
  {
    "id": 0,
    "category": {
      "name": "mydomain.com"
    },
    "name": "doggie",
    "photoUrls": [
      "string"
    ],
    "tags": [
      {
        "id": 0,
        "name": "string"
      }
    ],
    "status": "available"
  }
]
```

<h3 id="finds-pets-by-tags-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid tag value|None|

<h3 id="finds-pets-by-tags-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[Pet](#schemapet)]|false|none|none|
|» id|integer(int64)|false|none|none|
|» category|[DomainIn](#schemadomainin)|false|none|none|
|»» name|string|false|none|name of the domain|
|» name|string|true|none|none|
|» photoUrls|[string]|true|none|none|
|» tags|[[Tag](#schematag)]|false|none|none|
|»» id|integer(int64)|false|none|none|
|»» name|string|false|none|none|
|» status|string|false|none|pet status in the store|

#### Enumerated Values

|Property|Value|
|---|---|
|status|available|
|status|pending|
|status|sold|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
api_key
</aside>

## Find pet by ID

<a id="opIdgetPetById"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/xml',
  'api_key' => 'API_KEY'
}

result = RestClient.get 'https://api.inboxes.com/v2/pet/{petId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/xml',
  'api_key': 'API_KEY'
}

r = requests.get('https://api.inboxes.com/v2/pet/{petId}', params={

}, headers = headers)

print r.json()

```

`GET /pet/{petId}`

Returns a single pet

<h3 id="find-pet-by-id-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|petId|path|integer(int64)|true|ID of pet to return|

> Example responses

> 200 Response

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<Pet>
  <id>0</id>
  <category>
    <name>mydomain.com</name>
  </category>
  <name>doggie</name>
  <photoUrls>string</photoUrls>
  <tags>
    <id>0</id>
    <name>string</name>
  </tags>
  <status>available</status>
</Pet>
```

```json
{
  "id": 0,
  "category": {
    "name": "mydomain.com"
  },
  "name": "doggie",
  "photoUrls": [
    "string"
  ],
  "tags": [
    {
      "id": 0,
      "name": "string"
    }
  ],
  "status": "available"
}
```

<h3 id="find-pet-by-id-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[Pet](#schemapet)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid ID supplied|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Pet not found|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
api_key
</aside>

## Updates a pet in the store with form data

<a id="opIdupdatePetWithForm"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/x-www-form-urlencoded',
  'api_key' => 'API_KEY'
}

result = RestClient.post 'https://api.inboxes.com/v2/pet/{petId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/x-www-form-urlencoded',
  'api_key': 'API_KEY'
}

r = requests.post('https://api.inboxes.com/v2/pet/{petId}', params={

}, headers = headers)

print r.json()

```

`POST /pet/{petId}`

> Body parameter

```yaml
name: string
status: string

```

<h3 id="updates-a-pet-in-the-store-with-form-data-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|petId|path|integer(int64)|true|ID of pet that needs to be updated|
|body|body|object|false|none|
|» name|body|string|false|Updated name of the pet|
|» status|body|string|false|Updated status of the pet|

<h3 id="updates-a-pet-in-the-store-with-form-data-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|405|[Method Not Allowed](https://tools.ietf.org/html/rfc7231#section-6.5.5)|Invalid input|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
api_key
</aside>

## Deletes a pet

<a id="opIddeletePet"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'api_key' => 'string',
  'api_key' => 'API_KEY'
}

result = RestClient.delete 'https://api.inboxes.com/v2/pet/{petId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'api_key': 'string',
  'api_key': 'API_KEY'
}

r = requests.delete('https://api.inboxes.com/v2/pet/{petId}', params={

}, headers = headers)

print r.json()

```

`DELETE /pet/{petId}`

<h3 id="deletes-a-pet-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|api_key|header|string|false|none|
|petId|path|integer(int64)|true|Pet id to delete|

<h3 id="deletes-a-pet-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid ID supplied|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Pet not found|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
api_key
</aside>

## uploads an image

<a id="opIduploadFile"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'multipart/form-data',
  'Accept' => 'application/json',
  'api_key' => 'API_KEY'
}

result = RestClient.post 'https://api.inboxes.com/v2/pet/{petId}/uploadImage',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'multipart/form-data',
  'Accept': 'application/json',
  'api_key': 'API_KEY'
}

r = requests.post('https://api.inboxes.com/v2/pet/{petId}/uploadImage', params={

}, headers = headers)

print r.json()

```

`POST /pet/{petId}/uploadImage`

> Body parameter

```yaml
additionalMetadata: string
file: string

```

<h3 id="uploads-an-image-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|petId|path|integer(int64)|true|ID of pet to update|
|body|body|object|false|none|
|» additionalMetadata|body|string|false|Additional data to pass to server|
|» file|body|string(binary)|false|file to upload|

> Example responses

> 200 Response

```json
{
  "code": 0,
  "type": "string",
  "message": "string"
}
```

<h3 id="uploads-an-image-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[ApiResponse](#schemaapiresponse)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
api_key
</aside>

<h1 id="inboxes-developer-api-store">store</h1>

## Returns pet inventories by status

<a id="opIdgetInventory"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'api_key' => 'API_KEY'
}

result = RestClient.get 'https://api.inboxes.com/v2/store/inventory',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'api_key': 'API_KEY'
}

r = requests.get('https://api.inboxes.com/v2/store/inventory', params={

}, headers = headers)

print r.json()

```

`GET /store/inventory`

Returns a map of status codes to quantities

> Example responses

> 200 Response

```json
{
  "property1": 0,
  "property2": 0
}
```

<h3 id="returns-pet-inventories-by-status-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|Inline|

<h3 id="returns-pet-inventories-by-status-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» **additionalProperties**|integer(int32)|false|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
api_key
</aside>

## Place an order for a pet

<a id="opIdplaceOrder"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/xml'
}

result = RestClient.post 'https://api.inboxes.com/v2/store/order',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/xml'
}

r = requests.post('https://api.inboxes.com/v2/store/order', params={

}, headers = headers)

print r.json()

```

`POST /store/order`

> Body parameter

```json
{
  "id": "string",
  "name": "string",
  "validate": "string",
  "status": "missing validation",
  "active": false
}
```

<h3 id="place-an-order-for-a-pet-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[Domain](#schemadomain)|true|order placed for purchasing the pet|

> Example responses

> 200 Response

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<Domain>
  <id>string</id>
  <name>string</name>
  <validate>string</validate>
  <status>missing validation</status>
  <active>false</active>
</Domain>
```

```json
{
  "id": "string",
  "name": "string",
  "validate": "string",
  "status": "missing validation",
  "active": false
}
```

<h3 id="place-an-order-for-a-pet-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[Domain](#schemadomain)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid Order|None|

<aside class="success">
This operation does not require authentication
</aside>

## Find purchase order by ID

<a id="opIdgetOrderById"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/xml'
}

result = RestClient.get 'https://api.inboxes.com/v2/store/order/{orderId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/xml'
}

r = requests.get('https://api.inboxes.com/v2/store/order/{orderId}', params={

}, headers = headers)

print r.json()

```

`GET /store/order/{orderId}`

For valid response try integer IDs with value >= 1 and <= 10.         Other values will generated exceptions

<h3 id="find-purchase-order-by-id-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|orderId|path|integer(int64)|true|ID of pet that needs to be fetched|

> Example responses

> 200 Response

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<DomainIn>
  <name>mydomain.com</name>
</DomainIn>
```

```json
{
  "name": "mydomain.com"
}
```

<h3 id="find-purchase-order-by-id-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[DomainIn](#schemadomainin)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid ID supplied|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Order not found|None|

<aside class="success">
This operation does not require authentication
</aside>

## Delete purchase order by ID

<a id="opIddeleteOrder"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

result = RestClient.delete 'https://api.inboxes.com/v2/store/order/{orderId}',
  params: {
  }

p JSON.parse(result)

```

```python
import requests

r = requests.delete('https://api.inboxes.com/v2/store/order/{orderId}', params={

)

print r.json()

```

`DELETE /store/order/{orderId}`

For valid response try integer IDs with positive integer value.         Negative or non-integer values will generate API errors

<h3 id="delete-purchase-order-by-id-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|orderId|path|integer(int64)|true|ID of the order that needs to be deleted|

<h3 id="delete-purchase-order-by-id-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid ID supplied|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Order not found|None|

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="inboxes-developer-api-user">user</h1>

## Create user

<a id="opIdcreateUser"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json'
}

result = RestClient.post 'https://api.inboxes.com/v2/user',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json'
}

r = requests.post('https://api.inboxes.com/v2/user', params={

}, headers = headers)

print r.json()

```

`POST /user`

This can only be done by the logged in user.

> Body parameter

```json
{
  "id": 0,
  "username": "string",
  "firstName": "string",
  "lastName": "string",
  "email": "string",
  "password": "string",
  "phone": "string",
  "userStatus": 0
}
```

<h3 id="create-user-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[User](#schemauser)|true|Created user object|

<h3 id="create-user-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|default|Default|successful operation|None|

<aside class="success">
This operation does not require authentication
</aside>

## Creates list of users with given input array

<a id="opIdcreateUsersWithListInput"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json'
}

result = RestClient.post 'https://api.inboxes.com/v2/user/createWithList',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json'
}

r = requests.post('https://api.inboxes.com/v2/user/createWithList', params={

}, headers = headers)

print r.json()

```

`POST /user/createWithList`

> Body parameter

```json
[
  {
    "id": 0,
    "username": "string",
    "firstName": "string",
    "lastName": "string",
    "email": "string",
    "password": "string",
    "phone": "string",
    "userStatus": 0
  }
]
```

<h3 id="creates-list-of-users-with-given-input-array-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[UserArray](#schemauserarray)|true|List of user object|

<h3 id="creates-list-of-users-with-given-input-array-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|default|Default|successful operation|None|

<aside class="success">
This operation does not require authentication
</aside>

## Logs user into the system

<a id="opIdloginUser"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/xml'
}

result = RestClient.get 'https://api.inboxes.com/v2/user/login',
  params: {
  'username' => 'string',
'password' => 'string'
}, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/xml'
}

r = requests.get('https://api.inboxes.com/v2/user/login', params={
  'username': 'string',  'password': 'string'
}, headers = headers)

print r.json()

```

`GET /user/login`

<h3 id="logs-user-into-the-system-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|username|query|string|true|The user name for login|
|password|query|string|true|The password for login in clear text|

> Example responses

> 200 Response

```json
"string"
```

<h3 id="logs-user-into-the-system-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|string|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid username/password supplied|None|

### Response Headers

|Status|Header|Type|Format|Description|
|---|---|---|---|---|
|200|X-Rate-Limit|integer|int32|calls per hour allowed by the user|
|200|X-Expires-After|string|date-time|date in UTC when token expires|

<aside class="success">
This operation does not require authentication
</aside>

## Logs out current logged in user session

<a id="opIdlogoutUser"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

result = RestClient.get 'https://api.inboxes.com/v2/user/logout',
  params: {
  }

p JSON.parse(result)

```

```python
import requests

r = requests.get('https://api.inboxes.com/v2/user/logout', params={

)

print r.json()

```

`GET /user/logout`

<h3 id="logs-out-current-logged-in-user-session-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|default|Default|successful operation|None|

<aside class="success">
This operation does not require authentication
</aside>

## Get user by user name

<a id="opIdgetUserByName"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/xml'
}

result = RestClient.get 'https://api.inboxes.com/v2/user/{username}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/xml'
}

r = requests.get('https://api.inboxes.com/v2/user/{username}', params={

}, headers = headers)

print r.json()

```

`GET /user/{username}`

<h3 id="get-user-by-user-name-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|username|path|string|true|The name that needs to be fetched. Use user1 for testing. |

> Example responses

> 200 Response

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<User>
  <id>0</id>
  <username>string</username>
  <firstName>string</firstName>
  <lastName>string</lastName>
  <email>string</email>
  <password>string</password>
  <phone>string</phone>
  <userStatus>0</userStatus>
</User>
```

```json
{
  "id": 0,
  "username": "string",
  "firstName": "string",
  "lastName": "string",
  "email": "string",
  "password": "string",
  "phone": "string",
  "userStatus": 0
}
```

<h3 id="get-user-by-user-name-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[User](#schemauser)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid username supplied|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|User not found|None|

<aside class="success">
This operation does not require authentication
</aside>

## Updated user

<a id="opIdupdateUser"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json'
}

result = RestClient.put 'https://api.inboxes.com/v2/user/{username}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json'
}

r = requests.put('https://api.inboxes.com/v2/user/{username}', params={

}, headers = headers)

print r.json()

```

`PUT /user/{username}`

This can only be done by the logged in user.

> Body parameter

```json
{
  "id": 0,
  "username": "string",
  "firstName": "string",
  "lastName": "string",
  "email": "string",
  "password": "string",
  "phone": "string",
  "userStatus": 0
}
```

<h3 id="updated-user-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|username|path|string|true|name that need to be updated|
|body|body|[User](#schemauser)|true|Updated user object|

<h3 id="updated-user-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid user supplied|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|User not found|None|

<aside class="success">
This operation does not require authentication
</aside>

## Delete user

<a id="opIddeleteUser"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

result = RestClient.delete 'https://api.inboxes.com/v2/user/{username}',
  params: {
  }

p JSON.parse(result)

```

```python
import requests

r = requests.delete('https://api.inboxes.com/v2/user/{username}', params={

)

print r.json()

```

`DELETE /user/{username}`

This can only be done by the logged in user.

<h3 id="delete-user-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|username|path|string|true|The name that needs to be deleted|

<h3 id="delete-user-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid username supplied|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|User not found|None|

<aside class="success">
This operation does not require authentication
</aside>

# Schemas

<h2 id="tocSdomain">Domain</h2>

<a id="schemadomain"></a>

```json
{
  "id": "string",
  "name": "string",
  "validate": "string",
  "status": "missing validation",
  "active": false
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|false|none|none|
|name|string|false|none|name of the domain|
|validate|string|false|none|DNS TXT record to add to validate ownership|
|status|string|false|none|Domain Status|
|active|boolean|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|status|missing validation|
|status|validated|

<h2 id="tocSdomainin">DomainIn</h2>

<a id="schemadomainin"></a>

```json
{
  "name": "mydomain.com"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|name|string|false|none|name of the domain|

<h2 id="tocSinbox">Inbox</h2>

<a id="schemainbox"></a>

```json
{
  "id": "string",
  "name": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|false|none|Unique ID for this inbox|
|name|string|false|none|user @ domain i.e me@theinboxes.com|

<h2 id="tocSuser">User</h2>

<a id="schemauser"></a>

```json
{
  "id": 0,
  "username": "string",
  "firstName": "string",
  "lastName": "string",
  "email": "string",
  "password": "string",
  "phone": "string",
  "userStatus": 0
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer(int64)|false|none|none|
|username|string|false|none|none|
|firstName|string|false|none|none|
|lastName|string|false|none|none|
|email|string|false|none|none|
|password|string|false|none|none|
|phone|string|false|none|none|
|userStatus|integer(int32)|false|none|User Status|

<h2 id="tocStag">Tag</h2>

<a id="schematag"></a>

```json
{
  "id": 0,
  "name": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer(int64)|false|none|none|
|name|string|false|none|none|

<h2 id="tocSpet">Pet</h2>

<a id="schemapet"></a>

```json
{
  "id": 0,
  "category": {
    "name": "mydomain.com"
  },
  "name": "doggie",
  "photoUrls": [
    "string"
  ],
  "tags": [
    {
      "id": 0,
      "name": "string"
    }
  ],
  "status": "available"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer(int64)|false|none|none|
|category|[DomainIn](#schemadomainin)|false|none|none|
|name|string|true|none|none|
|photoUrls|[string]|true|none|none|
|tags|[[Tag](#schematag)]|false|none|none|
|status|string|false|none|pet status in the store|

#### Enumerated Values

|Property|Value|
|---|---|
|status|available|
|status|pending|
|status|sold|

<h2 id="tocSapiresponse">ApiResponse</h2>

<a id="schemaapiresponse"></a>

```json
{
  "code": 0,
  "type": "string",
  "message": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|code|integer(int32)|false|none|none|
|type|string|false|none|none|
|message|string|false|none|none|

