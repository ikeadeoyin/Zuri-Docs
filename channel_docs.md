# Zuri Chat Core API (Chat Channel Plugin) (v1)

# Authentication

### Authentication:
Method : Basic Authentication
- Username: string
- Password: pa$$word

Note that this authorization method will be used for every request in this collection. You can override this by specifying one in the request.

### BASE URL:
```sh
channels.zuri.chat
```

# Collections
<details>
  <summary> GET /v1/collections/{plugin_id}</summary>

 </details>

 This endpoint allows you get collections.

 Request Type: `GET`
<br>
Endpoint: `{baseUrl}/v1/collections/{plugin_id}`

## Path Parameters

Params| Description | Required
---------|----------|---------
 plugin_id | string | yes

## Request Headers
    
Content-Type: `application/json`
    
Authorization: `Basic Auth credentials`

## Sample Response

### **200** Success <br>

```
RESPONSE SCHEMA: application/json

code required      integer <int32> 
message required   string 
data required      object
```

```sh
{
    "status": "200",
    "message": "success"
}
```

### **404** Not Found <br>

```sh
{
    "status": "404",
    "message": "plugin not found"
}
```





# Get Collection by Organization

<details>
  <summary> GET /v1/collections/{plugin_id}/organizations{org_id}</summary>

 </details>

 This endpoint allows you to get collection by organization

Request Type: `GET`
<br>
Endpoint: `{baseUrl}/v1/collections/{plugin_id}/organizations{org_id}`

## Path Parameters

Params| Description | Required
---------|----------|---------
 plugin_id | string | yes
 org_id| string | yes

## Request Headers
    
Content-Type: `application/json`
    
Authorization: `Basic Auth credentials`

## Sample Response

### **200** Success <br>

```
RESPONSE SCHEMA: application/json

code required      integer <int32> 
message required   string 
data required      object
```

```sh
{
    "status": "200",
    "message": "success"
}
```

### **404** Not Found <br>

```sh
{
    "status": "404",
    "message": "not found"
}
```

# Read Details

<details>
  <summary> GET /v1/details/ </summary>

 </details>

This endpoint allows you to get details.

Request Type: `GET`
<br>
Endpoint: `{baseUrl}/v1/details`

## Sample Response

### **200** Success <br>

```
RESPONSE SCHEMA: application/json

code required      integer <int32> 
message required   string 
data required      object
```
```sh

{ 
"message": "Welcome, to the Channels Plugin",
"last_visted": "2021-09-17T14:47:46.401787+00:00",
"no_of_times_visted": "33"
}
```

### **404** Not Found <br>

```sh
{
    "status": "404",
    "message": "not found"
}
```


# Read Info

<details>
  <summary> GET /v1/info/ </summary>

 </details>

This endpoint allows you to get info.

Request Type: `GET`
<br>
Endpoint: `{baseUrl}/v1/info`

## Sample Response

### **200** Success <br>

```
RESPONSE SCHEMA: application/json

code required      integer <int32> 
message required   string 
data required      object
```
```sh

{
  "message": "Plugin Information Retrieved",
  "data": {
    "type": "Plugin Information",
    "plugin_info": {
      "name": "Channels Plugin",
      "description": [
        "Zuri.chat plugin",
        "The Channel Plugin is a feature    that helps users create spaces for    conversation and communication on zuri.chat."
      ]
    },
    "scaffold_structure": "Monolith",
    "team": "HNG 8.0/Team Coelho",
    "sidebar_url": "https://channels.zuri.chat/api/v1/sidebar/",
    "ping_url": "https://channels.zuri.chat/api/v1/ping/",
    "homepage_url": "https://channels.zuri.chat/"
  },
  "success": true
}

```

### **404** Not Found <br>

```sh
{
    "status": "404",
    "message": "not found"
}
```



# Read Sidebar

<details>
  <summary> GET /v1/sidebar/ </summary>

 </details>

This endpoint allows you to get the sidebar.

Request Type: `GET`
<br>
Endpoint: `{baseUrl}/v1/sidebar`

## Sample Response

### **200** Success <br>

```
RESPONSE SCHEMA: application/json

code required      integer <int32> 
message required   string 
data required      object
```
```sh

{ 
"name": "Channels Plugin",
  "description": "The Channel Plugin is a feature    that helps users create spaces for    conversation and communication on zuri.chat.",
  "plugin_id": "613654ede2358b02686503bb",
  "organisation_id": "buju",
  "user_id": "1",
  "group_name": "Zuri",
  "show_group": false,
  "joined_rooms": [],
  "public_rooms": []
}


```

