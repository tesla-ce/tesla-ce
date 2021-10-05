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
Set of API endpoints that allow users to be viewed or edited.

- [List Users](#admin_user_list)
- [Create User](#admin_user_create)
- [Read User](#admin_user_read)
- [Update User](#admin_user_update)
- [Update User Partial Information](#admin_user_partial_update)
- [Delete User](#admin_user_delete)


<!--- admin_user_list --->
## List Users: GET <a name="admin_user_list"></a>

API endpoint for listing Users.

### Request

Concept | Data
-- | --
HTTP Method | **GET**
Path | /api/v2/admin/user/
Authorization | JWT
Content Type | application/json

### Parameters
{{< tabs >}}
  {{< tab "REQUEST" >}}
   Request parameters.
    <table>
      <tbody>
          <tr>
              <td><strong>Name</strong></td>
              <td><strong>Type</strong></td>
              <td><strong>Comments</strong></td>
          </tr>
          <tr>
              <td>search</td>
              <td>string</td>
              <td>A search term.</td>
          </tr>
          <tr>
              <td>username</td>
              <td>string</span>&nbsp;</td>
              <td>&nbsp;</td>
          </tr>
          <tr>
              <td>first_name</td>
              <td>string</td>
              <td>&nbsp;</td>
          </tr>
          <tr>
              <td>last_name</td>
              <td>string</td>
              <td>&nbsp;</td>
          </tr>
          <tr>
              <td>email</td>
              <td>string</td>
              <td>&nbsp;</td>
          </tr>
          <tr>
              <td>institution</td>
              <td>string</td>
              <td>&nbsp;</td>
          </tr>
          <tr>
              <td>roles</td>
              <td>string</td>
              <td>&nbsp;</td>
          </tr>
          <tr>
              <td>ordering</td>
              <td>string</td>
              <td>&nbsp;Which field to use when ordering the results.</td>
          </tr>
          <tr>
              <td>limit</td>
              <td>integer</td>
              <td>&nbsp;Number of results to return per page.</td>
          </tr>
          <tr class="last undefined">
              <td>offset</td>
              <td>integer</td>
              <td>&nbsp;The initial index from which to return the results.</td>
          </tr>
      </tbody>
    </table>
  {{</ tab >}}

  {{< tab "RESPONSE" >}}
  Response parameters.
    <table>
      <tbody>
          <tr>
              <td><strong>Name</strong></td>
              <td><strong>Type</strong></td>
              <td><strong>Comments</strong></td>
          </tr>
          <tr>
              <td><strong>count</strong><br /><code>r<em class="diigoHighlight id_7521e0cfba1bf3a92fdff27c0f9e6295 type_0 yellow">equired</em></code></td>
              <td>integer</td>
              <td>&nbsp;</td>
          </tr>
          <tr>
              <td>next</td>
              <td>string &lt;uri&gt;<br />Nullable</td>
              <td>&nbsp;</td>
          </tr>
          <tr>
              <td>previous</td>
              <td>string &lt;uri&gt;<br />Nullable</td>
              <td>&nbsp;</td>
          </tr>
          <tr>
              <td>results<br /><code>required</code></td>
              <td>Array of Objects (User)</td>
              <td>&nbsp;</td>
          </tr>
      </tbody>
    </table>
  {{</ tab >}}
{{</ tabs >}}


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
HTTP Method | **POST**
Path | /api/v2/admin/user/
Authorization | JWT
Content Type | application/json


###  Parameters:

{{< tabs >}}
  {{< tab "REQUEST" >}}
   Request parameters.
        <table>
          <tbody>
              <tr>
                  <td><strong>Name</strong></td>
                  <td><strong>Type</strong></td>
                  <td><strong>Comments</strong></td>
              </tr>
              <tr>
                  <td><strong>username</strong><br><code>required</code></td>
                  <td>string (Username)<br>non-empty</td>
                  <td>-</td>
              </tr>
              <tr>
                  <td>first_name</td>
                  <td>string (First name)<br>non-empty</td>
                  <td>-</td>
              </tr>
              <tr>
                  <td>last_name</td>
                  <td>string (Last name) <br>non-empty</td>
                  <td>-</td>
              </tr>
              <tr>
                  <td>email</td>
                  <td>string &lt;email&gt; (Email)<br>non-empty</td>
                  <td>-</td>
              </tr>
              <tr>
                  <td>password</td>
                  <td>string (Password) <br>non-empty<br>Nullable</td>
                  <td>-</td>
              <tr>
                  <td>password2</td>
                  <td>string (Password2) <br>non-empty<br>Nullable</td>
                  <td>-</td>
              </tr>
             <tr>
                  <td>institution_id</td>
                  <td>integer (Institution id)<br>Nullable</td>
                  <td>-</td>
              </tr>
              <tr>
                  <td>inst_admin</td>
                  <td>boolean (Inst admin)<br>Nullable <br>Default: false</td>
                  <td>-</td>
              </tr>
              <tr>
                  <td>login_allowed</td>
                  <td>boolean (Login allowed) <br>Nullable <br>Default: true</td>
                  <td>-</td>
              </tr>
              <tr>
                  <td>uid</td>
                  <td>string (Uid) <br>non-empty<br>Nullable</td>
                  <td>-</td>
              </tr>
              <tr>
                  <td>is_superuser</td>
                  <td>boolean (Superuser status)</td>
                  <td>Designates that this user has all permissions without explicitly assigning them.</td>
              </tr>
             <tr>
                  <td>is_staff</td>
                  <td>boolean (Staff status)</td>
                  <td>Designates whether the user can log into this admin site. </td>
              </tr>
              <tr>
                  <td>is_active</td>
                  <td>boolean (Active)</td>
                  <td>Designates whether this user should be treated as active. Unselect this instead of deleting accounts.</td>
              </tr>
              <tr>
                  <td>date_joined</td>
                  <td>string &lt;date-time&gt; (Date joined)</td>
                  <td>-</td>
              </tr>
              <tr>
                  <td>groups</td>
                  <td>Array of integers </td>
                  <td>The groups this user belongs to. A user will get all permissions granted to each of their groups.</td>
              </tr>
              <tr>
                  <td>user_permissions</td>
                  <td>Array of integers</td>
                  <td>Specific permissions for this user.</td>
              </tr>
          </tbody>
        </table>
  {{</ tab >}}

  {{< tab "RESPONSE" >}}
       Response parameters.
        <table>
          <tbody>
              <tr>
                  <td><strong>Name</strong></td>
                  <td><strong>Type</strong></td>
                  <td><strong>Comments</strong></td>
              </tr>
              <tr>
                  <td>id</td>
                  <td>integer (ID)</td>
                  <td>-</td>
              </tr>
              <tr>
                  <td><strong>username</strong><br><code>required</code></td>
                  <td>string (Username)<br>non-empty</td>
                  <td>-</td>
              </tr>
              <tr>
                  <td>last_login &lt;date-time&gt;(Last login)</td>
                  <td>string </td>
                  <td></td>
              </tr>
              <tr>
                  <td>first_name</td>
                  <td>string (First name)<br>non-empty</td>
                  <td>-</td>
              </tr>
              <tr>
                  <td>last_name</td>
                  <td>string (Last name) <br>non-empty</td>
                  <td>-</td>
              </tr>
              <tr>
                  <td>email</td>
                  <td>string &lt;email&gt; (Email)<br>non-empty</td>
                  <td>-</td>
              </tr>
              <tr>
                  <td>password</td>
                  <td>string (Password) <br>non-empty<br>Nullable</td>
                  <td>-</td>
              <tr>
                  <td>password2</td>
                  <td>string (Password2) <br>non-empty<br>Nullable</td>
                  <td>-</td>
              </tr>
              <tr>
                  <td>institution</td>
                  <td>string (Institution)</td>
                  <td>-</td>
              </tr>
              <tr>
                  <td>roles</td>
                  <td>string (Roles)</td>
                  <td>-</td>
              </tr>
              <tr>
                  <td>institution_id</td>
                  <td>integer (Institution id)<br>Nullable</td>
                  <td>-</td>
              </tr>
              <tr>
                  <td>inst_admin</td>
                  <td>boolean (Inst admin)<br>Nullable <br>Default: false</td>
                  <td>-</td>
              </tr>
              <tr>
                  <td>login_allowed</td>
                  <td>boolean (Login allowed) <br>Nullable <br>Default: true</td>
                  <td>-</td>
              </tr>
              <tr>
                  <td>uid</td>
                  <td>string (Uid) <br>non-empty<br>Nullable</td>
                  <td>-</td>
              </tr>
              <tr>
                  <td>is_superuser</td>
                  <td>boolean (Superuser status)</td>
                  <td>Designates that this user has all permissions without explicitly assigning them.</td>
              </tr>
              <tr>
                  <td>is_staff</td>
                  <td>boolean (Staff status)</td>
                  <td>Designates whether the user can log into this admin site. </td>
              </tr>
              <tr>
                  <td>is_active</td>
                  <td>boolean (Active)</td>
                  <td>Designates whether this user should be treated as active. Unselect this instead of deleting accounts.</td>
              </tr>
              <tr>
                  <td>date_joined</td>
                  <td>string &lt;date-time&gt; (Date joined)</td>
                  <td>-</td>
              </tr>
              <tr>
                  <td>groups</td>
                  <td>Array of integers </td>
                  <td>The groups this user belongs to. A user will get all permissions granted to each of their groups.</td>
              </tr>
              <tr>
                  <td>user_permissions</td>
                  <td>Array of integers</td>
                  <td>Specific permissions for this user.</td>
              </tr>
          </tbody>
        </table>
  {{</ tab >}}
{{</ tabs >}}

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


<!--- ✔️ check why emoji are not working. Instead of images we should use :white_check_mark: or :heavy_check_mark: --->


### Responses

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
HTTP method | **GET**
Path | /api/v2/admin/user/{id}/
Authorization | JWT
Content Type | application/json

### Parameters:
{{< tabs >}}
  {{< tab "REQUEST" >}}
       Request parameters.
        <table>
          <tbody>
              <tr>
                  <td><strong>Name</strong></td>
                  <td><strong>Type</strong></td>
                  <td><strong>Comments</strong></td>
              </tr>
              <tr>
                  <td><strong>id</strong><br><code>required</code></td>
                  <td>string </td>
                  <td>Request path parameter</td>
              </tr>
         </tbody>
        </table>
  {{</ tab >}}

  {{< tab "RESPONSE" >}}
    Response parameters.
    <table>
      <tbody>
          <tr>
              <td><strong>Name</strong></td>
              <td><strong>Type</strong></td>
              <td><strong>Comments</strong></td>
          </tr>
          <tr>
              <td>id</td>
              <td>integer (ID)<br>non-empty </td>
              <td>-</td>
          </tr>
          <tr>
              <td><strong>username</strong><br><code>required</code></td>
              <td>string (Username)<br>non-empty </td>
              <td>-</td>
          </tr>
          <tr>
              <td>last_login</td>
              <td>string &lt;date-time&gt; (Last login) </td>
              <td>-</td>
          </tr>
          <tr>
              <td>first_name</td>
              <td>string (First name)<br>non-empty </td>
              <td>-</td>
          </tr>
          <tr>
              <td>last_name</td>
              <td>string (Last name) <br>non-empty </td>
              <td>-</td>
          </tr>
          <tr>
              <td>email</td>
              <td>string &lt;email&gt; (Email)<br>non-empty </td>
              <td>-</td>
          </tr>
          <tr>
              <td>password</td>
              <td>string (Password)<br>non-empty<br>Nullable </td>
              <td>-</td>
          </tr>
          <tr>
              <td>password2</td>
              <td>string (Password2)<br>non-empty<br>Nullable </td>
              <td>-</td>
          </tr>
          <tr>
              <td>institution</td>
              <td>string (Institution) </td>
              <td>-</td>
          </tr>
          <tr>
              <td>roles</td>
              <td>string (Roles)</td>
              <td>-</td>
          </tr>
          <tr>
              <td>institution_id</td>
              <td>integer (Institution ID)<br>Nullable </td>
              <td>-</td>
          </tr>
          <tr>
              <td>inst_admin</td>
              <td>boolean (Inst admin)<br>Nullable </td>
              <td>Default: false</td>
          </tr>
          <tr>
              <td>login_allowed</td>
              <td>boolean(Login allowed)<br>Nullable </td>
              <td>Default: true</td>
          </tr>
          <tr>
              <td>uid</td>
              <td>string (Uid)<br>non-empty<br>Nullable </td>
              <td>-</td>
          </tr>
          <tr>
              <td>is_superuser</td>
              <td>boolean (Superuser status) </td>
              <td>Designates that this user has all permissions without explicitly assigning them. </td>
          </tr>
          <tr>
              <td>is_staff</td>
              <td>boolean (Staff status) </td>
              <td>Designates whether the user can log into this admin site.</td>
          </tr>
          <tr>
              <td>is_active</td>
              <td>boolean (Active) </td>
              <td>Designates whether this user should be treated as active. Unselect this instead of deleting accounts.</td>
          </tr>
          <tr>
              <td>date_joined</td>
              <td>string &lt;date-time&gt; (Date joined) </td>
              <td>-</td>
          </tr>
          <tr>
              <td>groups</td>
              <td>Array of integers</td>
              <td>The groups this user belongs to. A user will get all permissions granted to each of their groups. </td>
          </tr>
          <tr>
              <td>user_permissions</td>
              <td>Array of integers</td>
              <td>Specific permissions for this user. </td>
          </tr>
      </tbody>
    </table>
  {{</ tab >}}
{{</ tabs >}}


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
HTTP Method | **PUT**
Path | /api/v2/admin/user/{id}/
Authorization | JWT
Content Type | application/json

### Parameters:

{{< tabs >}}
  {{< tab "REQUEST" >}}
       Request parameters.
        <table>
          <tbody>
             <tr>
                  <td><strong>Name</strong></td>
                  <td><strong>Type</strong></td>
                  <td><strong>Comments</strong></td>
              </tr>
              <tr>
                      <td><strong>id</strong><br><code>required</code></td>
                      <td>string </td>
                      <td>-</td>
              </tr>
              <tr>
                  <td><strong>username</strong><br><code>required</code></td>
                  <td>string (Username)<br>non-empty </td>
                  <td>-</td>
              <tr>
                  <td>first_name</td>
                  <td>string (First name)<br>non-empty </td>
                  <td>-</td>
              </tr>
              <tr>
                  <td>last_name</td>
                  <td>string (Last name) <br>non-empty </td>
                  <td>-</td>
              </tr>
              <tr>
                  <td>email</td>
                  <td>string &lt;email&gt; (Email)<br>non-empty </td>
                  <td>-</td>
              </tr>
              <tr>
                  <td>password</td>
                  <td>string (Password)<br>non-empty<br>Nullable </td>
                  <td>-</td>
              </tr>
              <tr>
                  <td>password2</td>
                  <td>string (Password2)<br>non-empty<br>Nullable </td>
                  <td>-</td>
              </tr>
              <tr>
                  <td>institution_id</td>
                  <td>integer (Institution ID)<br>Nullable </td>
                  <td>-</td>
              </tr>
              <tr>
                  <td>inst_admin</td>
                  <td>boolean (Inst admin)<br>Nullable </td>
                  <td>Default: false</td>
              </tr>
              <tr>
                  <td>login_allowed</td>
                  <td>boolean(Login allowed)<br>Nullable </td>
                  <td>Default: true</td>
              </tr>
              <tr>
                  <td>uid</td>
                  <td>string (Uid)<br>non-empty<br>Nullable </td>
                  <td>-</td>
              </tr>
              <tr>
                  <td>is_superuser</td>
                  <td>boolean (Superuser status) </td>
                  <td>Designates that this user has all permissions without explicitly assigning them. </td>
              </tr>
              <tr>
                  <td>is_staff</td>
                  <td>boolean (Staff status) </td>
                  <td>Designates whether the user can log into this admin site.</td>
              </tr>
              <tr>
                  <td>is_active</td>
                  <td>boolean (Active) </td>
                  <td>Designates whether this user should be treated as active. Unselect this instead of deleting accounts.</td>
              </tr>
              <tr>
                  <td>date_joined</td>
                  <td>string &lt;date-time&gt; (Date joined) </td>
                  <td>-</td>
              </tr>
              <tr>
                  <td>groups</td>
                  <td>Array of integers</td>
                  <td>The groups this user belongs to. A user will get all permissions granted to each of their groups. </td>
              </tr>
              <tr>
                  <td>user_permissions</td>
                  <td>Array of integers</td>
                  <td>Specific permissions for this user. </td>
              </tr>
         </tbody>
        </table>
  {{</ tab >}}

  {{< tab "RESPONSE" >}}
    Response parameters.
    <table>
      <tbody>
          <tr>
              <td><strong>Name</strong></td>
              <td><strong>Type</strong></td>
              <td><strong>Comments</strong></td>
          </tr>
          <tr>
                  <td><strong>id</td>
                  <td>integer (ID) </td>
                  <td></td>
          </tr>
          <tr>
              <td><strong>username</strong><br><code>required</code></td>
              <td>string (Username)<br>non-empty </td>
              <td>-</td>
          </tr>
              <tr>
                  <td>last_login</td>
                  <td>string &lt;date-time&gr; (Last login)</td>
                  <td></td>
              </tr>
          <tr>
              <td>first_name</td>
              <td>string (First name)<br>non-empty </td>
              <td>-</td>
          </tr>
          <tr>
              <td>last_name</td>
              <td>string (Last name) <br>non-empty </td>
              <td>-</td>
          </tr>
          <tr>
              <td>email</td>
              <td>string &lt;email&gt; (Email)<br>non-empty </td>
              <td>-</td>
          </tr>
          <tr>
              <td>password</td>
              <td>string (Password)<br>non-empty<br>Nullable </td>
              <td>-</td>
          </tr>
          <tr>
              <td>password2</td>
              <td>string (Password2)<br>non-empty<br>Nullable </td>
              <td>-</td>
          </tr>
          <tr>
              <td>institution</td>
              <td>string (Institution) </td>
              <td>-</td>
          </tr>
          <tr>
              <td>roles</td>
              <td>string (Roles)</td>
              <td>-</td>
          </tr>
          <tr>
              <td>institution_id</td>
              <td>integer (Institution ID)<br>Nullable </td>
              <td>-</td>
          </tr>
          <tr>
              <td>inst_admin</td>
              <td>boolean (Inst admin)<br>Nullable </td>
              <td>Default: false</td>
          </tr>
          <tr>
              <td>login_allowed</td>
              <td>boolean(Login allowed)<br>Nullable </td>
              <td>Default: true</td>
          </tr>
          <tr>
              <td>uid</td>
              <td>string (Uid)<br>non-empty<br>Nullable </td>
              <td>-</td>
          </tr>
          <tr>
              <td>is_superuser</td>
              <td>boolean (Superuser status) </td>
              <td>Designates that this user has all permissions without explicitly assigning them. </td>
          </tr>
          <tr>
              <td>is_staff</td>
              <td>boolean (Staff status) </td>
              <td>Designates whether the user can log into this admin site.</td>
          </tr>
          <tr>
              <td>is_active</td>
              <td>boolean (Active) </td>
              <td>Designates whether this user should be treated as active. Unselect this instead of deleting accounts.</td>
          </tr>
          <tr>
              <td>date_joined</td>
              <td>string &lt;date-time&gt; (Date joined) </td>
              <td>-</td>
          </tr>
          <tr>
              <td>groups</td>
              <td>Array of integers</td>
              <td>The groups this user belongs to. A user will get all permissions granted to each of their groups. </td>
          </tr>
          <tr>
              <td>user_permissions</td>
              <td>Array of integers</td>
              <td>Specific permissions for this user. </td>
          </tr>
       </tbody>
    </table>
  {{</tab>}}
{{</tabs>}}

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
HTTP Method | **PATCH**
Path | /api/v2/admin/user/{id}/
Authorization | JWT
Content Type | application/json

### Parameters:

{{< tabs >}}
  {{< tab "REQUEST" >}}
       Request parameters.
        <table>
          <tbody>
             <tr>
                  <td><strong>Name</strong></td>
                  <td><strong>Type</strong></td>
                  <td><strong>Comments</strong></td>
              </tr>
              <tr>
                      <td><strong>id</strong><br><code>required</code></td>
                      <td>string </td>
                      <td>-</td>
              </tr>
              <tr>
                  <td><strong>username</strong><br><code>required</code></td>
                  <td>string (Username)<br>non-empty </td>
                  <td>-</td>
              <tr>
                  <td>first_name</td>
                  <td>string (First name)<br>non-empty </td>
                  <td>-</td>
              </tr>
              <tr>
                  <td>last_name</td>
                  <td>string (Last name) <br>non-empty </td>
                  <td>-</td>
              </tr>
              <tr>
                  <td>email</td>
                  <td>string &lt;email&gt; (Email)<br>non-empty </td>
                  <td>-</td>
              </tr>
              <tr>
                  <td>password</td>
                  <td>string (Password)<br>non-empty<br>Nullable </td>
                  <td>-</td>
              </tr>
              <tr>
                  <td>password2</td>
                  <td>string (Password2)<br>non-empty<br>Nullable </td>
                  <td>-</td>
              </tr>
              <tr>
                  <td>institution_id</td>
                  <td>integer (Institution ID)<br>Nullable </td>
                  <td>-</td>
              </tr>
              <tr>
                  <td>inst_admin</td>
                  <td>boolean (Inst admin)<br>Nullable </td>
                  <td>Default: false</td>
              </tr>
              <tr>
                  <td>login_allowed</td>
                  <td>boolean(Login allowed)<br>Nullable </td>
                  <td>Default: true</td>
              </tr>
              <tr>
                  <td>uid</td>
                  <td>string (Uid)<br>non-empty<br>Nullable </td>
                  <td>-</td>
              </tr>
              <tr>
                  <td>is_superuser</td>
                  <td>boolean (Superuser status) </td>
                  <td>Designates that this user has all permissions without explicitly assigning them. </td>
              </tr>
              <tr>
                  <td>is_staff</td>
                  <td>boolean (Staff status) </td>
                  <td>Designates whether the user can log into this admin site.</td>
              </tr>
              <tr>
                  <td>is_active</td>
                  <td>boolean (Active) </td>
                  <td>Designates whether this user should be treated as active. Unselect this instead of deleting accounts.</td>
              </tr>
              <tr>
                  <td>date_joined</td>
                  <td>string &lt;date-time&gt; (Date joined) </td>
                  <td>-</td>
              </tr>
              <tr>
                  <td>groups</td>
                  <td>Array of integers</td>
                  <td>The groups this user belongs to. A user will get all permissions granted to each of their groups. </td>
              </tr>
              <tr>
                  <td>user_permissions</td>
                  <td>Array of integers</td>
                  <td>Specific permissions for this user. </td>
              </tr>
         </tbody>
        </table>
  {{</ tab >}}

  {{< tab "RESPONSE" >}}
    Response parameters.
    <table>
      <tbody>
          <tr>
              <td><strong>Name</strong></td>
              <td><strong>Type</strong></td>
              <td><strong>Comments</strong></td>
          </tr>
          <tr>
                  <td><strong>id</td>
                  <td>integer (ID) </td>
                  <td></td>
          </tr>
          <tr>
              <td><strong>username</strong><br><code>required</code></td>
              <td>string (Username)<br>non-empty </td>
              <td>-</td>
          </tr>
              <tr>
                  <td>last_login</td>
                  <td>string &lt;date-time&gr; (Last login)</td>
                  <td></td>
              </tr>
          <tr>
              <td>first_name</td>
              <td>string (First name)<br>non-empty </td>
              <td>-</td>
          </tr>
          <tr>
              <td>last_name</td>
              <td>string (Last name) <br>non-empty </td>
              <td>-</td>
          </tr>
          <tr>
              <td>email</td>
              <td>string &lt;email&gt; (Email)<br>non-empty </td>
              <td>-</td>
          </tr>
          <tr>
              <td>password</td>
              <td>string (Password)<br>non-empty<br>Nullable </td>
              <td>-</td>
          </tr>
          <tr>
              <td>password2</td>
              <td>string (Password2)<br>non-empty<br>Nullable </td>
              <td>-</td>
          </tr>
          <tr>
              <td>institution</td>
              <td>string (Institution) </td>
              <td>-</td>
          </tr>
          <tr>
              <td>roles</td>
              <td>string (Roles)</td>
              <td>-</td>
          </tr>
          <tr>
              <td>institution_id</td>
              <td>integer (Institution ID)<br>Nullable </td>
              <td>-</td>
          </tr>
          <tr>
              <td>inst_admin</td>
              <td>boolean (Inst admin)<br>Nullable </td>
              <td>Default: false</td>
          </tr>
          <tr>
              <td>login_allowed</td>
              <td>boolean(Login allowed)<br>Nullable </td>
              <td>Default: true</td>
          </tr>
          <tr>
              <td>uid</td>
              <td>string (Uid)<br>non-empty<br>Nullable </td>
              <td>-</td>
          </tr>
          <tr>
              <td>is_superuser</td>
              <td>boolean (Superuser status) </td>
              <td>Designates that this user has all permissions without explicitly assigning them. </td>
          </tr>
          <tr>
              <td>is_staff</td>
              <td>boolean (Staff status) </td>
              <td>Designates whether the user can log into this admin site.</td>
          </tr>
          <tr>
              <td>is_active</td>
              <td>boolean (Active) </td>
              <td>Designates whether this user should be treated as active. Unselect this instead of deleting accounts.</td>
          </tr>
          <tr>
              <td>date_joined</td>
              <td>string &lt;date-time&gt; (Date joined) </td>
              <td>-</td>
          </tr>
          <tr>
              <td>groups</td>
              <td>Array of integers</td>
              <td>The groups this user belongs to. A user will get all permissions granted to each of their groups. </td>
          </tr>
          <tr>
              <td>user_permissions</td>
              <td>Array of integers</td>
              <td>Specific permissions for this user. </td>
          </tr>
       </tbody>
    </table>
  {{</tab>}}
{{</tabs>}}


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
HTTP Method | **DELETE**
Path | /api/v2/admin/user/{id}/
Authorization | JWT
Content Type | application/json

### Parameters:
{{< tabs >}}
  {{< tab "REQUEST" >}}
       Request parameters.
        <table>
          <tbody>
             <tr>
                  <td><strong>Name</strong></td>
                  <td><strong>Type</strong></td>
                  <td><strong>Comments</strong></td>
              </tr>
              <tr>
                      <td><strong>id</strong><br><code>required</code></td>
                      <td>string </td>
                      <td>Request path parameter</td>
              </tr>
         </tbody>
        </table>
  {{</ tab >}}
{{</tabs>}}

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
Set of API endpoints that allow an Institution to be viewed or edited.

- GET: [List Institutions](#admin_institution_list)
- POST: [Create Institution](#admin_institution_create)
- GET: [Read Institution](#admin_institution_read)
- PUT: [Update Institution](#admin_institution_update)
- PATCH: [Update Institution Partial Information](#admin_institution_partial_update)
- DELETE: [Delete Institution](#admin_institution_delete)


<!--- admin_institution_list --->
## List Institutions: GET <a name="admin_institution_list"></a>

API endpoint for listing Institutions.

### Request

Concept | Data
-- | --
HTTP Method | **GET**
Path | /api/v2/admin/institution/
Authorization | JWT
Content Type | application/json

### Parameters

{{< tabs >}}
  {{< tab "REQUEST" >}}
       Request parameters.
        <table>
          <tbody>
             <tr>
                  <td><strong>Name</strong></td>
                  <td><strong>Type</strong></td>
                  <td><strong>Comments</strong></td>
              </tr>
              <tr>
                      <td>search</td>
                      <td>string </td>
                      <td>A search term</td>
              </tr>
              <tr>
                  <td>ordering</td>
                  <td>string</td>
                  <td>Which field to use when ordering the results.</td>
              <tr>
                  <td>limit</td>
                  <td>integer</td>
                  <td>Number of results to return per page.</td>
              </tr>
              <tr>
                  <td>offset</td>
                  <td>integer</td>
                  <td>The initial index from which to return the results.</td>
              </tr>
         </tbody>
        </table>
  {{</ tab >}}

  {{< tab "RESPONSE" >}}
    Response parameters.
    <table>
      <tbody>
          <tr>
              <td><strong>Name</strong></td>
              <td><strong>Type</strong></td>
              <td><strong>Comments</strong></td>
          </tr>
          <tr>
                  <td><strong>count</strong><br><code>required</code></td>
                  <td>integer (ID) </td>
                  <td></td>
          </tr>
          <tr>
              <td>next</td>
              <td>string (uri)<br>Nullable </td>
              <td>-</td>
          </tr>
          <tr>
              <td>previous</td>
              <td>string (uri)<br>Nullable </td>
              <td>-</td>
          </tr>
          <tr>
              <td><strong>results</strong><br><code>required</code></td>
              <td>Array of objects (InstitutionAdmin)</td>
              <td>-</td>
          </tr>
       </tbody>
    </table>
  {{</tab>}}
{{</tabs>}}


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

API endpoint for creating a new Institution.

### Request

Concept | Data
-- | --
HTTP Method | **POST**
Path | /api/v2/admin/institution/
Authorization | JWT
Content Type | application/json

### Parameters

{{< tabs >}}
  {{< tab "REQUEST" >}}
       Request parameters.
        <table>
          <tbody>
             <tr>
                  <td><strong>Name</strong></td>
                  <td><strong>Type</strong></td>
                  <td><strong>Comments</strong></td>
              </tr>
              <tr>
                      <td><strong>acronym</strong><br><code>required</code></td>
                      <td>string (Acronym) <br>[1 .. 255] characters</td>
                      <td>Institution acronym</td>
              </tr>
              <tr>
                      <td><strong>name</strong><br><code>required</code></td>
                      <td>string (Name) <br>non-empty</td>
                      <td>Name of the institution</td>
              </tr>
              <tr>
                  <td>external_ic</td>
                  <td>boolean (External ic)</td>
                  <td>Informed Consent is managed externally to TeSLA</td>
              <tr>
                  <td>mail_domain</td>
                  <td>string (Mail domain) <br><= 255 characters. <br>Nullable</td>
                  <td>Accepted mail domains for this institution.</td>
              </tr>
              <tr>
                  <td>disable_vle_learner_creation</td>
                  <td>boolean (Disable vle learner creation)</td>
                  <td>If enabled, VLEs cannot create learners.</td>
              </tr>
              <tr>
                  <td>disable_vle_instructor_creation</td>
                  <td>boolean (Disable vle instructor creation)</td>
                  <td>If enabled, VLEs cannot create instructors.</td>
              </tr>
              <tr>
                  <td>disable_vle_user_creation</td>
                  <td>boolean (Disable vle user creation)</td>
                  <td>If enabled, VLEs cannot create institution users.</td>
              </tr>
              <tr>
                  <td>allow_learner_report</td>
                  <td>boolean (Allow learner report)</td>
                  <td>Learners can access their reports.</td>
              </tr>
              <tr>
                  <td>allow_learner_audit</td>
                  <td>boolean (Allow learner audit)</td>
                  <td>Learners can access the audit data of their reports.</td>
              </tr>
              <tr>
                  <td>allow_valid_audit</td>
                  <td>boolean (Allow valid audit)</td>
                  <td>Audit data is available even when results are valid.</td>
              </tr>
         </tbody>
        </table>
  {{</ tab >}}

  {{< tab "RESPONSE" >}}
    Response parameters.
        <table>
          <tbody>
            <tr>
                <td><strong>Name</strong></td>
                <td><strong>Type</strong></td>
                <td><strong>Comments</strong></td>
            </tr>
            <tr>
                <td>id</td>
                <td>integer (Id)</td>
                <td>Institution Id.</td>
            </tr>
            <tr>
                <td><strong>acronym</strong><br><code>required</code></td>
                <td>string (Acronym) <br>[1 .. 255] characters</td>
                <td>Institution acronym</td>
            </tr>
            <tr>
                <td><strong>name</strong><br><code>required</code></td>
                <td>string (Name) <br>non-empty</td>
                <td>Name of the institution</td>
            </tr>
            <tr>
                <td>external_ic</td>
                <td>boolean (External ic)</td>
                <td>Informed Consent is managed externally to TeSLA</td>
            </tr>
            <tr>
                <td>mail_domain</td>
                <td>string (Mail domain) <br><= 255 characters. <br>Nullable</td>
                <td>Accepted mail domains for this institution.</td>
            </tr>
            <tr>
                <td>disable_vle_learner_creation</td>
                <td>boolean (Disable vle learner creation)</td>
                <td>If enabled, VLEs cannot create learners.</td>
            </tr>
            <tr>
                <td>disable_vle_instructor_creation</td>
                <td>boolean (Disable vle instructor creation)</td>
                <td>If enabled, VLEs cannot create instructors.</td>
            </tr>
            <tr>
                <td>disable_vle_user_creation</td>
                <td>boolean (Disable vle user creation)</td>
                <td>If enabled, VLEs cannot create institution users.</td>
            </tr>
            <tr>
                <td>allow_learner_report</td>
                <td>boolean (Allow learner report)</td>
                <td>Learners can access their reports.</td>
            </tr>
            <tr>
                <td>allow_learner_audit</td>
                <td>boolean (Allow learner audit)</td>
                <td>Learners can access the audit data of their reports.</td>
            </tr>
            <tr>
                <td>allow_valid_audit</td>
                <td>boolean (Allow valid audit)</td>
                <td>Audit data is available even when results are valid.</td>
            </tr>
            <tr>
                <td>created_at</td>
                <td>string &lt;date-time&gt;(Created at)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>updated_at</td>
                <td>string &lt;date-time&gt;(Updated at)</td>
                <td>-</td>
            </tr>
         </tbody>
        </table>
   {{</tab>}}
{{</tabs>}}

#### Request Sample: POST

```json
{
  "acronym": "string",
  "name": "string",
  "external_ic": true,
  "mail_domain": "string",
  "disable_vle_learner_creation": true,
  "disable_vle_instructor_creation": true,
  "disable_vle_user_creation": true,
  "allow_learner_report": true,
  "allow_learner_audit": true,
  "allow_valid_audit": true
}
````


### Responses

#### Response sample
<!--- details and summary tags, both, needed for expandable code --->
<details>
  <summary>201</summary>

  ````json
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
  ````
</details>


<!--- admin_institution_read --->
## Read Institution<a name="admin_institution_read"></a>
Retrieves information about an Institution.

### Request
Concept | Data
-- | --
HTTP method | **GET**
Path | /api/v2/admin/institution/{institution_id}/
Authorization | JWT
Content Type | application/json

### Parameters:
{{< tabs >}}
  {{< tab "REQUEST" >}}
       Request parameters.
        <table>
          <tbody>
              <tr>
                  <td><strong>Name</strong></td>
                  <td><strong>Type</strong></td>
                  <td><strong>Comments</strong></td>
              </tr>
              <tr>
                  <td><strong>institution_id</strong><br><code>required</code></td>
                  <td>string </td>
                  <td>Request path parameter</td>
              </tr>
         </tbody>
        </table>
  {{</ tab >}}

  {{< tab "RESPONSE" >}}
    Response parameters.
    <table>
      <tbody>
        <tr>
            <td><strong>Name</strong></td>
            <td><strong>Type</strong></td>
            <td><strong>Comments</strong></td>
        </tr>
        <tr>
            <td>id</td>
            <td>integer (Id)</td>
            <td>Institution Id.</td>
        </tr>
        <tr>
            <td><strong>acronym</strong><br><code>required</code></td>
            <td>string (Acronym) <br>[1 .. 255] characters</td>
            <td>Institution acronym</td>
        </tr>
        <tr>
            <td><strong>name</strong><br><code>required</code></td>
            <td>string (Name) <br>non-empty</td>
            <td>Name of the institution</td>
        </tr>
        <tr>
            <td>external_ic</td>
            <td>boolean (External ic)</td>
            <td>Informed Consent is managed externally to TeSLA</td>
        </tr>
        <tr>
            <td>mail_domain</td>
            <td>string (Mail domain) <br><= 255 characters. <br>Nullable</td>
            <td>Accepted mail domains for this institution.</td>
        </tr>
        <tr>
            <td>disable_vle_learner_creation</td>
            <td>boolean (Disable vle learner creation)</td>
            <td>If enabled, VLEs cannot create learners.</td>
        </tr>
        <tr>
            <td>disable_vle_instructor_creation</td>
            <td>boolean (Disable vle instructor creation)</td>
            <td>If enabled, VLEs cannot create instructors.</td>
        </tr>
        <tr>
            <td>disable_vle_user_creation</td>
            <td>boolean (Disable vle user creation)</td>
            <td>If enabled, VLEs cannot create institution users.</td>
        </tr>
        <tr>
            <td>allow_learner_report</td>
            <td>boolean (Allow learner report)</td>
            <td>Learners can access their reports.</td>
        </tr>
        <tr>
            <td>allow_learner_audit</td>
            <td>boolean (Allow learner audit)</td>
            <td>Learners can access the audit data of their reports.</td>
        </tr>
        <tr>
            <td>allow_valid_audit</td>
            <td>boolean (Allow valid audit)</td>
            <td>Audit data is available even when results are valid.</td>
        </tr>
        <tr>
            <td>created_at</td>
            <td>string &lt;date-time&gt;(Created at)</td>
            <td>-</td>
        </tr>
        <tr>
            <td>updated_at</td>
            <td>string &lt;date-time&gt;(Updated at)</td>
            <td>-</td>
        </tr>
      </tbody>
    </table>
  {{</ tab >}}
{{</ tabs >}}


### Responses

#### Response sample: 200

<!--- details and summary tags, both, needed for expandable code --->
<details>
  <summary>200</summary>

```json
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
```
</details>


<!--- admin_institution_update --->
## Update Institution<a name="admin_institution_update"></a>
API endpoint that updates Institution's information.

### Request
Concept | Data
-- | --
HTTP method | **PUT**
Path | /api/v2/admin/institution/{institution_id}/
Authorization | JWT
Content Type | application/json

### Parameters:
{{< tabs >}}
  {{< tab "REQUEST" >}}
       Request parameters.
        <table>
          <tbody>
              <tr>
                  <td><strong>Name</strong></td>
                  <td><strong>Type</strong></td>
                  <td><strong>Comments</strong></td>
              </tr>
              <tr>
                  <td><strong>institution_id</strong><br><code>required</code></td>
                  <td>string </td>
                  <td>Request path parameter</td>
              </tr>
            <tr>
                <td><strong>acronym</strong><br><code>required</code></td>
                <td>string (Acronym) <br>[1 .. 255] characters</td>
                <td>Institution acronym</td>
            </tr>
            <tr>
                <td><strong>name</strong><br><code>required</code></td>
                <td>string (Name) <br>non-empty</td>
                <td>Name of the institution</td>
            </tr>
            <tr>
                <td>external_ic</td>
                <td>boolean (External ic)</td>
                <td>Informed Consent is managed externally to TeSLA</td>
            </tr>
            <tr>
                <td>mail_domain</td>
                <td>string (Mail domain) <br><= 255 characters. <br>Nullable</td>
                <td>Accepted mail domains for this institution.</td>
            </tr>
            <tr>
                <td>disable_vle_learner_creation</td>
                <td>boolean (Disable vle learner creation)</td>
                <td>If enabled, VLEs cannot create learners.</td>
            </tr>
            <tr>
                <td>disable_vle_instructor_creation</td>
                <td>boolean (Disable vle instructor creation)</td>
                <td>If enabled, VLEs cannot create instructors.</td>
            </tr>
            <tr>
                <td>disable_vle_user_creation</td>
                <td>boolean (Disable vle user creation)</td>
                <td>If enabled, VLEs cannot create institution users.</td>
            </tr>
            <tr>
                <td>allow_learner_report</td>
                <td>boolean (Allow learner report)</td>
                <td>Learners can access their reports.</td>
            </tr>
            <tr>
                <td>allow_learner_audit</td>
                <td>boolean (Allow learner audit)</td>
                <td>Learners can access the audit data of their reports.</td>
            </tr>
            <tr>
                <td>allow_valid_audit</td>
                <td>boolean (Allow valid audit)</td>
                <td>Audit data is available even when results are valid.</td>
            </tr>
         </tbody>
        </table>
  {{</ tab >}}

  {{< tab "RESPONSE" >}}
    Response parameters.
    <table>
      <tbody>
        <tr>
            <td><strong>Name</strong></td>
            <td><strong>Type</strong></td>
            <td><strong>Comments</strong></td>
        </tr>
        <tr>
            <td>id</td>
            <td>integer (Id)</td>
            <td>Institution Id.</td>
        </tr>
        <tr>
            <td><strong>acronym</strong><br><code>required</code></td>
            <td>string (Acronym) <br>[1 .. 255] characters</td>
            <td>Institution acronym</td>
        </tr>
        <tr>
            <td><strong>name</strong><br><code>required</code></td>
            <td>string (Name) <br>non-empty</td>
            <td>Name of the institution</td>
        </tr>
        <tr>
            <td>external_ic</td>
            <td>boolean (External ic)</td>
            <td>Informed Consent is managed externally to TeSLA</td>
        </tr>
        <tr>
            <td>mail_domain</td>
            <td>string (Mail domain) <br><= 255 characters. <br>Nullable</td>
            <td>Accepted mail domains for this institution.</td>
        </tr>
        <tr>
            <td>disable_vle_learner_creation</td>
            <td>boolean (Disable vle learner creation)</td>
            <td>If enabled, VLEs cannot create learners.</td>
        </tr>
        <tr>
            <td>disable_vle_instructor_creation</td>
            <td>boolean (Disable vle instructor creation)</td>
            <td>If enabled, VLEs cannot create instructors.</td>
        </tr>
        <tr>
            <td>disable_vle_user_creation</td>
            <td>boolean (Disable vle user creation)</td>
            <td>If enabled, VLEs cannot create institution users.</td>
        </tr>
        <tr>
            <td>allow_learner_report</td>
            <td>boolean (Allow learner report)</td>
            <td>Learners can access their reports.</td>
        </tr>
        <tr>
            <td>allow_learner_audit</td>
            <td>boolean (Allow learner audit)</td>
            <td>Learners can access the audit data of their reports.</td>
        </tr>
        <tr>
            <td>allow_valid_audit</td>
            <td>boolean (Allow valid audit)</td>
            <td>Audit data is available even when results are valid.</td>
        </tr>
        <tr>
            <td>created_at</td>
            <td>string &lt;date-time&gt;(Created at)</td>
            <td>-</td>
        </tr>
        <tr>
            <td>updated_at</td>
            <td>string &lt;date-time&gt;(Updated at)</td>
            <td>-</td>
        </tr>
      </tbody>
    </table>
  {{</ tab >}}
{{</ tabs >}}

#### Request sample
```json
{
  "acronym": "string",
  "name": "string",
  "external_ic": true,
  "mail_domain": "string",
  "disable_vle_learner_creation": true,
  "disable_vle_instructor_creation": true,
  "disable_vle_user_creation": true,
  "allow_learner_report": true,
  "allow_learner_audit": true,
  "allow_valid_audit": true
}
```
### Responses

#### Response sample: 200

<!--- details and summary tags, both, needed for expandable code --->
<details>
  <summary>200</summary>

```json
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
```
</details>

<!--- admin_institution_partial_update --->
## Update Institution<a name="admin_institution_partial_update"></a>
API endpoint that updates Institution's information.

### Request
Concept | Data
-- | --
HTTP method | **PATCH**
Path | /api/v2/admin/institution/{institution_id}/
Authorization | JWT
Content Type | application/json

### Parameters:
{{< tabs >}}
  {{< tab "REQUEST" >}}
       Request parameters.
        <table>
          <tbody>
              <tr>
                  <td><strong>Name</strong></td>
                  <td><strong>Type</strong></td>
                  <td><strong>Comments</strong></td>
              </tr>
              <tr>
                  <td><strong>institution_id</strong><br><code>required</code></td>
                  <td>string </td>
                  <td>Request path parameter</td>
              </tr>
            <tr>
                <td><strong>acronym</strong><br><code>required</code></td>
                <td>string (Acronym) <br>[1 .. 255] characters</td>
                <td>Institution acronym</td>
            </tr>
            <tr>
                <td><strong>name</strong><br><code>required</code></td>
                <td>string (Name) <br>non-empty</td>
                <td>Name of the institution</td>
            </tr>
            <tr>
                <td>external_ic</td>
                <td>boolean (External ic)</td>
                <td>Informed Consent is managed externally to TeSLA</td>
            </tr>
            <tr>
                <td>mail_domain</td>
                <td>string (Mail domain) <br><= 255 characters. <br>Nullable</td>
                <td>Accepted mail domains for this institution.</td>
            </tr>
            <tr>
                <td>disable_vle_learner_creation</td>
                <td>boolean (Disable vle learner creation)</td>
                <td>If enabled, VLEs cannot create learners.</td>
            </tr>
            <tr>
                <td>disable_vle_instructor_creation</td>
                <td>boolean (Disable vle instructor creation)</td>
                <td>If enabled, VLEs cannot create instructors.</td>
            </tr>
            <tr>
                <td>disable_vle_user_creation</td>
                <td>boolean (Disable vle user creation)</td>
                <td>If enabled, VLEs cannot create institution users.</td>
            </tr>
            <tr>
                <td>allow_learner_report</td>
                <td>boolean (Allow learner report)</td>
                <td>Learners can access their reports.</td>
            </tr>
            <tr>
                <td>allow_learner_audit</td>
                <td>boolean (Allow learner audit)</td>
                <td>Learners can access the audit data of their reports.</td>
            </tr>
            <tr>
                <td>allow_valid_audit</td>
                <td>boolean (Allow valid audit)</td>
                <td>Audit data is available even when results are valid.</td>
            </tr>
         </tbody>
        </table>
  {{</ tab >}}

  {{< tab "RESPONSE" >}}
    Response parameters.
    <table>
      <tbody>
        <tr>
            <td><strong>Name</strong></td>
            <td><strong>Type</strong></td>
            <td><strong>Comments</strong></td>
        </tr>
        <tr>
            <td>id</td>
            <td>integer (Id)</td>
            <td>Institution Id.</td>
        </tr>
        <tr>
            <td><strong>acronym</strong><br><code>required</code></td>
            <td>string (Acronym) <br>[1 .. 255] characters</td>
            <td>Institution acronym</td>
        </tr>
        <tr>
            <td><strong>name</strong><br><code>required</code></td>
            <td>string (Name) <br>non-empty</td>
            <td>Name of the institution</td>
        </tr>
        <tr>
            <td>external_ic</td>
            <td>boolean (External ic)</td>
            <td>Informed Consent is managed externally to TeSLA</td>
        </tr>
        <tr>
            <td>mail_domain</td>
            <td>string (Mail domain) <br><= 255 characters. <br>Nullable</td>
            <td>Accepted mail domains for this institution.</td>
        </tr>
        <tr>
            <td>disable_vle_learner_creation</td>
            <td>boolean (Disable vle learner creation)</td>
            <td>If enabled, VLEs cannot create learners.</td>
        </tr>
        <tr>
            <td>disable_vle_instructor_creation</td>
            <td>boolean (Disable vle instructor creation)</td>
            <td>If enabled, VLEs cannot create instructors.</td>
        </tr>
        <tr>
            <td>disable_vle_user_creation</td>
            <td>boolean (Disable vle user creation)</td>
            <td>If enabled, VLEs cannot create institution users.</td>
        </tr>
        <tr>
            <td>allow_learner_report</td>
            <td>boolean (Allow learner report)</td>
            <td>Learners can access their reports.</td>
        </tr>
        <tr>
            <td>allow_learner_audit</td>
            <td>boolean (Allow learner audit)</td>
            <td>Learners can access the audit data of their reports.</td>
        </tr>
        <tr>
            <td>allow_valid_audit</td>
            <td>boolean (Allow valid audit)</td>
            <td>Audit data is available even when results are valid.</td>
        </tr>
        <tr>
            <td>created_at</td>
            <td>string &lt;date-time&gt;(Created at)</td>
            <td>-</td>
        </tr>
        <tr>
            <td>updated_at</td>
            <td>string &lt;date-time&gt;(Updated at)</td>
            <td>-</td>
        </tr>
      </tbody>
    </table>
  {{</ tab >}}
{{</ tabs >}}

#### Request sample
```json
{
  "acronym": "string",
  "name": "string",
  "external_ic": true,
  "mail_domain": "string",
  "disable_vle_learner_creation": true,
  "disable_vle_instructor_creation": true,
  "disable_vle_user_creation": true,
  "allow_learner_report": true,
  "allow_learner_audit": true,
  "allow_valid_audit": true
}
```
### Responses

#### Response sample: 200

<!--- details and summary tags, both, needed for expandable code --->
<details>
  <summary>200</summary>

```json
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
```
</details>

<!--- admin_institution_delete --->
## Delete Institution<a name="admin_institution_delete"></a>
API endpoint for deleting Institution from the system.

### Request
Concept | Data
-- | --
HTTP Method | **DELETE**
Path | /api/v2/admin/institution/{institution_id}/
Authorization | JWT
Content Type | application/json

### Parameters:
{{< tabs >}}
  {{< tab "REQUEST" >}}
       Request parameters.
        <table>
          <tbody>
             <tr>
                  <td><strong>Name</strong></td>
                  <td><strong>Type</strong></td>
                  <td><strong>Comments</strong></td>
              </tr>
              <tr>
                      <td><strong>institution_id</strong><br><code>required</code></td>
                      <td>string </td>
                      <td>Request path parameter</td>
              </tr>
         </tbody>
        </table>
  {{</ tab >}}
{{</tabs>}}

### Responses

#### Response sample: 204
<details>
  <summary>204</summary>

```json
{
}
```
</details>




---

# 3. Instrument Management <a name="instrument_management"></a>
Set of API endpoints that allow an Instrument to be viewed or edited.
<br>
- GET: [List Instruments](#admin_instrument_list)
- POST: [Create Instrument](#admin_instrument_create)
- GET: [Read Instrument](#admin_instrument_read)
- PUT: [Update Instrument](#admin_instrument_update)
- PATCH: [Update Instrument Partial Information](#admin_instrument_partial_update)
- DELETE: [Delete Instrument](#admin_instrument_delete)


<!--- admin_instrument_list --->
## List Instruments<a name="admin_instrument_list"></a> [GET]
API endpoint for listing all Instruments.

### Request

Concept | Data
-- | --
HTTP Method | **GET**
Path | /api/v2/admin/instrument/
Authorization | JWT
Content Type | application/json

### Parameters

{{< tabs >}}
  {{< tab "REQUEST" >}}
       Request parameters.
        <table>
          <tbody>
             <tr>
                  <td><strong>Name</strong></td>
                  <td><strong>Type</strong></td>
                  <td><strong>Comments</strong></td>
              </tr>
              <tr>
                      <td>search</td>
                      <td>string </td>
                      <td>A search term</td>
              </tr>
              <tr>
                  <td>ordering</td>
                  <td>string</td>
                  <td>Which field to use when ordering the results.</td>
              <tr>
                  <td>limit</td>
                  <td>integer</td>
                  <td>Number of results to return per page.</td>
              </tr>
              <tr>
                  <td>offset</td>
                  <td>integer</td>
                  <td>The initial index from which to return the results.</td>
              </tr>
         </tbody>
        </table>
  {{</ tab >}}

  {{< tab "RESPONSE" >}}
    Response parameters.
    <table>
      <tbody>
          <tr>
              <td><strong>Name</strong></td>
              <td><strong>Type</strong></td>
              <td><strong>Comments</strong></td>
          </tr>
          <tr>
                  <td><strong>count</strong><br><code>required</code></td>
                  <td>integer (ID) </td>
                  <td></td>
          </tr>
          <tr>
              <td>next</td>
              <td>string (uri)<br>Nullable </td>
              <td>-</td>
          </tr>
          <tr>
              <td>previous</td>
              <td>string (uri)<br>Nullable </td>
              <td>-</td>
          </tr>
          <tr>
              <td><strong>results</strong><br><code>required</code></td>
              <td>Array of objects (Instrument)</td>
              <td>-</td>
          </tr>
       </tbody>
    </table>
  {{</tab>}}
{{</tabs>}}


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
      "options_schema": {},
      "name": "string",
      "acronym": "string",
      "queue": "string",
      "enabled": true,
      "requires_enrolment": true,
      "description": "string",
      "identity": true,
      "originality": true,
      "authorship": true,
      "integrity": true,
      "created_at": "2019-08-24T14:15:22Z",
      "updated_at": "2019-08-24T14:15:22Z"
    }
  ]
}
  ````
</details>



<!--- admin_instrument_create --->
## Create Instrument<a name="admin_instrument_create"></a> [POST] 

API endpoint for creating a new Instrument.

### Request

Concept | Data
-- | --
HTTP Method | **POST**
Path | /api/v2/admin/instrument/
Authorization | JWT
Content Type | application/json

### Parameters

{{< tabs >}}
  {{< tab "REQUEST" >}}
       Request parameters.
        <table>
          <tbody>
             <tr>
                  <td><strong>Name</strong></td>
                  <td><strong>Type</strong></td>
                  <td><strong>Comments</strong></td>
              </tr>
              <tr>
                      <td>options_schema</td>
                      <td>object (Options schema) <br>Nullable</td>
                      <td>-</td>
              </tr>
              <tr>
                      <td><strong>name</strong><br><code>required</code></td>
                      <td>string (Name) <br>[1 .. 250] characters</td>
                      <td>Instrument name</td>
              </tr>
              <tr>
                      <td><strong>acronym</strong><br><code>required</code></td>
                      <td>string (Acronym) <br>[1 .. 30] characters</td>
                      <td>Instrument acronym</td>
              </tr>
              <tr>
                      <td><strong>queue</strong><br><code>required</code></td>
                      <td>string (Queue) <br>non-empty</td>
                      <td>Queue this instrument listens to.</td>
              </tr>
              <tr>
                  <td>enabled</td>
                  <td>boolean (Enabled)</td>
                  <td>The instrument is enabled.</td>
              <tr>
                  <td>requires_enrolment</td>
                  <td>boolean (Requires enrolment)</td>
                  <td>Whether this instrument requires enrolment.</td>
              </tr>
              <tr>
                  <td>description</td>
                  <td>string (Description) <br>Nullable</td>
                  <td>Description of the instrument.</td>
              </tr>
              <tr>
                  <td>identity</td>
                  <td>boolean (Identity)</td>
                  <td>This instrument contributes to the learner identity verification.</td>
              </tr>
              <tr>
                  <td>originality</td>
                  <td>boolean (Originality)</td>
                  <td>This instrument contributes to the assessment originality verification.</td>
              </tr>
              <tr>
                  <td>authorship</td>
                  <td>boolean (Authorship)</td>
                  <td>This instrument contributes to the assessment authorship verification.</td>
              </tr>
              <tr>
                  <td>integrity</td>
                  <td>boolean (Integrity)</td>
                  <td>This instrument contributes to the assessment integrity verification.</td>
              </tr>
         </tbody>
        </table>
  {{</ tab >}}

  {{< tab "RESPONSE" >}}
    Response parameters.
        <table>
          <tbody>
             <tr>
                  <td><strong>Name</strong></td>
                  <td><strong>Type</strong></td>
                  <td><strong>Comments</strong></td>
              </tr>
              <tr>
                      <td>id</td>
                      <td>integer (ID)</td>
                      <td>-</td>
              </tr>
              <tr>
                      <td>options_schema</td>
                      <td>object (Options schema) <br>Nullable</td>
                      <td>-</td>
              </tr>
              <tr>
                      <td><strong>name</strong><br><code>required</code></td>
                      <td>string (Name) <br>[1 .. 250] characters</td>
                      <td>Instrument name</td>
              </tr>
              <tr>
                      <td><strong>acronym</strong><br><code>required</code></td>
                      <td>string (Acronym) <br>[1 .. 30] characters</td>
                      <td>Instrument acronym</td>
              </tr>
              <tr>
                      <td><strong>queue</strong><br><code>required</code></td>
                      <td>string (Queue) <br>non-empty</td>
                      <td>Queue this instrument listens to.</td>
              </tr>
              <tr>
                  <td>enabled</td>
                  <td>boolean (Enabled)</td>
                  <td>The instrument is enabled.</td>
              <tr>
                  <td>requires_enrolment</td>
                  <td>boolean (Requires enrolment)</td>
                  <td>Whether this instrument requires enrolment.</td>
              </tr>
              <tr>
                  <td>description</td>
                  <td>string (Description) <br>Nullable</td>
                  <td>Description of the instrument.</td>
              </tr>
              <tr>
                  <td>identity</td>
                  <td>boolean (Identity)</td>
                  <td>This instrument contributes to the learner identity verification.</td>
              </tr>
              <tr>
                  <td>originality</td>
                  <td>boolean (Originality)</td>
                  <td>This instrument contributes to the assessment originality verification.</td>
              </tr>
              <tr>
                  <td>authorship</td>
                  <td>boolean (Authorship)</td>
                  <td>This instrument contributes to the assessment authorship verification.</td>
              </tr>
              <tr>
                  <td>integrity</td>
                  <td>boolean (Integrity)</td>
                  <td>This instrument contributes to the assessment integrity verification.</td>
              </tr>
              <tr>
                    <td>created_at</td>
                    <td>string &lt;date-time&gt; (Created at)</td>
                    <td>-</td>
              </tr>
              <tr>
                    <td>updated_at</td>
                    <td>string &lt;date-time&gt; (Updated at)</td>
                    <td>-</td>
              </tr>
         </tbody>
        </table>
   {{</tab>}}
{{</tabs>}}

#### Request Sample: POST

```json
{
  "options_schema": {},
  "name": "string",
  "acronym": "string",
  "queue": "string",
  "enabled": true,
  "requires_enrolment": true,
  "description": "string",
  "identity": true,
  "originality": true,
  "authorship": true,
  "integrity": true
}
````


### Responses

#### Response sample
<!--- details and summary tags, both, needed for expandable code --->
<details>
  <summary>201</summary>

  ````json
{
  "id": 0,
  "options_schema": {},
  "name": "string",
  "acronym": "string",
  "queue": "string",
  "enabled": true,
  "requires_enrolment": true,
  "description": "string",
  "identity": true,
  "originality": true,
  "authorship": true,
  "integrity": true,
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
  ````
</details>


<!--- admin_instrument_read --->
## Read Instrument<a name="admin_instrument_read"></a> [GET] 
Retrieves information about an Instrument.

### Request
Concept | Data
-- | --
HTTP method | **GET**
Path | /api/v2/admin/instrument/{instrument_id}/
Authorization | JWT
Content Type | application/json

### Parameters:
{{< tabs >}}
  {{< tab "REQUEST" >}}
       Request parameters.
        <table>
          <tbody>
              <tr>
                  <td><strong>Name</strong></td>
                  <td><strong>Type</strong></td>
                  <td><strong>Comments</strong></td>
              </tr>
              <tr>
                  <td><strong>instrument_id</strong><br><code>required</code></td>
                  <td>string </td>
                  <td>Request path parameter. A unique integer value identifying this instrument.</td>
              </tr>
         </tbody>
        </table>
  {{</ tab >}}

  {{< tab "RESPONSE" >}}
    Response parameters.
    <table>
      <tbody>
        <tr>
            <td><strong>Name</strong></td>
            <td><strong>Type</strong></td>
            <td><strong>Comments</strong></td>
        </tr>
        <tr>
            <td>id</td>
            <td>integer (Id)</td>
            <td>Instrument Id.</td>
        </tr>
        <tr>
              <td>options_schema</td>
              <td>object (Options schema) <br>Nullable</td>
              <td>-</td>
        </tr>
        <tr>
              <td><strong>name</strong><br><code>required</code></td>
              <td>string (Name) <br>[1 .. 250] characters</td>
              <td>Instrument name</td>
        </tr>
        <tr>
              <td><strong>acronym</strong><br><code>required</code></td>
              <td>string (Acronym) <br>[1 .. 30] characters</td>
              <td>Instrument acronym</td>
        </tr>
        <tr>
              <td><strong>queue</strong><br><code>required</code></td>
              <td>string (Queue) <br>non-empty</td>
              <td>Queue this instrument listens to.</td>
        </tr>
        <tr>
          <td>enabled</td>
          <td>boolean (Enabled)</td>
          <td>The instrument is enabled.</td>
        <tr>
          <td>requires_enrolment</td>
          <td>boolean (Requires enrolment)</td>
          <td>Whether this instrument requires enrolment.</td>
        </tr>
        <tr>
          <td>description</td>
          <td>string (Description) <br>Nullable</td>
          <td>Description of the instrument.</td>
        </tr>
        <tr>
          <td>identity</td>
          <td>boolean (Identity)</td>
          <td>This instrument contributes to the learner identity verification.</td>
        </tr>
        <tr>
          <td>originality</td>
          <td>boolean (Originality)</td>
          <td>This instrument contributes to the assessment originality verification.</td>
        </tr>
        <tr>
          <td>authorship</td>
          <td>boolean (Authorship)</td>
          <td>This instrument contributes to the assessment authorship verification.</td>
        </tr>
        <tr>
          <td>integrity</td>
          <td>boolean (Integrity)</td>
          <td>This instrument contributes to the assessment integrity verification.</td>
        </tr>
        <tr>
            <td>created_at</td>
            <td>string &lt;date-time&gt; (Created at)</td>
            <td>-</td>
        </tr>
        <tr>
            <td>updated_at</td>
            <td>string &lt;date-time&gt; (Updated at)</td>
            <td>-</td>
        </tr>
     </tbody>
    </table>
  {{</ tab >}}
{{</ tabs >}}


### Responses

#### Response sample: 200

<!--- details and summary tags, both, needed for expandable code --->
<details>
  <summary>200</summary>

```json
{
  "id": 0,
  "options_schema": {},
  "name": "string",
  "acronym": "string",
  "queue": "string",
  "enabled": true,
  "requires_enrolment": true,
  "description": "string",
  "identity": true,
  "originality": true,
  "authorship": true,
  "integrity": true,
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
```
</details>


<!--- admin_instrument_update --->
## Update Instrument<a name="admin_instrument_update"></a> [PUT] 
API endpoint that updates Instrument's information.

### Request
Concept | Data
-- | --
HTTP method | **PUT**
Path | /api/v2/admin/instrument/{instrument_id}/
Authorization | JWT
Content Type | application/json

### Parameters:
{{< tabs >}}
  {{< tab "REQUEST" >}}
       Request parameters.
        <table>
          <tbody>
                <tr>
                  <td><strong>Name</strong></td>
                  <td><strong>Type</strong></td>
                  <td><strong>Comments</strong></td>
                </tr>
                <tr>
                  <td><strong>instrument_id</strong><br><code>required</code></td>
                  <td>string </td>
                  <td>Request path parameter. A unique integer value identifying this instrument.</td>
                </tr>
                <tr>
                      <td>options_schema</td>
                      <td>object (Options schema) <br>Nullable</td>
                      <td>-</td>
                </tr>
                <tr>
                      <td><strong>name</strong><br><code>required</code></td>
                      <td>string (Name) <br>[1 .. 250] characters</td>
                      <td>Instrument name</td>
                </tr>
                <tr>
                      <td><strong>acronym</strong><br><code>required</code></td>
                      <td>string (Acronym) <br>[1 .. 30] characters</td>
                      <td>Instrument acronym</td>
                </tr>
                <tr>
                      <td><strong>queue</strong><br><code>required</code></td>
                      <td>string (Queue) <br>non-empty</td>
                      <td>Queue this instrument listens to.</td>
                </tr>
                <tr>
                  <td>enabled</td>
                  <td>boolean (Enabled)</td>
                  <td>The instrument is enabled.</td>
                <tr>
                  <td>requires_enrolment</td>
                  <td>boolean (Requires enrolment)</td>
                  <td>Whether this instrument requires enrolment.</td>
                </tr>
                <tr>
                  <td>description</td>
                  <td>string (Description) <br>Nullable</td>
                  <td>Description of the instrument.</td>
                </tr>
                <tr>
                  <td>identity</td>
                  <td>boolean (Identity)</td>
                  <td>This instrument contributes to the learner identity verification.</td>
                </tr>
                <tr>
                  <td>originality</td>
                  <td>boolean (Originality)</td>
                  <td>This instrument contributes to the assessment originality verification.</td>
                </tr>
                <tr>
                  <td>authorship</td>
                  <td>boolean (Authorship)</td>
                  <td>This instrument contributes to the assessment authorship verification.</td>
                </tr>
                <tr>
                  <td>integrity</td>
                  <td>boolean (Integrity)</td>
                  <td>This instrument contributes to the assessment integrity verification.</td>
                </tr>
         </tbody>
        </table>
  {{</ tab >}}

  {{< tab "RESPONSE" >}}
    Response parameters.
    <table>
      <tbody>
        <tr>
            <td><strong>Name</strong></td>
            <td><strong>Type</strong></td>
            <td><strong>Comments</strong></td>
        </tr>
        <tr>
            <td>id</td>
            <td>integer (Id)</td>
            <td>Instrument Id.</td>
        </tr>
        <tr>
              <td>options_schema</td>
              <td>object (Options schema) <br>Nullable</td>
              <td>-</td>
        </tr>
        <tr>
              <td><strong>name</strong><br><code>required</code></td>
              <td>string (Name) <br>[1 .. 250] characters</td>
              <td>Instrument name</td>
        </tr>
        <tr>
              <td><strong>acronym</strong><br><code>required</code></td>
              <td>string (Acronym) <br>[1 .. 30] characters</td>
              <td>Instrument acronym</td>
        </tr>
        <tr>
              <td><strong>queue</strong><br><code>required</code></td>
              <td>string (Queue) <br>non-empty</td>
              <td>Queue this instrument listens to.</td>
        </tr>
        <tr>
          <td>enabled</td>
          <td>boolean (Enabled)</td>
          <td>The instrument is enabled.</td>
        <tr>
          <td>requires_enrolment</td>
          <td>boolean (Requires enrolment)</td>
          <td>Whether this instrument requires enrolment.</td>
        </tr>
        <tr>
          <td>description</td>
          <td>string (Description) <br>Nullable</td>
          <td>Description of the instrument.</td>
        </tr>
        <tr>
          <td>identity</td>
          <td>boolean (Identity)</td>
          <td>This instrument contributes to the learner identity verification.</td>
        </tr>
        <tr>
          <td>originality</td>
          <td>boolean (Originality)</td>
          <td>This instrument contributes to the assessment originality verification.</td>
        </tr>
        <tr>
          <td>authorship</td>
          <td>boolean (Authorship)</td>
          <td>This instrument contributes to the assessment authorship verification.</td>
        </tr>
        <tr>
          <td>integrity</td>
          <td>boolean (Integrity)</td>
          <td>This instrument contributes to the assessment integrity verification.</td>
        </tr>
        <tr>
            <td>created_at</td>
            <td>string &lt;date-time&gt; (Created at)</td>
            <td>-</td>
        </tr>
        <tr>
            <td>updated_at</td>
            <td>string &lt;date-time&gt; (Updated at)</td>
            <td>-</td>
        </tr>
      </tbody>
    </table>
  {{</ tab >}}
{{</ tabs >}}

#### Request sample
```json
{
  "options_schema": {},
  "name": "string",
  "acronym": "string",
  "queue": "string",
  "enabled": true,
  "requires_enrolment": true,
  "description": "string",
  "identity": true,
  "originality": true,
  "authorship": true,
  "integrity": true
}
```
### Responses

#### Response sample: 200

<!--- details and summary tags, both, needed for expandable code --->
<details>
  <summary>200</summary>

```json
{
  "id": 0,
  "options_schema": {},
  "name": "string",
  "acronym": "string",
  "queue": "string",
  "enabled": true,
  "requires_enrolment": true,
  "description": "string",
  "identity": true,
  "originality": true,
  "authorship": true,
  "integrity": true,
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
```
</details>


<!--- admin_instrument_partial_update --->
## Update Instrument Partial Information<a name="admin_instrument_partial_update"></a> [PATCH]
API endpoint that updates Instrument's information.

### Request
Concept | Data
-- | --
HTTP method | **PATCH**
Path | /api/v2/admin/instrument/{instrument_id}/
Authorization | JWT
Content Type | application/json

### Parameters:
{{< tabs >}}
  {{< tab "REQUEST" >}}
       Request parameters.
        <table>
          <tbody>
                <tr>
                  <td><strong>Name</strong></td>
                  <td><strong>Type</strong></td>
                  <td><strong>Comments</strong></td>
                </tr>
                <tr>
                  <td><strong>instrument_id</strong><br><code>required</code></td>
                  <td>string </td>
                  <td>Request path parameter. A unique integer value identifying this instrument.</td>
                </tr>
                <tr>
                      <td>options_schema</td>
                      <td>object (Options schema) <br>Nullable</td>
                      <td>-</td>
                </tr>
                <tr>
                      <td><strong>name</strong><br><code>required</code></td>
                      <td>string (Name) <br>[1 .. 250] characters</td>
                      <td>Instrument name</td>
                </tr>
                <tr>
                      <td><strong>acronym</strong><br><code>required</code></td>
                      <td>string (Acronym) <br>[1 .. 30] characters</td>
                      <td>Instrument acronym</td>
                </tr>
                <tr>
                      <td><strong>queue</strong><br><code>required</code></td>
                      <td>string (Queue) <br>non-empty</td>
                      <td>Queue this instrument listens to.</td>
                </tr>
                <tr>
                  <td>enabled</td>
                  <td>boolean (Enabled)</td>
                  <td>The instrument is enabled.</td>
                <tr>
                  <td>requires_enrolment</td>
                  <td>boolean (Requires enrolment)</td>
                  <td>Whether this instrument requires enrolment.</td>
                </tr>
                <tr>
                  <td>description</td>
                  <td>string (Description) <br>Nullable</td>
                  <td>Description of the instrument.</td>
                </tr>
                <tr>
                  <td>identity</td>
                  <td>boolean (Identity)</td>
                  <td>This instrument contributes to the learner identity verification.</td>
                </tr>
                <tr>
                  <td>originality</td>
                  <td>boolean (Originality)</td>
                  <td>This instrument contributes to the assessment originality verification.</td>
                </tr>
                <tr>
                  <td>authorship</td>
                  <td>boolean (Authorship)</td>
                  <td>This instrument contributes to the assessment authorship verification.</td>
                </tr>
                <tr>
                  <td>integrity</td>
                  <td>boolean (Integrity)</td>
                  <td>This instrument contributes to the assessment integrity verification.</td>
                </tr>
         </tbody>
        </table>
  {{</ tab >}}

  {{< tab "RESPONSE" >}}
    Response parameters.
    <table>
      <tbody>
        <tr>
            <td><strong>Name</strong></td>
            <td><strong>Type</strong></td>
            <td><strong>Comments</strong></td>
        </tr>
        <tr>
            <td>id</td>
            <td>integer (Id)</td>
            <td>Instrument Id.</td>
        </tr>
        <tr>
              <td>options_schema</td>
              <td>object (Options schema) <br>Nullable</td>
              <td>-</td>
        </tr>
        <tr>
              <td><strong>name</strong><br><code>required</code></td>
              <td>string (Name) <br>[1 .. 250] characters</td>
              <td>Instrument name</td>
        </tr>
        <tr>
              <td><strong>acronym</strong><br><code>required</code></td>
              <td>string (Acronym) <br>[1 .. 30] characters</td>
              <td>Instrument acronym</td>
        </tr>
        <tr>
              <td><strong>queue</strong><br><code>required</code></td>
              <td>string (Queue) <br>non-empty</td>
              <td>Queue this instrument listens to.</td>
        </tr>
        <tr>
          <td>enabled</td>
          <td>boolean (Enabled)</td>
          <td>The instrument is enabled.</td>
        <tr>
          <td>requires_enrolment</td>
          <td>boolean (Requires enrolment)</td>
          <td>Whether this instrument requires enrolment.</td>
        </tr>
        <tr>
          <td>description</td>
          <td>string (Description) <br>Nullable</td>
          <td>Description of the instrument.</td>
        </tr>
        <tr>
          <td>identity</td>
          <td>boolean (Identity)</td>
          <td>This instrument contributes to the learner identity verification.</td>
        </tr>
        <tr>
          <td>originality</td>
          <td>boolean (Originality)</td>
          <td>This instrument contributes to the assessment originality verification.</td>
        </tr>
        <tr>
          <td>authorship</td>
          <td>boolean (Authorship)</td>
          <td>This instrument contributes to the assessment authorship verification.</td>
        </tr>
        <tr>
          <td>integrity</td>
          <td>boolean (Integrity)</td>
          <td>This instrument contributes to the assessment integrity verification.</td>
        </tr>
        <tr>
            <td>created_at</td>
            <td>string &lt;date-time&gt; (Created at)</td>
            <td>-</td>
        </tr>
        <tr>
            <td>updated_at</td>
            <td>string &lt;date-time&gt; (Updated at)</td>
            <td>-</td>
        </tr>
      </tbody>
    </table>
  {{</ tab >}}
{{</ tabs >}}

#### Request sample
```json
{
  "options_schema": {},
  "name": "string",
  "acronym": "string",
  "queue": "string",
  "enabled": true,
  "requires_enrolment": true,
  "description": "string",
  "identity": true,
  "originality": true,
  "authorship": true,
  "integrity": true
}
```
### Responses

#### Response sample: 200

<!--- details and summary tags, both, needed for expandable code --->
<details>
  <summary>200</summary>

```json
{
  "id": 0,
  "options_schema": {},
  "name": "string",
  "acronym": "string",
  "queue": "string",
  "enabled": true,
  "requires_enrolment": true,
  "description": "string",
  "identity": true,
  "originality": true,
  "authorship": true,
  "integrity": true,
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
```
</details>


<!--- admin_instrument_delete --->
## Delete Instrument<a name="admin_instrument_delete"></a> [DELETE] 
API endpoint for deleting Instrument from the system.

### Request
Concept | Data
-- | --
HTTP Method | **DELETE**
Path | /api/v2/admin/instrument/{instrument_id}/
Authorization | JWT
Content Type | application/json

### Parameters:
{{< tabs >}}
  {{< tab "REQUEST" >}}
       Request parameters.
        <table>
          <tbody>
             <tr>
                  <td><strong>Name</strong></td>
                  <td><strong>Type</strong></td>
                  <td><strong>Comments</strong></td>
              </tr>
              <tr>
                      <td><strong>instrument_id</strong><br><code>required</code></td>
                      <td>integer </td>
                      <td>Request path parameter. A unique integer value identifying this instrument.</td>
              </tr>
         </tbody>
        </table>
  {{</ tab >}}
{{</tabs>}}

### Responses

#### Response sample: 204
<details>
  <summary>204</summary>

```json
{
}
```
</details>



---

# 4. UI Management <a name="ui_management"></a>
Set of API endpoints that allow a UI to be viewed or edited.

- [List UI](#admin_ui_list) (GET)
- [Create UI](#admin_ui_create) (POST)
- [Read UI](#admin_ui_read) (GET)
- [Update UI](#admin_ui_update) (PUT)
- [Update UI Partial Information](#admin_ui_partial_update) (PATCH)
- [Delete UI](#admin_ui_delete) (DELETE)


<!--- admin_ui_list --->
## List UI<a name="admin_ui_list"></a> (GET)
API endpoint for listing UI.
### Request
Concept | Data
-- | --
HTTP method | **GET**
Path | /api/v2/admin/ui/
Authorization | JWT
Content Type | application/json

### Parameters:
{{< tabs >}}
  {{< tab "REQUEST" >}}
       Request parameters.
        <table>
          <tbody>
                <tr>
                  <td><strong>Name</strong></td>
                  <td><strong>Type</strong></td>
                  <td><strong>Comments</strong></td>
                </tr>
                <tr>
                      <td>search</td>
                      <td>string</td>
                      <td>A search term.</td>
                </tr>
                <tr>
                  <td>ordering</td>
                  <td>string</td>
                  <td>Which field to use when ordering the results.</td>
                <tr>
               <tr>
                  <td>limit</td>
                  <td>integer</td>
                  <td>Number of results to return per page.</td>
                </tr>
               <tr>
                  <td>offset</td>
                  <td>integer</td>
                  <td>The initial index from which to return the results.</td>
                </tr>
         </tbody>
        </table>
  {{</ tab >}}

  {{< tab "RESPONSE" >}}
    Response parameters.
    <table>
      <tbody>
            <tr>
              <td><strong>Name</strong></td>
              <td><strong>Type</strong></td>
              <td><strong>Comments</strong></td>
            </tr>
          <tr>
                  <td><strong>count</strong><br><code>required</code></td>
                  <td>integer (ID) </td>
                  <td></td>
          </tr>
          <tr>
              <td>next</td>
              <td>string (uri)<br>Nullable </td>
              <td>-</td>
          </tr>
          <tr>
              <td>previous</td>
              <td>string (uri)<br>Nullable </td>
              <td>-</td>
          </tr>
          <tr>
              <td><strong>results</strong><br><code>required</code></td>
              <td>Array of objects (Instrument)</td>
              <td>-</td>
          </tr>
      </tbody>
    </table>
  {{</ tab >}}
{{</ tabs >}}

### Responses

#### Response sample: 200

<!--- details and summary tags, both, needed for expandable code --->
<details>
  <summary>200</summary>

```json
{
  "count": 0,
  "next": "http://example.com",
  "previous": "http://example.com",
  "results": [
    {
      "id": "string",
      "route": "string",
      "enabled": true,
      "roles": "string"
    }
  ]
}
```
</details>


<!--- admin_ui_create --->
## Create UI<a name="admin_ui_create"></a> (POST)
API endpoint for creating a new UI.


### Request
Concept | Data
-- | --
HTTP method | **POST**
Path | /api/v2/admin/ui/
Authorization | JWT
Content Type | application/json

### Parameters:
{{< tabs >}}
  {{< tab "REQUEST" >}}
       Request parameters.
        <table>
          <tbody>
                <tr>
                  <td><strong>Name</strong></td>
                  <td><strong>Type</strong></td>
                  <td><strong>Comments</strong></td>
                </tr>
                <tr>
                      <td><strong>route</strong><br><code>required</code></td>
                      <td>string (Route) <br>[1 .. 250] characters</td>
                      <td>Affected Route.</td>
                </tr>
                <tr>
                  <td>enabled</td>
                  <td>boolean (Enabled)</td>
                  <td>Status.</td>
                <tr>
               <tr>
                  <td>roles</td>
                  <td>string (Roles) <br><=250 characters.<br>Nullable</td>
                  <td>Required roles.</td>
                </tr>
         </tbody>
        </table>
  {{</ tab >}}

  {{< tab "RESPONSE" >}}
    Response parameters.
    <table>
      <tbody>
            <tr>
              <td><strong>Name</strong></td>
              <td><strong>Type</strong></td>
              <td><strong>Comments</strong></td>
            </tr>
            <tr>
              <td>ui_id</td>
              <td>string (Id)</td>
              <td>-</td>
            </tr>
            <tr>
                  <td><strong>route</strong><br><code>required</code></td>
                  <td>string (Route) <br>[1 .. 250] characters</td>
                  <td>Affected Route.</td>
            </tr>
            <tr>
              <td>enabled</td>
              <td>boolean (Enabled)</td>
              <td>Status.</td>
            <tr>
            <tr>
              <td>roles</td>
              <td>string (Roles) <br><=250 characters.<br>Nullable</td>
              <td>Required roles.</td>
            </tr>
      </tbody>
    </table>
  {{</ tab >}}
{{</ tabs >}}

#### Request sample
```json
{
  "route": "string",
  "enabled": true,
  "roles": "string"
}
```
### Responses

#### Response sample: 201

<!--- details and summary tags, both, needed for expandable code --->
<details>
  <summary>201</summary>

```json
{
  "id": "string",
  "route": "string",
  "enabled": true,
  "roles": "string"
}
```
</details>


<!--- admin_ui_read --->
## Read UI<a name="admin_ui_read"></a> (GET)
Retrieves information about UI Options.

### Request
Concept | Data
-- | --
HTTP method | **GET**
Path | /api/v2/admin/ui/{ui_id}/
Authorization | JWT
Content Type | application/json

### Parameters:
{{< tabs >}}
  {{< tab "REQUEST" >}}
       Request parameters.
        <table>
          <tbody>
                <tr>
                  <td><strong>Name</strong></td>
                  <td><strong>Type</strong></td>
                  <td><strong>Comments</strong></td>
                </tr>
                <tr>
                  <td><strong>ui_id</strong><br><code>required</code></td>
                  <td>string </td>
                  <td>Request path parameter. </td>
                </tr>
         </tbody>
        </table>
  {{</ tab >}}

  {{< tab "RESPONSE" >}}
    Response parameters.
    <table>
      <tbody>
            <tr>
              <td><strong>Name</strong></td>
              <td><strong>Type</strong></td>
              <td><strong>Comments</strong></td>
            </tr>
            <tr>
              <td>ui_id</td>
              <td>string (Id)</td>
              <td>-</td>
            </tr>
            <tr>
                  <td><strong>route</strong><br><code>required</code></td>
                  <td>string (Route) <br>[1 .. 250] characters</td>
                  <td>Affected Route.</td>
            </tr>
            <tr>
              <td>enabled</td>
              <td>boolean (Enabled)</td>
              <td>Status.</td>
            <tr>
            <tr>
              <td>roles</td>
              <td>string (Roles) <br><=250 characters.<br>Nullable</td>
              <td>Required roles.</td>
            </tr>
      </tbody>
    </table>
  {{</ tab >}}
{{</ tabs >}}


### Responses

#### Response sample: 200

<!--- details and summary tags, both, needed for expandable code --->
<details>
  <summary>200</summary>

```json
{
  "id": "string",
  "route": "string",
  "enabled": true,
  "roles": "string"
}
```
</details>



<!--- admin_ui_update --->
## Update UI<a name="admin_ui_update"></a> (PUT)
API endpoint that updates UI Options' information.

### Request
Concept | Data
-- | --
HTTP method | **PUT**
Path | /api/v2/admin/ui/{ui_id}/
Authorization | JWT
Content Type | application/json

### Parameters:
{{< tabs >}}
  {{< tab "REQUEST" >}}
       Request parameters.
        <table>
          <tbody>
                <tr>
                  <td><strong>Name</strong></td>
                  <td><strong>Type</strong></td>
                  <td><strong>Comments</strong></td>
                </tr>
                <tr>
                  <td><strong>ui_id</strong><br><code>required</code></td>
                  <td>string </td>
                  <td>Request path parameter. </td>
                </tr>
                <tr>
                      <td><strong>route</strong><br><code>required</code></td>
                      <td>string (Route) <br>[1 .. 250] characters</td>
                      <td>Affected Route.</td>
                </tr>
                <tr>
                  <td>enabled</td>
                  <td>boolean (Enabled)</td>
                  <td>Status.</td>
                <tr>
               <tr>
                  <td>roles</td>
                  <td>string (Roles) <br><=250 characters.<br>Nullable</td>
                  <td>Required roles.</td>
                </tr>
         </tbody>
        </table>
  {{</ tab >}}

  {{< tab "RESPONSE" >}}
    Response parameters.
    <table>
      <tbody>
            <tr>
              <td><strong>Name</strong></td>
              <td><strong>Type</strong></td>
              <td><strong>Comments</strong></td>
            </tr>
            <tr>
              <td>ui_id</td>
              <td>string (Id)</td>
              <td>-</td>
            </tr>
            <tr>
                  <td><strong>route</strong><br><code>required</code></td>
                  <td>string (Route) <br>[1 .. 250] characters</td>
                  <td>Affected Route.</td>
            </tr>
            <tr>
              <td>enabled</td>
              <td>boolean (Enabled)</td>
              <td>Status.</td>
            <tr>
            <tr>
              <td>roles</td>
              <td>string (Roles) <br><=250 characters.<br>Nullable</td>
              <td>Required roles.</td>
            </tr>
      </tbody>
    </table>
  {{</ tab >}}
{{</ tabs >}}

#### Request sample
```json
{
  "route": "string",
  "enabled": true,
  "roles": "string"
}
```
### Responses

#### Response sample: 200

<!--- details and summary tags, both, needed for expandable code --->
<details>
  <summary>200</summary>

```json
{
  "id": "string",
  "route": "string",
  "enabled": true,
  "roles": "string"
}
```
</details>


<!--- admin_ui_partial_update --->
## Update UI Partial Information<a name="admin_ui_partial_update"></a> (PATCH)
API endpoint that updates UI Options' information.

### Request
Concept | Data
-- | --
HTTP method | **PATCH**
Path | /api/v2/admin/ui/{ui_id}/
Authorization | JWT
Content Type | application/json

### Parameters:
{{< tabs >}}
  {{< tab "REQUEST" >}}
       Request parameters.
        <table>
          <tbody>
                <tr>
                  <td><strong>Name</strong></td>
                  <td><strong>Type</strong></td>
                  <td><strong>Comments</strong></td>
                </tr>
                <tr>
                  <td><strong>ui_id</strong><br><code>required</code></td>
                  <td>string </td>
                  <td>Request path parameter. </td>
                </tr>
                <tr>
                      <td><strong>route</strong><br><code>required</code></td>
                      <td>string (Route) <br>[1 .. 250] characters</td>
                      <td>Affected Route.</td>
                </tr>
                <tr>
                  <td>enabled</td>
                  <td>boolean (Enabled)</td>
                  <td>Status.</td>
                <tr>
               <tr>
                  <td>roles</td>
                  <td>string (Roles) <br><=250 characters.<br>Nullable</td>
                  <td>Required roles.</td>
                </tr>
         </tbody>
        </table>
  {{</ tab >}}

  {{< tab "RESPONSE" >}}
    Response parameters.
    <table>
      <tbody>
            <tr>
              <td><strong>Name</strong></td>
              <td><strong>Type</strong></td>
              <td><strong>Comments</strong></td>
            </tr>
            <tr>
              <td>ui_id</td>
              <td>string (Id)</td>
              <td>-</td>
            </tr>
            <tr>
                  <td><strong>route</strong><br><code>required</code></td>
                  <td>string (Route) <br>[1 .. 250] characters</td>
                  <td>Affected Route.</td>
            </tr>
            <tr>
              <td>enabled</td>
              <td>boolean (Enabled)</td>
              <td>Status.</td>
            <tr>
            <tr>
              <td>roles</td>
              <td>string (Roles) <br><=250 characters.<br>Nullable</td>
              <td>Required roles.</td>
            </tr>
      </tbody>
    </table>
  {{</ tab >}}
{{</ tabs >}}

#### Request sample
```json
{
  "route": "string",
  "enabled": true,
  "roles": "string"
}
```
### Responses

#### Response sample: 200

<!--- details and summary tags, both, needed for expandable code --->
<details>
  <summary>200</summary>

```json
{
  "id": "string",
  "route": "string",
  "enabled": true,
  "roles": "string"
}
```
</details>

<!--- admin_ui_delete --->
## Delete UI<a name="admin_ui_delete"></a> (DELETE)
API endpoint for deleting UI Options from the system.

### Request
Concept | Data
-- | --
HTTP Method | **DELETE**
Path | /api/v2/admin/ui/{ui_id}/
Authorization | JWT
Content Type | application/json

### Parameters:
{{< tabs >}}
  {{< tab "REQUEST" >}}
       Request parameters.
        <table>
          <tbody>
             <tr>
                  <td><strong>Name</strong></td>
                  <td><strong>Type</strong></td>
                  <td><strong>Comments</strong></td>
              </tr>
              <tr>
                      <td><strong>ui_id</strong><br><code>required</code></td>
                      <td>string </td>
                      <td>Request path parameter. .</td>
              </tr>
         </tbody>
        </table>
  {{</ tab >}}
{{</tabs>}}

### Responses

#### Response sample: 204
<details>
  <summary>204</summary>

```json
{
}
```
</details>


