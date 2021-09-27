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
HTTP Method | **GET**
Path | /api/v2/admin/user/
Authorization | JWT
Content Type | application/json

### Parameters
{{< tabs >}}
  {{< tab "REQUEST" >}}
   Request parameters
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
  Response parameters
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

{{< tabs >}}
  {{< tab "REQUEST" >}}
   Request parameters
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
       Response parameters
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



<!--- ✔️ check why emoji are not working. Instead of images we should use :white_check_mark: or :heavy_check_mark: --->


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
{{< tabs >}}
  {{< tab "REQUEST" >}}
       Request parameters
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
       Request parameters
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
HTTP Method | PATCH
Path | /api/v2/admin/user/{id}/
Authorization | JWT
Content Type | application/json

### Parameters:

{{< tabs >}}
  {{< tab "REQUEST" >}}
       Request parameters
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
HTTP Method | DELETE
Path | /api/v2/admin/user/{id}/
Authorization | JWT
Content Type | application/json

### Parameters:
{{< tabs >}}
  {{< tab "REQUEST" >}}
       Request parameters
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

{{< tabs >}}
  {{< tab "REQUEST" >}}
       Request parameters
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
         </tbody>
        </table>
  {{</ tab >}}

  {{< tab "RESPONSE" >}}
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
       </tbody>
    </table>
  {{</tab>}}
{{</tabs>}}

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
- GET: [List Instruments](#admin_instrument_list)
- POST: [Create Instrument](#admin_instrument_create)
- GET: [Read Instrument](#admin_instrument_read)
- PUT: [Update Instrument](#admin_instrument_update)
- PATCH: [Update Instrument Partial Information](#admin_instrument_partial_update)
- DELETE: [Delete Instrument](#admin_instrument_delete)


<!--- admin_instrument_list --->
## List Instruments <a name="admin_instrument_list"></a>

<!--- admin_instrument_create --->
## Create instrument<a name="admin_instrument_create"></a>

<!--- admin_instrument_read --->
## Read instrument<a name="admin_instrument_read"></a>

<!--- admin_instrument_update --->
## Update instrument<a name="admin_instrument_update"></a>

<!--- admin_instrument_partial_update --->
## Update instrument<a name="admin_instrument_partial_update"></a>

<!--- admin_instrument_delete --->
## Delete instrument<a name="admin_instrument_delete"></a>



---

# 4. UI Management <a name="ui_management"></a>

- GET: [List UI](#admin_ui_list)
- POST: [Create UI](#admin_ui_create)
- GET: [Read UI](#admin_ui_read)
- PUT: [Update UI](#admin_ui_update)
- PATCH: [Update UI Partial Information](#admin_ui_partial_update)
- DELETE: [Delete UI](#admin_ui_delete)


<!--- admin_ui_list --->
## List UI<a name="admin_ui_list"></a>

<!--- admin_ui_create --->
## Create UI<a name="admin_ui_create"></a>

<!--- admin_ui_read --->
## Read UI<a name="admin_ui_read"></a>

<!--- admin_ui_update --->
## Update UI<a name="admin_ui_update"></a>

<!--- admin_ui_partial_update --->
## Update UI<a name="admin_ui_partial_update"></a>

<!--- admin_ui_delete --->
## Delete UI<a name="admin_ui_delete"></a>



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