### **404** Not Found <br>

```sh
{
    "status": "404",
    "message": "not found"
}
```


# Read ping

<details>
  <summary> GET /v1/ping/ </summary>

 </details>

This endpoint allows you to get ping.

Request Type: `GET`
<br>
Endpoint: `{baseUrl}/v1/ping`

## Sample Response

### **200** Success <br>

```
RESPONSE SCHEMA: application/json

code required      integer <int32> 
message required   string 
data required      object
```
```sh

{ 
"success": true
}
```

### **404** Not Found <br>

```sh
{
    "status": "404",
    "message": "not found"
}
```


# Read a Channel
<details>
  <summary> GET /v1/{org_id}/channels </summary>

 </details>

 This endpoint allows you to get all the channels for a particular organization
 Request Type: `GET`
<br>
Endpoint: `{baseUrl}/v1/{org_id}/channels`

## Path Parameters

Params| Description | Required
---------|----------|---------
 org_id | string | yes

 ## Request Headers
    
Content-Type: `application/json`
    
Authorization: `Basic Auth credentials`

## Sample Response

### **200** Success <br>

```
RESPONSE SCHEMA: application/json

code required      integer <int32> 
message required   string 
data required      object
```
```sh

{ 
"_id": "string",
"name": "string",
"description": "string",
"private": "boolean",
"owner": "string",
"archived": "boolean"
"users": "..."
}
```

### **404** Not Found <br>

```sh
{
    "status": "404",
    "message": "not found"
}
```


# Create a Channel

<details>
  <summary> POST /v1/{org_id}/channels/</summary>

 </details>

 This endpoint allows you to create a channel for an organization

Request Type: `POST`
<br>
Endpoint: `{baseUrl}/v1/{org_id}/channels/`

## Path Parameters

Params| Description | Required
---------|----------|---------
 org_id | string | yes

## Request Headers
    
Content-Type: `application/json`
    
Authorization: `Basic Auth credentials`

## Sample request

How to create a channel

### Request Body Params

Params| Description | Required
---------|----------|---------
name | string | yes
owner| string | yes
description | string | -
private| boolean | -

Content-Type: `application/json`

```sh
{ 
"name" : "string",
"owner": "string",
"description": "string",
"private": "boolean"
}
```

## Sample Response

### **201** Success <br>

```
RESPONSE SCHEMA: application/json

code required      integer <int32> 
message required   string 
data required      object
```

```sh
{ 

"_id": "string",
"name": "string",
"description": "string",
"private" : "boolean",
"archived": "boolean"
}
```

### **404** Not Found <br>

```sh
{
    "message": "not found",
    "status": "404"
}
```

# Read one channel from an organization

<details>
  <summary> GET /v1​/{org_id}​/channels​/{channel_id}​/ </summary>

 </details>

This endpoint allows you to get a channel from an organization

Request Type: `GET`
<br>
Endpoint: `{baseUrl}/v1/{org_id}/channels/{channel_id}/members/{member_id}`

## Path Parameters

Params| Description | Required
---------|----------|---------
 org_id | string | yes
 channel_id| string | yes


## Request Headers
    
Content-Type: `application/json`
    
Authorization: `Basic Auth credentials`

## Sample Response

### **200** Success <br>

```
RESPONSE SCHEMA: application/json

code required      integer <int32> 
message required   string 
data required      object
```
```sh

{ 
"_id": "string",
"name": "string",
"description": "string",
"private": "boolean",
"owner": "string",
"archived": "boolean"
"users": "..."
}
```

### **404** Not Found <br>

```sh
{
    "message": "not found",
    "status": "404"
}
```

# Update a channel

<details>
  <summary> PUT /v1/{org_id}/channels/{channel_id}/ </summary>

 </details>

This endpoint allows you to update a channel

Request Type: `PUT`
<br>
Endpoint: `{baseUrl}/v1/{org_id}/channels/{channel_id}/`

## Path Parameters

Params| Description | Required
---------|----------|---------
 org_id | string | yes
 channel_id| string | yes

## Request Headers
    
Content-Type: `application/json`
    
Authorization: `Basic Auth credentials`

## Sample request

How to update a channel

### Request Body Params

Params| Description | Required
---------|----------|---------
name | string | -
description | string | -
private| boolean | -
archived | boolean | 

Content-Type: `application/json`

```sh
{ 
"name" : "string",
"description": "string",
"private": "boolean",
"archived": "boolean"
}
```

## Sample Response

### **200** Success <br>

