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
API endpoint that allows authentication process for front-end.


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
  "email": " inst_admin@example.com", 
  "password": "string"
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
      "access_token":"8cdbacfe-de57-4c44-ad67-62f665bebfab", 
      "refresh_token":"0f1d9342"
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
  "role_id": "bad6209f-4310-4621-aa09-22178e71a7a9", 
  "secret_id": "1211c5e7-d122-437b-9e45-824aa498bae9"
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
      "consumer_key": "0e55ff96-6a87-46bf-bfe9-09a882282d0d", 
      "consumer_secret": "dd5c2714-f66a-4066-9b51-ac51b1f35a39"
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
    "access_token": "ad56bb9e-c468-4c93-aef5-68048707b4bc", 
    "refresh_token": "b96ac612-8473-423b-ac8b-3829a81afd7f"
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
  "refresh_token": "f59fc2e6-58e9-44a7-a398-a5c214a35ee7"
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
    "access_token": "fe67d841-5c6b-4799-b22c-a9493c401161"
  }
}


  ````
</details>

<div style="text-align:right">

[[top page]](#table-of-content) 
</div>
<br>



