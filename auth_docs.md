# Zuri Chat Core API (Authentication Endpoints) (v1)

Zuri Chat is an open source slack clone.
The Authentication API enables you to manage all aspects of user identity. It offers endpoints so your users can log in, log out, access APIs, and more.

# Account - Reset password

This endpoint allows you request a code to reset your password

Request Type: `POST`

Endpoint: `/account/request-password-reset-code`


## Request Headers
    
Content-Type: `application/json`
    
Authorization: `Basic Auth credentials`

## Request Body Params
Params| Description | Required
---------|----------|---------
 email | string | yes

## Sample Request

```sh
{
  "email": "user@example.com"
}
```

## Sample Response

### **200** Success 


```
RESPONSE SCHEMA: application/json

code required      integer <int32>
message required   string 
data required      object
```

```sh
{
  "code": 200,
  "data": null,
  "message": "string"
}
```

### **404** Bad Request 

```sh
{
  "status": 400,
  "message": "Key: 'Email' Error:Field validation for 'Email' failed on the 'email' tag"
}
```

# Account - Verify User Acount

This endpoint allows you verify a user's account

Request Type: `POST`

Endpoint: `/account/verify-account`

## Request Headers
    
Content-Type: `application/json`
    
Authorization: `Basic Auth credentials`

## Request Body Params
Params| Description | Required
---------|----------|---------
 email | string | yes
password | string | yes

## Sample request

```sh
{
  "email": "user@example.com",
  "password": "string"
}
```

## Sample Response

### **200** Success 

```
RESPONSE SCHEMA: application/json

code required      integer <int32>
message required   string 
data required      object
```

```sh
{
  "code": 200,
  "message": "Password confirm successful"
}

```

### **404** Bad Request 

```sh
{
  "status": 400,
  "message": ""
}
```

# Confirm User Password

This endpoint allows you confirm a user's password

Request Type: `POST`

Endpoint: `/auth​/confirm-password`

## Request Headers
    
Content-Type: `application/json`
    
Authorization: `cookieAuth` or `bearerAuth`

## Request Body Params
Params| Description | Required
---------|----------|---------
 confirm_password | string | yes
password | string | yes

## Sample Request
```sh
{
  "confirm_password": "string",
  "password": "string"
}
```
## Sample Response

### **200** Success 

```
RESPONSE SCHEMA: application/json

code required      integer <int32>
message required   string 
data required      object
```

```sh
{
  "code": 200,
  "data": null,
  "message": "password confirm successful"
}

```

### **404** Bad Request 

```sh
{
  "status": 400,
  "message": ""
}
```


# Login

This endpoint is used to sign a user into the application.

Endpoint :`/auth/login`

Request Type :` POST`

Content-Type: `application/json`

## Request Body Params

Params| Description | Required
---------|----------|---------
email | string | yes
password | string | yes

##  Sample Request
```sh
{
  "email": "user@example.com",
  "password": "string"
}
```
## Sample Response

### **200** Success 

```
RESPONSE SCHEMA: application/json

code required      integer <int32>
message required   string 
data required      object
```

```sh
{
  "code": 200,
  "data": {
    "session_id": "string",
    "user": {
      "created_at": "2021-09-06 03:54:37.387816",
      "display_name": "samsoft",
      "email": "hng.user01@gmail.com",
      "first_name": "Johnson",
      "id": "613590fd0366b6816a0b75ee",
      "last_name": "Ajayi",
      "phone": "09067324567",
      "status": 0,
      "time_zone": "string",
      "token": "l6TVRneU9ESTBNSHhIZDNkQlIwUlplRTVFVFhwYWFsVXlXa1JCZVU5RVVtbFplbHBvVDFSSmVVMTZUbXBPVVQwOWZFQWpod01iU0E2d1FOUkczQlcwaUZDbHVqUnVOVXFFTHk4QUdGMGhMdkgzIiwiZW1haWwiOiJqYjEyQGdtYWlsLmNvbSIsImlkIjoiNjE0MzNmNTZkMDI4NGJjNmE5MjIzM2M1Iiwib3B0aW9ucyI6ey",
      "update_at": "0001-01-01 00:00:00"
    }
  },
  "message": "string"
}

```

### **404** Bad Request 

```sh
{
  "status": 400,
  "message": "string"
}
```



# Logout

This endpoint logs a user out from the application

Endpoint :`/auth/logout`

Request Type :` POST` or `GET`

Content-Type: `application/json`

## Sample Response

### **200** Success 

```
RESPONSE SCHEMA: application/json

code required      integer <int32>
message required   string 
data required      object
```

```sh
{
    "code": 200,
    "message": "Logged out successfully"
}
```

### **401** Unauthorized access

```sh
{
  "status": 401,
  "message": "string"
}
```



# Logout user from all sessions

This endpoint logouts a user from all sessions

Request Type: `POST` 

Endpoint: `/auth/logout/othersessions`



## Request Body Params

Params| Description | Required
---------|----------|---------
email | string | yes


##  Sample Request
```sh
{
  "email": "user@example.com"
}
```

## Sample Response

### **200** Success 

```
RESPONSE SCHEMA: application/json

code required      integer <int32>
message required   string 
data required      object
```

```sh

{
  "code": 200,
  "message": "Logged out successfully"
}
```

### **401** Unauthorized error

```sh
{
    "status": "401",
    "message" : "unauthorized error"
}
```

# Reset User  Password

This endpoint  resets a user password.

Request Type: `POST` 

Endpoint: `/auth/request-reset-password`

## Request Headers
    
Content-Type: `application/json`
    
Authorization: `cookieAuth` or `bearerAuth`

## Request Body Params

Params| Description | Required
---------|----------|---------
email | string | yes

##  Sample Request
```sh
{
  "email": "user@example.com"
}
```

## Sample Response

### **200** Success 

```
RESPONSE SCHEMA: application/json

code required      integer <int32>
message required   string 
data required      object
```

```sh

{
  "code": 200,
  "message": ""
}
```

### **404** Not found

```sh
{
    "status": "401",
    "message" : ""
}
```

# Validate User before access is granted

This endpoint verifies a user before access is granted

Request Type: `GET`

Endpoint: `/auth/verify-token`

## Request Headers
    
Content-Type: `application/json`
    
Authorization: `cookieAuth` or `bearerAuth`


## Sample Response

### **200** Success 

```
RESPONSE SCHEMA: application/json

code required      integer <int32>
message required   string 
data required      object
```

```sh
{
  "code": 200,
  "data": {
    "is_verified": true,
    "user": {
      "created_at": "2021-09-06 03:54:37.387816",
      "display_name": "samsoft",
      "email": "hng.user01@gmail.com",
      "first_name": "Johnson",
      "id": "613590fd0366b6816a0b75ee",
      "last_name": "Ajayi",
      "phone": "09067324567",
      "status": 0,
      "time_zone": "string",
      "update_at": "0001-01-01 00:00:00"
    }
  },
  "message": "string"
}
```

### **500** Internal Server Error

```sh

{
  "code": 500,
  "message": "string"
}
```