```
RESPONSE SCHEMA: application/json

code required      integer <int32> 
message required   string 
data required      object
```
```sh

{ 
"_id": "string",
"name": "string",
"description": "string",
"private": "boolean",
"owner": "string",
"archived": "boolean"
"users": "..."
}
```

### **404** Not Found <br>

```sh
{
    "message": "not found",
    "status": "404"
}
```


# Delete a channel

<details>
  <summary> DELETE /v1/{org_id}/channels/{channel_id}/</summary>

 </details>

This endpoint allows you to delete a channel

Request Type: `GET`
<br>
Endpoint: `{baseUrl}/v1/{org_id}/channels/{channel_id}/`

## Path Parameters

Params| Description | Required
---------|----------|---------
 org_id | string | yes
 channel_id| string | yes


## Request Headers
    
Content-Type: `application/json`
    
Authorization: `Basic Auth credentials`

 
## Sample Response

### **204** Success <br>

```
RESPONSE SCHEMA: application/json

code required      integer <int32> 
message required   string 
data required      object
```

```sh
{
    "status": "204",
    "message": "channel deleted"
}
```

### **404** Not Found <br>

```sh
{
    "status": "404",
    "message": "member not found"
}
```






# Retrieve a Member's details in a Channel
<details>
  <summary> GET /v1/{org_id}/channels/{channel_id}/members/{member_id} </summary>

 </details>

This endpoint allows you to retrieve a member's details in a channel

Request Type: `GET`
<br>
Endpoint: `{baseUrl}/v1/{org_id}/channels/{channel_id}/members/{member_id}`

## Path Parameters

Params| Description | Required
---------|----------|---------
 org_id | string | yes
 channel_id| string | yes
 member_id | string | yes

## Request Headers
    
Content-Type: `application/json`
    
Authorization: `Basic Auth credentials`

## Sample request

How to retrive a member's detail in a channel

Content-Type: `application/json`

```sh
{ 
"org_id" : "",
"channel_id": "",
"member_id": ""
}
```

## Sample Response

### **200** Success <br>

```
RESPONSE SCHEMA: application/json

code required      integer <int32> 
message required   string 
data required      object
```

```sh
{ 

"_id": "string",
"name": "string",
"description": "string",
"private": "boolean",
"archived": "boolean"

}
```

### Response for an error:

Status Code: `404` -  Not Found

### **400** Not Found <br>

```sh
{
 "status": "404",
 "message": "there was an unexpected error",
}
```

# Update a member's detail in a channel

<details>
  <summary> PUT /v1/{org_id}/channels/{channel_id}/members/{member_id} </summary>

 </details>


This endpoint allows you to update a member's details in a channel

Request Type: `PUT`
<br>
Endpoint: `{baseUrl}/v1/{org_id}/channels/{channel_id}/members/{member_id}`

### Path Parameters

Params| Description | Required
---------|----------|---------
 org_id | string | yes
 channel_id| string | yes
 member_id | string | yes


## Request Headers
    
Content-Type: `application/json`
    
Authorization: `Basic Auth credentials`

## Sample request

How to update a member's detail in a channel

### Request Body Params

Params| Description | Required
---------|----------|---------
 _id | string | yes
 role_id| string | -
 is_admin | string | -


Content-Type: `application/json`

```sh
{ 
"_id" : "string",
"role_id": "string",
"is_admin": "string"
}
```

## Sample Response

### **200** Success <br>

```
RESPONSE SCHEMA: application/json

code required      integer <int32> 
message required   string 
data required      object
```

```sh
{ 

"_id": "string",
"role_id": "string",
"is_admin": "string"
}
```

### Error Response:

### **404** Not Found <br>

```sh
{
 "status": "404",
 "message": "there was an unexpected error",
}
```


# Delete a Member from a Channel

<details>
<summary> DELETE /v1/{org_id}/channels/{channel_id}/members/{member_id}] </summary>

</details>

This endpoint allows you to delete a member from a channel

Request Type: `DELETE`
<br>
Endpoint: `{baseUrl}/v1/{org_id}/channels/{channel_id}/members/{member_id}`


## Path Parameters

Params| Description | Required
---------|----------|---------
 org_id | string | yes
 channel_id| string | yes
 member_id | string | yes

## Request Headers
    
Content-Type: `application/json`
    
Authorization: `Basic Auth credentials`

 
## Sample Response

### **204** Success <br>

```
RESPONSE SCHEMA: application/json

code required      integer <int32> 
message required   string 
data required      object
```

```sh
{
    "status": "204",
    "message": "member removed from the channel"
}
```

### **404** Not Found <br>

```sh
{
    "status": "404",
    "message": "member not found"
}
```