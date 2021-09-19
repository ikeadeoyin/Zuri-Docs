# Zuri Chat Core API (Chat Channel Plugin) (v1)

# Authentication

### Authentication:
Method : Basic Authentication
- Username: string
- Password: pa$$word

Note that this authorization method will be used for every request in this collection. You can override this by specifying one in the request.
#### Base Url:
```sh
[ **Base URL**: channels.zuri.chat/api ]
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
