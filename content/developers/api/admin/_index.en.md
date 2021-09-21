---
title: "Admin"
weight: 1
draft: false
# search related keywords
keywords: ["API","admin"]
---

{{< notice info >}}
  **This page is under construction** <br>
  We're working on it!
{{</ notice >}}

# Table of Content
1. [User Management](#user_management)
2. [Institution Management](#institution_management)
3. [Instrument Management](#instrument_management)
4. [UI Management](#ui_management)


*****
*****


# 1. User Management <a name="user_management"></a> 
- [List Users](#admin_user_list)
- [Create User](#admin_user_create)
- [Read User](#admin_user_read)
- [Update User](#admin_user_update)
- [Update User Partial Information](#admin_user_partial_update)
- [Delete User](#admin_user_delete)


<!--- admin_user_list --->
## List Users: GET <a name="admin_user_list"></a>

API endpoint that allows users to be viewed or edited.

### Request

Concept | Data
-- | --
HTTP Method | GET
Path | /api/v2/admin/user/
Authorization | JWT
Content Type | application/json

### Parameters

Name | Type | Comments | Request | Response
---- | ---- | ---- | --- | ---
search | string | A search term. | ✔️ | 
username | string | - | ✔️ | 
first_name | string | - | ✔️ | 
last_name | string  | - | ✔️ | 
email | string  | - | ✔️ | 
institution | string | - | ✔️ | 
roles | string | - | ✔️ | 
ordering | string | Which field to use when ordering the results. | ✔️ | 
limit | integer | Number of results to return per page. | ✔️ | 
offset | integer | The initial index from which to return the results. | ✔️ |
**count** <br>`required`  | integer |  | | ✔️ | 
next  | string \<uri\> <br>Nullable | | | ✔️ | 
previous  | string \<uri\> <br>Nullable | | | ✔️ | 
results <br>`required`  | Array of Objects (User) |  | | ✔️ | 

### Responses

#### Response sample
<!--- details and summary tags, both, needed for expandable code --->
<details>
  <summary>200</summary>

  ````json
  {
    "count": 0,
    "next": "http://example.com",
    "previous": "http://example.com",
    "results": [
      {
        "id": 0,
        "username": "string",
        "last_login": "2019-08-24T14:15:22Z",
        "first_name": "string",
        "last_name": "string",
        "email": "user@example.com",
        "password": "string",
        "password2": "string",
        "institution": "string",
        "roles": "string",
        "institution_id": 0,
        "inst_admin": false,
        "login_allowed": true,
        "uid": "string",
        "is_superuser": true,
        "is_staff": true,
        "is_active": true,
        "date_joined": "2019-08-24T14:15:22Z",
        "groups": [
          0
        ],
        "user_permissions": [
          0
        ]
      }
    ]
  }
  ````
</details>

<!--- admin_user_create --->
## Create User: POST <a name="admin_user_create"></a>

API endpoint that creates a new user. This endpoint is only available to admin users with the right admin permissions.

### Request
Concept | Data
-- | --
HTTP Method | POST
Path | /api/v2/admin/user/
Authorization | JWT
Content Type | application/json

#### Request Sample: POST

```json
{
  "username": "string",
  "first_name": "string",
  "last_name": "string",
  "email": "user@example.com",
  "password": "string",
  "password2": "string",
  "institution_id": 0,
  "inst_admin": false,
  "login_allowed": true,
  "uid": "string",
  "is_superuser": true,
  "is_staff": true,
  "is_active": true,
  "date_joined": "2019-08-24T14:15:22Z",
  "groups": [
    0
  ],
  "user_permissions": [
    0
  ]
}
````

###  Parameters:

<!--- check why emoji are not working. Instead of images we should use :white_check_mark: or :heavy_check_mark: --->

Name | Type | Comments | Request | Response
--- | --- | --- | --- | ---
id | integer (ID) | - | | ✔️
**username** <br>_`required`_ | string (Username) <br>non-empty |  |  ✔️ | ✔️
last_login | string \<date-time\>(Last login) | - |  | ✔️
first_name | string (First name) <br>non-empty |  | ✔️ | ✔️
last_name | string (Last name) <br>non-empty|  | ✔️ | ✔️
email | string \<email\> (Email)<br>non-empty | | ✔️ | ✔️
password | string (Password) <br>non-empty<br>Nullable | | ✔️ | ✔️
password2 | string (Password2) <br>non-empty<br>Nullable | | ✔️ | ✔️
institution | string (Institution) | - |  | ✔️
roles | string (Roles) | - |  | ✔️
institution_id | integer (Institution id) | Nullable | ✔️ | ✔️
inst_admin | boolean (Inst admin)<br>Nullable <br>Default: false |  | ✔️ | ✔️
login_allowed | boolean (Login allowed) <br>Nullable <br>Default: true | | ✔️ | ✔️
uid | string (Uid) <br>non-empty<br>Nullable| | ✔️ | ✔️
is_superuser | boolean (Superuser status) | Designates that this user has all permissions without explicitly assigning them. | ✔️ | ✔️
is_staff | boolean (Staff status)| Designates whether the user can log into this admin site. | ✔️ | ✔️
is_active | boolean (Active)| Designates whether this user should be treated as active. Unselect this instead of deleting accounts. | ✔️ | ✔️
date_joined | string \<date-time\> (Date joined) | - | ✔️ | ✔️
groups | Array of integers | The groups this user belongs to. A user will get all permissions granted to each of their groups. | ✔️ | ✔️
user_permissions | Array of integers | Specific permissions for this user. | ✔️ | ✔️

### Responses
#### Response schema: application/json
<!--- details and summary tags, both, needed for expandable code --->
<details>
  <summary>201</summary>

Field | Type | Comments
--- | --- | ---
id | integer (ID) | - 
username `required` | string (Username) non-empty | -
last_login | string<uri> | Nullable  - 
previous | string<uri> Nullable | -
results `required` | Array of objects (User)

</details>

#### Response sample: 201

<!--- details and summary tags, both, needed for expandable code --->
<details>
  <summary>201</summary>
  
  ```json
  {
    "id": 0,
    "username": "string",
    "last_login": "2019-08-24T14:15:22Z",
    "first_name": "string",
    "last_name": "string",
    "email": "user@example.com",
    "password": "string",
    "password2": "string",
    "institution": "string",
    "roles": "string",
    "institution_id": 0,
    "inst_admin": false,
    "login_allowed": true,
    "uid": "string",
    "is_superuser": true,
    "is_staff": true,
    "is_active": true,
    "date_joined": "2019-08-24T14:15:22Z",
    "groups": [
      0
    ],
    "user_permissions": [
      0
    ]
  }
  ```
</details>

<!--- admin_user_read --->
## Read User<a name="admin_user_read"></a>
Retrieves information about a user.

### Request
Concept | Data
-- | --
HTTP method | GET
Path | /api/v2/admin/user/{id}/
Authorization | JWT
Content Type | application/json

### Parameters:
Name | Type | Comments | Request | Response
--- | --- | --- | --- | ---
**id** <br>_`required`_ | string | | ✔️ <br>Request path parameter| ✔️ |
id | integer (ID) | | | ✔️
username `required` | string (Username) | non-empty | | ✔️
last_login | string<date-time>(Last login) | - |  | ✔️
first_name | string (First name) | non-empty |  | ✔️
last_name | string (Last name) | non-empty |️ | ✔️
email | string <email> (Email) | non-empty |️ | ✔️
password | string (Password) | non-empty. Nullable |️ | ✔️
password2 | string (Password2) | non-empty. Nullable |️ | ✔️
institution | string (Institution) | - |  | ✔️
roles | string (Roles) | - |  | ✔️
institution_id | integer (Institution id) | Nullable |️ | ✔️
inst_admin | boolean (Inst admin) | Nullable <br>Default: false |️ | ✔️
login_allowed | boolean (Login allowed) | Nullable <br>Default: true |️ | ✔️
uid | string (Uid) | non-empty. Nullable |️ | ✔️
is_superuser | boolean (Superuser status) | Designates that this user has all permissions without explicitly assigning them. |️ | ✔️
is_staff | boolean (Staff status)| Designates whether the user can log into this admin site. |️ | ✔️
is_active | boolean (Active)| Designates whether this user should be treated as active. Unselect this instead of deleting accounts. |️ | ✔️
date_joined | string \<date-time\> (Date joined) | - |️ | ✔️
groups | Array of integers | The groups this user belongs to. A user will get all permissions granted to each of their groups. |️ | ✔️
user_permissions | Array of integers | Specific permissions for this user. |️ | ✔️

### Responses

#### Response sample: 200

<!--- details and summary tags, both, needed for expandable code --->
<details>
  <summary>200</summary>

```json
{
  "id": 0,
  "username": "string",
  "last_login": "2019-08-24T14:15:22Z",
  "first_name": "string",
  "last_name": "string",
  "email": "user@example.com",
  "password": "string",
  "password2": "string",
  "institution": "string",
  "roles": "string",
  "institution_id": 0,
  "inst_admin": false,
  "login_allowed": true,
  "uid": "string",
  "is_superuser": true,
  "is_staff": true,
  "is_active": true,
  "date_joined": "2019-08-24T14:15:22Z",
  "groups": [
    0
  ],
  "user_permissions": [
    0
  ]
}
```
</details>

<!--- admin_user_update --->
## Update User<a name="admin_user_update"></a>
Updates user's information.

### Request
Concept | Data
-- | --
HTTP Method | PUT
Path | /api/v2/admin/user/{id}/
Authorization | JWT
Content Type | application/json

### Parameters:
Name | Type | Comments | Request | Response
--- | --- | --- | --- | ---
**id** <br>_`required`_ | string | | ✔️ <br>Request path parameter| ✔️ |
**username** `required` | string (Username) | non-empty | ✔️ | ✔️
last_login | string<date-time>(Last login) | - |  | ✔️
first_name | string (First name) | non-empty | ✔️ | ✔️
last_name | string (Last name) | non-empty |✔️️ | ✔️
email | string <email> (Email) | non-empty |️✔️ | ✔️
password | string (Password) | non-empty. Nullable |️✔️ | ✔️
password2 | string (Password2) | non-empty. Nullable |️✔️ | ✔️
institution | string (Institution) | - |  | ✔️
roles | string (Roles) | - |  | ✔️
institution_id | integer (Institution id) | Nullable |️✔️ | ✔️
inst_admin | boolean (Inst admin) | Nullable <br>Default: false |️ ✔️| ✔️
login_allowed | boolean (Login allowed) | Nullable <br>Default: true |️ ✔️| ✔️
uid | string (Uid) | non-empty. Nullable |✔️️ | ✔️
is_superuser | boolean (Superuser status) | Designates that this user has all permissions without explicitly assigning them. |️✔️ | ✔️
is_staff | boolean (Staff status)| Designates whether the user can log into this admin site. |️ ✔️| ✔️
is_active | boolean (Active)| Designates whether this user should be treated as active. Unselect this instead of deleting accounts. |✔️️ | ✔️
date_joined | string \<date-time\> (Date joined) | - |️✔️ | ✔️
groups | Array of integers | The groups this user belongs to. A user will get all permissions granted to each of their groups. |️ ✔️| ✔️
user_permissions | Array of integers | Specific permissions for this user. |️✔️ | ✔️

### Responses

#### Response sample: 200

<!--- details and summary tags, both, needed for expandable code --->
<details>
  <summary>200</summary>

```json
{
  "id": 0,
  "username": "string",
  "last_login": "2019-08-24T14:15:22Z",
  "first_name": "string",
  "last_name": "string",
  "email": "user@example.com",
  "password": "string",
  "password2": "string",
  "institution": "string",
  "roles": "string",
  "institution_id": 0,
  "inst_admin": false,
  "login_allowed": true,
  "uid": "string",
  "is_superuser": true,
  "is_staff": true,
  "is_active": true,
  "date_joined": "2019-08-24T14:15:22Z",
  "groups": [
    0
  ],
  "user_permissions": [
    0
  ]
}
```
</details>

<!--- admin_user_partial_update --->
## Update User Partial Information<a name="admin_user_partial_update"></a>
Updates partial user's information.

### Request
Concept | Data
-- | --
HTTP Method | PATCH
Path | /api/v2/admin/user/{id}/
Authorization | JWT
Content Type | application/json

### Parameters:
Name | Type | Comments | Request | Response
--- | --- | --- | --- | ---
**id** <br>_`required`_ | string | | ✔️ <br>Request path parameter| ✔️ |
**username** `required` | string (Username) | non-empty | ✔️ | ✔️
last_login | string<date-time>(Last login) | - |  | ✔️
first_name | string (First name) | non-empty | ✔️ | ✔️
last_name | string (Last name) | non-empty |✔️️ | ✔️
email | string <email> (Email) | non-empty |️✔️ | ✔️
password | string (Password) | non-empty. Nullable |️✔️ | ✔️
password2 | string (Password2) | non-empty. Nullable |️✔️ | ✔️
institution | string (Institution) | - |  | ✔️
roles | string (Roles) | - |  | ✔️
institution_id | integer (Institution id) | Nullable |️✔️ | ✔️
inst_admin | boolean (Inst admin) | Nullable <br>Default: false |️ ✔️| ✔️
login_allowed | boolean (Login allowed) | Nullable <br>Default: true |️ ✔️| ✔️
uid | string (Uid) | non-empty. Nullable |✔️️ | ✔️
is_superuser | boolean (Superuser status) | Designates that this user has all permissions without explicitly assigning them. |️✔️ | ✔️
is_staff | boolean (Staff status)| Designates whether the user can log into this admin site. |️ ✔️| ✔️
is_active | boolean (Active)| Designates whether this user should be treated as active. Unselect this instead of deleting accounts. |✔️️ | ✔️
date_joined | string \<date-time\> (Date joined) | - |️✔️ | ✔️
groups | Array of integers | The groups this user belongs to. A user will get all permissions granted to each of their groups. |️ ✔️| ✔️
user_permissions | Array of integers | Specific permissions for this user. |️✔️ | ✔️

### Responses

#### Response sample: 200

<!--- details and summary tags, both, needed for expandable code --->
<details>
  <summary>200</summary>

```json
{
  "id": 0,
  "username": "string",
  "last_login": "2019-08-24T14:15:22Z",
  "first_name": "string",
  "last_name": "string",
  "email": "user@example.com",
  "password": "string",
  "password2": "string",
  "institution": "string",
  "roles": "string",
  "institution_id": 0,
  "inst_admin": false,
  "login_allowed": true,
  "uid": "string",
  "is_superuser": true,
  "is_staff": true,
  "is_active": true,
  "date_joined": "2019-08-24T14:15:22Z",
  "groups": [
    0
  ],
  "user_permissions": [
    0
  ]
}
```
</details>


<!--- admin_user_delete --->
## Delete User<a name="admin_user_delete"></a>
Deletes user from the system.

### Request
Concept | Data
-- | --
HTTP Method | DELETE
Path | /api/v2/admin/user/{id}/
Authorization | JWT
Content Type | application/json

### Parameters:
Name | Type | Comments | Request | Response
--- | --- | --- | --- | ---
**id** <br>_`required`_ | string | | ✔️ <br>Request path parameter| ✔️ |

### Responses

#### Response sample: 204
 <!--- 666 --->
<!--- details and summary tags, both, needed for expandable code --->
<details>
  <summary>204</summary>

```json
{
}
```
</details>






---

# 2. Institution Management <a name="institution_management"></a> 
- GET: [List Institutions](#admin_institution_list)
- POST: [Create Institution](#admin_institution_create)
- GET: [Read Institution](#admin_institution_read)
- PUT: [Update Institution](#admin_institution_update)
- PATCH: [Update Institution Partial Information](#admin_institution_partial_update)
- DELETE: [Delete Institution](#admin_institution_delete)


<!--- admin_institution_list --->
## List Institutions: GET <a name="admin_institution_list"></a>

API endpoint that allows Institution to be viewed or edited.

### Request

Concept | Data
-- | --
HTTP Method | GET
Path | /api/v2/admin/institution/
Authorization | JWT
Content Type | application/json

### Parameters

Name | Type | Comments | Request | Response
---- | ---- | ---- | --- | ---
search | string | A search term. | ✔️ | 
**count** `required` | integer | | | ✔️
ordering | string | Which field to use when ordering the results. | ✔️ |
limit | integer | Number of results to return per page. | ✔️ | 
offset | integer | The initial index from which to return the results. | ✔️ |
next | string \<uri\> | Nullable | | ✔️
previous | string \<uri\> | Nullable | | ✔️
**results** `required | Àrray of objects (InstitutionAdmin) | Nullable | | ✔️


### Responses

#### Response sample
<!--- details and summary tags, both, needed for expandable code --->
<details>
  <summary>200</summary>

  ````json
  {
  "count": 0,
  "next": "http://example.com",
  "previous": "http://example.com",
  "results": [
    {
      "id": 0,
      "acronym": "string",
      "name": "string",
      "external_ic": true,
      "mail_domain": "string",
      "disable_vle_learner_creation": true,
      "disable_vle_instructor_creation": true,
      "disable_vle_user_creation": true,
      "allow_learner_report": true,
      "allow_learner_audit": true,
      "allow_valid_audit": true,
      "created_at": "2019-08-24T14:15:22Z",
      "updated_at": "2019-08-24T14:15:22Z"
    }
  ]
}
  ````
</details>



<!--- admin_institution_create --->
## Create Institution<a name="admin_institution_create"></a>

<!--- admin_institution_read --->
## Read Institution<a name="admin_institution_read"></a>

<!--- admin_institution_update --->
## Update Institution<a name="admin_institution_update"></a>

<!--- admin_institution_partial_update --->
## Update Institution<a name="admin_institution_partial_update"></a>

<!--- admin_institution_delete --->
## Delete Institution<a name="admin_institution_delete"></a>

---

# 3. Instrument Management <a name="instrument_management"></a>


## List <a name="instrument_management_list"></a>

## Create <a name="instrument_management_create"></a>

## Read <a name="instrument_management_read"></a>

## Update <a name="instrument_management_update"></a>

## Delete <a name="instrument_management_delete"></a>

---

# 4. UI Management <a name="ui_management"></a>


## List <a name="ui_management_list"></a>

## Create <a name="ui_management_create"></a>

## Read <a name="ui_management_read"></a>

## Update <a name="ui_management_update"></a>

## Delete <a name="ui_management_delete"></a>


****

*****

Musce libero nunc, dignissim quis turpis quis, semper vehicula dolor. Suspendisse tincidunt consequat quam, ac posuere leo dapibus id. Cras fringilla convallis elit, at eleifend mi interam.

{{< notice note >}}
  This is a simple note.
{{</ notice >}}

{{< notice tip >}}
  This is a simple tip.
{{</ notice >}}

{{< notice info >}}
  This is a simple info.
{{</ notice >}}


{{< tabs >}}
  {{< tab "first" >}}
   This is first tab
  ###bla bla bla

  {{</ tab >}}

  {{< tab "second" >}}
  this is second tab
  bla bla bla</>
  {{</ tab >}}

  {{< tab "third" >}}
  this is third tab
  {{</ tab >}}
{{</ tabs >}}

Nulla non sollicitudin. Morbi sit amet laoreet ipsum, vel pretium mi. Morbi varius, tellus in accumsan blandit, elit ligula eleifend velit, luctus mattis ante nulla condimentum nulla. Etiam vestibulum risus vel arcu elementum eleifend. Cras at dolor eget urna varius faucibus tempus in elit.

### Image Example

Nunc porta malesuada porta. Etiam tristique vestibulum dolor at ultricies. Proin hendrerit sapien sed erat fermentum, at commodo velit consectetur.

![image example](img-1.jpg "image")

Etiam vestibulum risus vel arcu elementum eleifend. Cras at dolor eget urna varius faucibus tempus in elit. Cras a dui imperdiet, tempus metus quis, pharetra turpis. Phasellus at massa sit amet ante semper fermentum sed eget lectus. Quisque id dictum magna, et dapibus turpis.

### Example Of Code Block

In accumsan lacus ac neque maximus dictum. Phasellus eleifend leo id mattis bibendum. Curabitur et purus turpis. Vestibulum ante ipsum primis in faucibus orci luctus et ultrices posuere cubilia Curae;

````html
`<head>
  <meta charset="utf-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="stylesheet" href="/assets/css/main.css">
  <link rel="shortcut icon" type="image/png" href="/assets/img/favicon.png" >
  <script src="/assets/js/main.js"></script>
</head>
```

### Text and Quote

Cras at dolor eget urna varius faucibus tempus in elit. Cras a dui imperdiet, tempus metus quis, pharetra turpis. Phasellus at massa sit amet ante semper fermentum sed eget lectus. Quisque id dictum magna turpis.

> Etiam vestibulum risus vel arcu elementum eleifend. Cras at dolor eget urna varius faucibus tempus in elit. Cras a dui imperdiet

Etiam vestibulum risus vel arcu elementum eleifend. Cras at dolor eget urna varius faucibus tempus in elit. Cras a dui imperdiet, tempus metus quis, pharetra turpis. Phasellus at massa sit amet ante semper fermentum sed eget lectus. Quisque id dictum magna, et dapibus turpis.Etiam vestibulum risus vel arcu elementum eleifend. Cras at dolor eget urna varius faucibus tempus in elit. Cras a dui imperdiet, tempus metus quis, pharetra turpis. Phasellus at massa sit amet ante semper fermentum sed eget lectus. Quisque id dictum magna, et dapibus turpis.

[../_index.en.md]: ../admin/_index.en.md
