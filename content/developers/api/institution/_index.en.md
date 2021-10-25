---
title: "Institution"
weight: 3
draft: false
# search related keywords
keywords: ["API","institution"]
---
{{< notice info >}}
  **This page is under construction** <br>
  We're working on it!
{{</ notice >}}

<table><tr><td>

# Table of Content

1. [Institution Management](#institution_management)
2. [Institution VLE Management](#institution_vle_management)
3. Institution Course
4. Institution Group
5. Institution Group Course
6. Institution IC
7. Institution IC Document
8. Institution Instrument
9. Institution UI
10. Institution User
11. Institution Instructor
12. Institution Learner
13. Institution SEND
14. Institution learner SEND
15. Institution Course Instructor
16. Institution Course Learner
17. Institution Course Activity
18. Institution Course Activity Instrument
19. Institution Course Activity Report
20. Institution Course Activity Report Audit


</td></tr></table>

<br><br>

 
# 1. Institution Management <a name="institution_management"></a>
---
Set of API endpoint that allows access to institution data.

  1.1 GET: [List Institution](#institution_list)<br>
  1.2 GET: [Read Institution](#institution_read)<br>
  1.3 PUT: [Update Institution](#institution_update)<br>
  1.4 PATCH: [Partial Update Institution](#institution_partial_update)<br>
<div style="text-align:right">

[[top page]](#table-of-content) 
</div>
<br>


<!--- institution_list --->
## 1.1 List Institution<a name="institution_list"></a>

API endpoint that allows access to institution data.

### Request

<table style="table-layout: fixed; width: 100%">
 <tbody>
    <tr>
        <td style="width:20%"><strong>Concept</strong></td>
        <td><strong>Data</strong></td>
    </tr>
    <tr>
        <td>HTTP Method</td>
        <td><strong><code>GET</code></strong></td>
    </tr>
    <tr>
        <td>Path</td>
        <td><span style="word-wrap: break-word">/api/v2/institution/</span></td>
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
                <td>search</td>
                <td>string </td>
                <td>A search term</td>
            </tr>
            <tr>
                <td>ordering</td>
                <td>string</td>
                <td>Which field to use when ordering the results.</td>
            </tr>
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
    Response parameters.<br>
    <table>
      <tbody>
          <tr>
            <td><strong>Name</strong></td>
            <td><strong>Type</strong></td>
            <td><strong>Comments</strong></td>
          </tr>
          <tr>
            <td><strong>count</strong><br><code>required</code></td>
            <td>integer </td>
            <td>-</td>
          </tr>
          <tr>
            <td>next</td>
            <td>string &lt;uri&gt;<br>Nullable. </td>
            <td>-</td>
          </tr>
          <tr>
            <td>previous</td>
            <td>string &lt;uri&gt;<br>Nullable. </td>
            <td>-</td>
          </tr>
          <tr>
            <td><strong>results</strong><br><code>required</code></td>
            <td>Array of objects (Institution)</td>
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

<div style="text-align:right">

[[top section]](#institution_management) [[top page]](#table-of-content) 
</div>
<br>



<!--- institution_read --->
## 1.2 Read Institution <a name="institution_read"></a>

API endpoint that allows access to institution data.


### Request
<table style="table-layout: fixed; width: 100%">
 <tbody>
    <tr>
        <td style="width:20%"><strong>Concept</strong></td>
        <td><strong>Data</strong></td>
    </tr>
    <tr>
        <td>HTTP Method</td>
        <td><strong><code>GET</code></strong></td>
    </tr>
    <tr>
        <td>Path</td>
        <td><span style="word-wrap: break-word">/api/v2/institution/{institution_id}/</span></td>
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

<div style="text-align:right">

[[top section]](#institution_management) [[top page]](#table-of-content) 
</div>
<br>

<!--- institution_update --->
## 1.3 Update Institution <a name="institution_update"></a>

API endpoint that allows access to institution data.


### Request
<table style="table-layout: fixed; width: 100%">
 <tbody>
    <tr>
        <td style="width:20%"><strong>Concept</strong></td>
        <td><strong>Data</strong></td>
    </tr>
    <tr>
        <td>HTTP Method</td>
        <td><strong><code>PUT</code></strong></td>
    </tr>
    <tr>
        <td>Path</td>
        <td><span style="word-wrap: break-word">/api/v2/institution/{institution_id}/</span></td>
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

<div style="text-align:right">

[[top section]](#institution_management) [[top page]](#table-of-content) 
</div>
<br>

<!--- institution_partial_update --->
## 1.4 Partial Update Institution <a name="institution_partial_update"></a>

API endpoint that allows access to institution data.

### Request
<table style="table-layout: fixed; width: 100%">
 <tbody>
    <tr>
        <td style="width:20%"><strong>Concept</strong></td>
        <td><strong>Data</strong></td>
    </tr>
    <tr>
        <td>HTTP Method</td>
        <td><strong><code>PATCH</code></strong></td>
    </tr>
    <tr>
        <td>Path</td>
        <td><span style="word-wrap: break-word">/api/v2/institution/{institution_id}/</span></td>
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

<div style="text-align:right">

[[top section]](#institution_management) [[top page]](#table-of-content) 
</div>
<br>



# 2. Institution VLE Management <a name="institution_vle_management"></a>
---
Set of API endpoint that allows access to Institution VLE data.

  2.1 GET: [List Institution VLE](#institution_vle_list)<br>
  2.2 POST: [Create Institution VLE](#institution_vle_create)<br>
  2.3 GET: [Read Institution VLE](#institution_vle_read)<br>
  2.4 PUT: [Update Institution VLE](#institution_vle_update)<br>
  2.5 PATCH: [Partial Update Institution VLE](#institution_vle_partial_update)<br>
  2.6 DEL: [Delete Institution VLE](#institution_vle_delete)<br>
<div style="text-align:right">

[[top page]](#table-of-content) 
</div>
<br>


<!--- institution_vle_list --->
## 2.1 List Institution VLE <a name="institution_vle_list"></a>

API endpoint that allows access to Institution VLE data.

### Request

<table style="table-layout: fixed; width: 100%">
 <tbody>
    <tr>
        <td style="width:20%"><strong>Concept</strong></td>
        <td><strong>Data</strong></td>
    </tr>
    <tr>
        <td>HTTP Method</td>
        <td><strong><code>GET</code></strong></td>
    </tr>
    <tr>
        <td>Path</td>
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/vle/</span></td>
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
                <td><strong>parent_lookup_institution_id</strong><br><code>required</code></td>
                <td>string </td>
                <td>Request path parameter.</td>
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
            </tr>
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
    Response parameters.<br>
    <table>
      <tbody>
          <tr>
            <td><strong>Name</strong></td>
            <td><strong>Type</strong></td>
            <td><strong>Comments</strong></td>
          </tr>
          <tr>
            <td><strong>count</strong><br><code>required</code></td>
            <td>integer </td>
            <td>-</td>
          </tr>
          <tr>
            <td>next</td>
            <td>string &lt;uri&gt;<br>Nullable. </td>
            <td>-</td>
          </tr>
          <tr>
            <td>previous</td>
            <td>string &lt;uri&gt;<br>Nullable. </td>
            <td>-</td>
          </tr>
          <tr>
            <td><strong>results</strong><br><code>required</code></td>
            <td>Array of objects (InstitutionVLE)</td>
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
      "type": 0,
      "lti": {},
      "name": "string",
      "credentials": "string",
      "url": "string",
      "client_id": "string"
    }
  ]
}
  ````
</details>

<div style="text-align:right">

[[top section]](#institution_vle_management) [[top page]](#table-of-content) 
</div>
<br>


<!--- institution_vle_create --->
## 2.2 Create Institution VLE <a name="institution_vle_create"></a>

API endpoint that creates Institution VLE.

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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/vle/</span></td>
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

<div style="text-align:right">

[[top section]](#institution_vle_management) [[top page]](#table-of-content) 
</div>
<br>


<!--- institution_vle_read --->
## 2.3 Read Institution VLE <a name="institution_vle_read"></a>

API endpoint that allows access to Institution VLE data.

### Request
<table style="table-layout: fixed; width: 100%">
 <tbody>
    <tr>
        <td style="width:20%"><strong>Concept</strong></td>
        <td><strong>Data</strong></td>
    </tr>
    <tr>
        <td>HTTP Method</td>
        <td><strong><code>GET</code></strong></td>
    </tr>
    <tr>
        <td>Path</td>
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/vle/{id}/</span></td>
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

<div style="text-align:right">

[[top section]](#institution_vle_management) [[top page]](#table-of-content) 
</div>
<br>

<!--- institution_vle_update --->
## 2.4 Update Institution VLE <a name="institution_vle_update"></a>

API endpoint that updates Institution VLE data.

### Request
<table style="table-layout: fixed; width: 100%">
 <tbody>
    <tr>
        <td style="width:20%"><strong>Concept</strong></td>
        <td><strong>Data</strong></td>
    </tr>
    <tr>
        <td>HTTP Method</td>
        <td><strong><code>PUT</code></strong></td>
    </tr>
    <tr>
        <td>Path</td>
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/vle/{id}/</span></td>
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

<div style="text-align:right">

[[top section]](#institution_vle_management) [[top page]](#table-of-content) 
</div>
<br>

<!--- institution_vle_partial_update --->
## 2.5 Partial Update Institution VLE <a name="institution_vle_partial_update"></a>

API endpoint that updates Institution VLE data.

### Request
<table style="table-layout: fixed; width: 100%">
 <tbody>
    <tr>
        <td style="width:20%"><strong>Concept</strong></td>
        <td><strong>Data</strong></td>
    </tr>
    <tr>
        <td>HTTP Method</td>
        <td><strong><code>PATCH</code></strong></td>
    </tr>
    <tr>
        <td>Path</td>
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/vle/{id}/</span></td>
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

<div style="text-align:right">

[[top section]](#institution_vle_management) [[top page]](#table-of-content) 
</div>
<br>

<!--- institution_vle_delete --->
## 2.6 Delete Institution VLE <a name="institution_vle_delete"></a>

API endpoint that deletes Institution VLE.


### Request
<table style="table-layout: fixed; width: 100%">
 <tbody>
    <tr>
        <td style="width:20%"><strong>Concept</strong></td>
        <td><strong>Data</strong></td>
    </tr>
    <tr>
        <td>HTTP Method</td>
        <td><strong><code>DELETE</code></strong></td>
    </tr>
    <tr>
        <td>Path</td>
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/vle/{id}/</span></td>
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

<div style="text-align:right">

[[top section]](#institution_vle_management) [[top page]](#table-of-content) 
</div>
<br>


<br><br><br><br>

----
----
----

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
  {{</ tab >}}

  {{< tab "second" >}}
  this is second tab
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


### Text and Quote

Cras at dolor eget urna varius faucibus tempus in elit. Cras a dui imperdiet, tempus metus quis, pharetra turpis. Phasellus at massa sit amet ante semper fermentum sed eget lectus. Quisque id dictum magna turpis.

> Etiam vestibulum risus vel arcu elementum eleifend. Cras at dolor eget urna varius faucibus tempus in elit. Cras a dui imperdiet

Etiam vestibulum risus vel arcu elementum eleifend. Cras at dolor eget urna varius faucibus tempus in elit. Cras a dui imperdiet, tempus metus quis, pharetra turpis. Phasellus at massa sit amet ante semper fermentum sed eget lectus. Quisque id dictum magna, et dapibus turpis.Etiam vestibulum risus vel arcu elementum eleifend. Cras at dolor eget urna varius faucibus tempus in elit. Cras a dui imperdiet, tempus metus quis, pharetra turpis. Phasellus at massa sit amet ante semper fermentum sed eget lectus. Quisque id dictum magna, et dapibus turpis.
