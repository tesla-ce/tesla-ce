---
title: "Authentication"
weight: 2
draft: false
# search related keywords
keywords: ["API","authentication", "auth"]
---
{{< notice info >}}
  **This page is under construction** <br>
  We're working on it!
{{</ notice >}}

<table><tr><td>

# Table of Contents
1. [Auth Login Create](#auth_login_create)
1. [Auth Approle Create](#auth_approle_create)
1. [Auth Token Refresh Create](#auth_token_refresh_create)

</td></tr></table>

<br><br>

 <!--- auth_login_create --->
# 1. Auth Login Create <a name="auth_login_create"></a>
---
API endpoint that allow authentication process for front-end


### Request

<table style="table-layout: fixed; width: 100%">
 <tbody>
    <tr>
        <td style="width:20%"><strong>Concept</strong></td>
        <td><strong>Data</strong></td>
    </tr>
    <tr>
        <td>HTTP Method</td>
        <td><strong><code>POST</code></strong></td>
    </tr>
    <tr>
        <td>Path</td>
        <td><span style="word-wrap: break-word">/api/v2/auth/login</span></td>
    </tr>
    <tr>
        <td>Authorization</td>
        <td>JWT</td>
    </tr>
    <tr>
        <td>Content Type</td>
        <td>application/json</td>
    </tr>
 </tbody>
</table>

### Parameters

{{< tabs >}}
  {{< tab "REQUEST" >}}
       Request parameters.<br>
        <table>
          <tbody>
            <tr>
                <td><strong>Name</strong></td>
                <td><strong>Type</strong></td>
                <td><strong>Comments</strong></td>
            </tr>
            <tr>
                <td><strong>email</strong><br><code>required</code></td>
                <td>string</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>password</strong><br><code>required</code></td>
                <td>string</td>
                <td>-</td>
            </tr>
            <tr>
                <td>realm</td>
                <td>string</td>
                <td>If the system allows several authentication methods, 
                    this parameter indicates which one is used.<br>
                    Default: "api"</td>
            </tr>
         </tbody>
        </table>
  {{</ tab >}}

  {{< tab "RESPONSE" >}}
    Response parameters.<br>
    <table>
      <tbody>
          <tr>
            <td><strong>Name</strong></td>
            <td><strong>Type</strong></td>
            <td><strong>Comments</strong></td>
          </tr>
          <tr>
            <td><strong>access_token</strong><br><code>required</code></td>
            <td>string </td>
            <td>-</td>
          </tr>
          <tr>
            <td><strong>refresh_token</strong><br><code>required</code></td>
            <td>string </td>
            <td>-</td>
          </tr>
       </tbody>
    </table>
  {{</tab>}}
{{</tabs>}}

#### Request sample
`````json
{
  "email": " inst_admin@dev.tesla-ce.eu", 
  "password": "inst_admin@dev.tesla-ce.eu"
} 

`````
### Responses

#### Response sample
<!--- details and summary tags, both, needed for expandable code --->
<details>
  <summary>201</summary>

  ````json
{
    "token": {
      "access_token":"eyJhbGciOiAiUlMyNTYiLCAidHlwIjoWW89", 
      "refresh_token":"eyJhbG"
    }
}

  ````
</details>

<div style="text-align:right">

[[top page]](#table-of-content) 
</div>
<br>


<!--- auth_approle_create --->
# 2. Auth Approle Create <a name="auth_approle_create"></a>
---
API endpoint that creates the access token for the SDK.


### Request

<table style="table-layout: fixed; width: 100%">
 <tbody>
    <tr>
        <td style="width:20%"><strong>Concept</strong></td>
        <td><strong>Data</strong></td>
    </tr>
    <tr>
        <td>HTTP Method</td>
        <td><strong><code>POST</code></strong></td>
    </tr>
    <tr>
        <td>Path</td>
        <td><span style="word-wrap: break-word">/api/v2/auth/approle</span></td>
    </tr>
    <tr>
        <td>Authorization</td>
        <td>JWT</td>
    </tr>
    <tr>
        <td>Content Type</td>
        <td>application/json</td>
    </tr>
 </tbody>
</table>

### Parameters

{{< tabs >}}
  {{< tab "REQUEST" >}}
       Request parameters.<br>
        <table>
          <tbody>
            <tr>
                <td><strong>Name</strong></td>
                <td><strong>Type</strong></td>
                <td><strong>Comments</strong></td>
            </tr>
            <tr>
                <td><strong>role_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>secret_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>-</td>
            </tr>
         </tbody>
        </table>
  {{</ tab >}}

  {{< tab "RESPONSE" >}}
    Response parameters.<br>
    <table>
      <tbody>
          <tr>
            <td><strong>Name</strong></td>
            <td><strong>Type</strong></td>
            <td><strong>Comments</strong></td>
          </tr>
          <tr>
            <td><strong>access_token</strong><br><code>required</code></td>
            <td>string </td>
            <td>-</td>
          </tr>
          <tr>
            <td><strong>refresh_token</strong><br><code>required</code></td>
            <td>string </td>
            <td>-</td>
          </tr>
          <tr>
            <td><strong>access_token</strong><br><code>required</code></td>
            <td>string </td>
            <td>-</td>
          </tr>
       </tbody>
    </table>
  {{</tab>}}
{{</tabs>}}

#### Request sample
`````json
{
  "role_id": "xxx", 
  "secret_id": "xxx"
} 


`````
### Responses

#### Response sample
<!--- details and summary tags, both, needed for expandable code --->
<details>
  <summary>201</summary>

  ````json
{
  "apps": [], 
  "config": { "TESLA_DOMAIN": "string" }, 
  "description": "string", 
  "domain": "string", 
  "institution_acronym": "default", 
  "institution_id": 1, 
  "module": "string", 
  "services": {}, 
  "vle_id": 1, 
  "vle_name": "default_moodle", 
  "vle_url": "string", 
  "type": "vle", 
  "pk": 1, 
  "vle": { 
    "id": 1, 
    "lti": { 
      "consumer_key": "c8e87343-9b3c-44ea-bb85-c640cc1f020b", 
      "consumer_secret": "9bba2695-47b7-4d64-94f6-fbc76cd945b1"
    }, 
    "name": "default_moodle", 
    "type": 0, 
    "url": "string", 
    "client_id": null, 
    "created_at": "2021-10-07T10:25:15.580239Z", 
    "updated_at": "2021-11-15T15:24:33.985594Z", 
    "institution": 1
  }, 
  "token": { 
    "access_token": "32ecbeb7-76f6-482f-8d92-bbdd50470704", 
    "refresh_token": "2b450c9a-4211-4e1b-92ba-0893346da742"
  } 
}


  ````
</details>

<div style="text-align:right">

[[top page]](#table-of-content) 
</div>
<br>

<!--- auth_token_refresh_create --->
# 3. Auth Token Refresh Create <a name="auth_token_refresh_create"></a>
---
API endpoint used for recreating main token when it is expired.


### Request

<table style="table-layout: fixed; width: 100%">
 <tbody>
    <tr>
        <td style="width:20%"><strong>Concept</strong></td>
        <td><strong>Data</strong></td>
    </tr>
    <tr>
        <td>HTTP Method</td>
        <td><strong><code>POST</code></strong></td>
    </tr>
    <tr>
        <td>Path</td>
        <td><span style="word-wrap: break-word">/api/v2/auth/token/refresh</span></td>
    </tr>
    <tr>
        <td>Authorization</td>
        <td>JWT</td>
    </tr>
    <tr>
        <td>Content Type</td>
        <td>application/json</td>
    </tr>
 </tbody>
</table>

### Parameters

{{< tabs >}}
  {{< tab "REQUEST" >}}
       Request parameters.<br>
        <table>
          <tbody>
            <tr>
                <td><strong>Name</strong></td>
                <td><strong>Type</strong></td>
                <td><strong>Comments</strong></td>
            </tr>
            <tr>
                <td><strong>refresh_token</strong><br><code>required</code></td>
                <td>string</td>
                <td>-</td>
            </tr>
         </tbody>
        </table>
  {{</ tab >}}

  {{< tab "RESPONSE" >}}
    Response parameters.<br>
    <table>
      <tbody>
          <tr>
            <td><strong>Name</strong></td>
            <td><strong>Type</strong></td>
            <td><strong>Comments</strong></td>
          </tr>
          <tr>
            <td><strong>access_token</strong><br><code>required</code></td>
            <td>string </td>
            <td>-</td>
          </tr>
       </tbody>
    </table>
  {{</tab>}}
{{</tabs>}}

#### Request sample
`````json
{ 
  "refresh_token": "2b450c9a-4211-4e1b-92ba-0893346da742"
} 


`````
### Responses

#### Response sample
<!--- details and summary tags, both, needed for expandable code --->
<details>
  <summary>201</summary>

  ````json
{
  "token": {
    "access_token": "7ce0eb17-3bdc-4fee-bce3-3a40386b0fc6"
  }
}


  ````
</details>

<div style="text-align:right">

[[top page]](#table-of-content) 
</div>
<br>



