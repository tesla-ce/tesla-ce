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
3. [Institution Course Management](#institution_course_management)
4. [Institution Group Management](#institution_group_management)
5. [Institution Group Courses Management](#institution_group_courses_management)
6. [Institution IC Management](#institution_ic_management)
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
                <td><strong>institution_id</strong><br><code>required</code></td>
                <td>string </td>
                <td>Request path parameter.</td>
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
            <td>id</td>
            <td>integer (Id) </td>
            <td>-</td>
          </tr>
          <tr>
            <td>acronym</td>
            <td>string (Acronym)<br>non-empty </td>
            <td>-</td>
          </tr>
          <tr>
            <td>name</td>
            <td>string (Name)<br>non-empty </td>
            <td>-</td>
          </tr>
          <tr>
            <td>external_ic</td>
            <td>boolean (External IC)</td>
            <td>Informed Consent is managed externally to TeSLA.</td>
          </tr>
          <tr>
            <td>mail_domain</td>
            <td>string (Mail domain)<br><= 255 characters<br>Nullable. </td>
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
            <td>If enabled, VLE cannot create instructors.</td>
          </tr>
          <tr>
            <td>disable_vle_user_creation</td>
            <td>boolean (Disable vle user creation)</td>
            <td>If enabled, VLE cannot create institution users.</td>
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


### Responses

#### Response sample
<!--- details and summary tags, both, needed for expandable code --->
<details>
  <summary>200</summary>

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

<div style="text-align:right">

[[top section]](#institution_management) [[top page]](#table-of-content) 
</div>
<br>

<!--- institution_update --->
## 1.3 Update Institution <a name="institution_update"></a>

API endpoint that allows institution data update.


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
                <td><strong>institution_id</strong><br><code>required</code></td>
                <td>string </td>
                <td>Request path parameter.</td>
            </tr>
          <tr>
            <td>external_ic</td>
            <td>boolean (External IC)</td>
            <td>Informed Consent is managed externally to TeSLA.</td>
          </tr>
          <tr>
            <td>mail_domain</td>
            <td>string (Mail domain)<br><= 255 characters<br>Nullable. </td>
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
            <td>If enabled, VLE cannot create instructors.</td>
          </tr>
          <tr>
            <td>disable_vle_user_creation</td>
            <td>boolean (Disable vle user creation)</td>
            <td>If enabled, VLE cannot create institution users.</td>
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
    Response parameters.<br>
    <table>
      <tbody>
          <tr>
            <td><strong>Name</strong></td>
            <td><strong>Type</strong></td>
            <td><strong>Comments</strong></td>
          </tr>
          <tr>
            <td>id</td>
            <td>integer (Id) </td>
            <td>-</td>
          </tr>
          <tr>
            <td>acronym</td>
            <td>string (Acronym)<br>non-empty </td>
            <td>-</td>
          </tr>
          <tr>
            <td>name</td>
            <td>string (Name)<br>non-empty </td>
            <td>-</td>
          </tr>
          <tr>
            <td>external_ic</td>
            <td>boolean (External IC)</td>
            <td>Informed Consent is managed externally to TeSLA.</td>
          </tr>
          <tr>
            <td>mail_domain</td>
            <td>string (Mail domain)<br><= 255 characters<br>Nullable. </td>
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
            <td>If enabled, VLE cannot create instructors.</td>
          </tr>
          <tr>
            <td>disable_vle_user_creation</td>
            <td>boolean (Disable vle user creation)</td>
            <td>If enabled, VLE cannot create institution users.</td>
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

#### Request sample
`````json
{
  "external_ic": true,
  "mail_domain": "string",
  "disable_vle_learner_creation": true,
  "disable_vle_instructor_creation": true,
  "disable_vle_user_creation": true,
  "allow_learner_report": true,
  "allow_learner_audit": true,
  "allow_valid_audit": true
}
`````

### Responses

#### Response sample
<!--- details and summary tags, both, needed for expandable code --->
<details>
  <summary>200</summary>

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

<div style="text-align:right">

[[top section]](#institution_management) [[top page]](#table-of-content) 
</div>
<br>

<!--- institution_partial_update --->
## 1.4 Partial Update Institution <a name="institution_partial_update"></a>

API endpoint that allows institution data update.

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
                <td><strong>institution_id</strong><br><code>required</code></td>
                <td>string </td>
                <td>Request path parameter.</td>
            </tr>
          <tr>
            <td>external_ic</td>
            <td>boolean (External IC)</td>
            <td>Informed Consent is managed externally to TeSLA.</td>
          </tr>
          <tr>
            <td>mail_domain</td>
            <td>string (Mail domain)<br><= 255 characters<br>Nullable. </td>
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
            <td>If enabled, VLE cannot create instructors.</td>
          </tr>
          <tr>
            <td>disable_vle_user_creation</td>
            <td>boolean (Disable vle user creation)</td>
            <td>If enabled, VLE cannot create institution users.</td>
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
    Response parameters.<br>
    <table>
      <tbody>
          <tr>
            <td><strong>Name</strong></td>
            <td><strong>Type</strong></td>
            <td><strong>Comments</strong></td>
          </tr>
          <tr>
            <td>id</td>
            <td>integer (Id) </td>
            <td>-</td>
          </tr>
          <tr>
            <td>acronym</td>
            <td>string (Acronym)<br>non-empty </td>
            <td>-</td>
          </tr>
          <tr>
            <td>name</td>
            <td>string (Name)<br>non-empty </td>
            <td>-</td>
          </tr>
          <tr>
            <td>external_ic</td>
            <td>boolean (External IC)</td>
            <td>Informed Consent is managed externally to TeSLA.</td>
          </tr>
          <tr>
            <td>mail_domain</td>
            <td>string (Mail domain)<br><= 255 characters<br>Nullable. </td>
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
            <td>If enabled, VLE cannot create instructors.</td>
          </tr>
          <tr>
            <td>disable_vle_user_creation</td>
            <td>boolean (Disable vle user creation)</td>
            <td>If enabled, VLE cannot create institution users.</td>
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

#### Request sample
`````json
{
  "external_ic": true,
  "mail_domain": "string",
  "disable_vle_learner_creation": true,
  "disable_vle_instructor_creation": true,
  "disable_vle_user_creation": true,
  "allow_learner_report": true,
  "allow_learner_audit": true,
  "allow_valid_audit": true
}
`````

### Responses

#### Response sample
<!--- details and summary tags, both, needed for expandable code --->
<details>
  <summary>200</summary>

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

<div style="text-align:right">

[[top section]](#institution_management) [[top page]](#table-of-content) 
</div>
<br><br>



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
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>type</strong><br><code>required</code></td>
                <td>integer (Type)</td>
                <td>Value: 0</td>
            </tr>
            <tr>
                <td><strong>name</strong><br><code>required</code></td>
                <td>string (Name)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>url</td>
                <td>string (Url)<br>Nullable. </td>
                <td>VLE url.</td>
            </tr>
            <tr>
                <td>client_id</td>
                <td>string (Client id)<br>[1 .. 250] characters<br>Nullable.</td>
                <td>LTI 1.3 Client ID.</td>
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
                <td>id</td>
                <td>integer (ID)</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>type</strong><br><code>required</code></td>
                <td>integer (Type)</td>
                <td>Value: 0</td>
            </tr>
            <tr>
                <td>lti</td>
                <td>object (Lti)</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>name</strong><br><code>required</code></td>
                <td>string (Name)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>credentials</td>
                <td>string (Credentials)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>url</td>
                <td>string (Url)<br>Nullable. </td>
                <td>VLE url.</td>
            </tr>
            <tr>
                <td>client_id</td>
                <td>string (Client id)<br>[1 .. 250] characters<br>Nullable.</td>
                <td>LTI 1.3 Client ID.</td>
            </tr>
        </tbody>
    </table>
  {{</tab>}}
{{</tabs>}}

#### Request sample
`````json
{
  "type": 0,
  "name": "string",
  "url": "string",
  "client_id": "string"
}
`````

### Responses

#### Response sample
<!--- details and summary tags, both, needed for expandable code --->
<details>
  <summary>201</summary>

````json
{
  "id": 0,
  "type": 0,
  "lti": {},
  "name": "string",
  "credentials": "string",
  "url": "string",
  "client_id": "string"
}
````
</details>

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
                <td><strong>id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_institution_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
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
                <td>id</td>
                <td>integer (ID)</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>type</strong><br><code>required</code></td>
                <td>integer (Type)</td>
                <td>Value: 0</td>
            </tr>
            <tr>
                <td>lti</td>
                <td>object (Lti)</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>name</strong><br><code>required</code></td>
                <td>string (Name)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>credentials</td>
                <td>string (Credentials)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>url</td>
                <td>string (Url)<br>Nullable. </td>
                <td>VLE url.</td>
            </tr>
            <tr>
                <td>client_id</td>
                <td>string (Client id)<br>[1 .. 250] characters<br>Nullable.</td>
                <td>LTI 1.3 Client ID.</td>
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
  "id": 0,
  "type": 0,
  "lti": {},
  "name": "string",
  "credentials": "string",
  "url": "string",
  "client_id": "string"
}
````
</details>


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
                <td><strong>id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_institution_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>type</strong><br><code>required</code></td>
                <td>integer (Type)</td>
                <td>Value: 0</td>
            </tr>
            <tr>
                <td><strong>name</strong><br><code>required</code></td>
                <td>string (Name)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>url</td>
                <td>string (Url)<br>Nullable. </td>
                <td>VLE url.</td>
            </tr>
            <tr>
                <td>client_id</td>
                <td>string (Client id)<br>[1 .. 250] characters<br>Nullable.</td>
                <td>LTI 1.3 Client ID.</td>
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
                <td>id</td>
                <td>integer (ID)</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>type</strong><br><code>required</code></td>
                <td>integer (Type)</td>
                <td>Value: 0</td>
            </tr>
            <tr>
                <td>lti</td>
                <td>object (Lti)</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>name</strong><br><code>required</code></td>
                <td>string (Name)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>credentials</td>
                <td>string (Credentials)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>url</td>
                <td>string (Url)<br>Nullable. </td>
                <td>VLE url.</td>
            </tr>
            <tr>
                <td>client_id</td>
                <td>string (Client id)<br>[1 .. 250] characters<br>Nullable.</td>
                <td>LTI 1.3 Client ID.</td>
            </tr>
        </tbody>
    </table>
  {{</tab>}}
{{</tabs>}}

#### Request sample

````json
{
  "type": 0,
  "name": "string",
  "url": "string",
  "client_id": "string"
}
````
        
### Responses

#### Response sample
<!--- details and summary tags, both, needed for expandable code --->
<details>
  <summary>200</summary>

````json
{
  "id": 0,
  "type": 0,
  "lti": {},
  "name": "string",
  "credentials": "string",
  "url": "string",
  "client_id": "string"
}
````

</details>

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
                <td><strong>id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_institution_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>type</strong><br><code>required</code></td>
                <td>integer (Type)</td>
                <td>Value: 0</td>
            </tr>
            <tr>
                <td><strong>name</strong><br><code>required</code></td>
                <td>string (Name)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>url</td>
                <td>string (Url)<br>Nullable. </td>
                <td>VLE url.</td>
            </tr>
            <tr>
                <td>client_id</td>
                <td>string (Client id)<br>[1 .. 250] characters<br>Nullable.</td>
                <td>LTI 1.3 Client ID.</td>
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
                <td>id</td>
                <td>integer (ID)</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>type</strong><br><code>required</code></td>
                <td>integer (Type)</td>
                <td>Value: 0</td>
            </tr>
            <tr>
                <td>lti</td>
                <td>object (Lti)</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>name</strong><br><code>required</code></td>
                <td>string (Name)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>credentials</td>
                <td>string (Credentials)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>url</td>
                <td>string (Url)<br>Nullable. </td>
                <td>VLE url.</td>
            </tr>
            <tr>
                <td>client_id</td>
                <td>string (Client id)<br>[1 .. 250] characters<br>Nullable.</td>
                <td>LTI 1.3 Client ID.</td>
            </tr>
        </tbody>
    </table>
  {{</tab>}}
{{</tabs>}}

#### Request sample

  ````json
{
  "type": 0,
  "name": "string",
  "url": "string",
  "client_id": "string"
}
````

### Responses

#### Response sample
<!--- details and summary tags, both, needed for expandable code --->
<details>
  <summary>200</summary>

  ````json
{
  "id": 0,
  "type": 0,
  "lti": {},
  "name": "string",
  "credentials": "string",
  "url": "string",
  "client_id": "string"
}
````
</details>

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
                <td><strong>id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_institution_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
         </tbody>
        </table>
  {{</ tab >}}
{{</tabs>}}


### Responses

#### Response sample
<!--- details and summary tags, both, needed for expandable code --->
<details>
  <summary>204</summary>

  ````json
{
}
````
</details>

<div style="text-align:right">

[[top section]](#institution_vle_management) [[top page]](#table-of-content) 
</div>
<br><br>


# 3. Institution Course Management <a name="institution_course_management"></a>
---
Set of API endpoint that allows access to Institution Course data.

  3.1 GET: [List Institution Course](#institution_course_list)<br>
  3.3 GET: [Read Institution Course](#institution_course_read)<br>
<div style="text-align:right">

[[top page]](#table-of-content) 
</div>
<br>


<!--- institution_course_list --->
## 3.1 List Institution Course <a name="institution_course_list"></a>

API endpoint that allows Institution Courses list.

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
        <td><span style="word-wrap: break-word">https://demo.tesla-project.eu/api/v2/institution/{parent_lookup_vle__institution_id}/course/</span></td>
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
                <td><strong>parent_lookup_vle__institution_id</strong><br><code>required</code></td>
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
            <td>Array of objects (InstitutionCourse)</td>
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
      "vle": {
        "id": 0,
        "type": "string",
        "name": "string",
        "url": "string",
        "client_id": "string"
      },
      "vle_course_id": "string",
      "code": "string",
      "description": "string",
      "start": "2019-08-24T14:15:22Z",
      "end": "2019-08-24T14:15:22Z",
      "user_roles": "string",
      "created_at": "2019-08-24T14:15:22Z",
      "updated_at": "2019-08-24T14:15:22Z"
    }
  ]
}
 ````

</details>

<div style="text-align:right">

[[top section]](#institution_course_management) [[top page]](#table-of-content) 
</div>
<br>



<!--- institution_course_read --->
## 3.2 Read Institution Course <a name="institution_course_read"></a>

API endpoint that allows access to Institution Course data.

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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_vle__institution_id}/course/{id}/</span></td>
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
                <td><strong>id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_vle__institution_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
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
                <td><strong>id</strong><br><code>required</code></td>
                <td>integer (Id)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>vle</td>
                <td>object (VLE)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>vle_course_id</td>
                <td>string (VLE Course ID)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>code</td>
                <td>string (Code)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>description</td>
                <td>string (Description)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>start</td>
                <td>string &lt;date-time&gt; (Start)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>end</td>
                <td>string &lt;date-time&gt; (End)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>user_roles</td>
                <td>string (User roles)</td>
                <td>-</td>
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


### Responses

#### Response sample
<!--- details and summary tags, both, needed for expandable code --->
<details>
  <summary>200</summary>

````json
{
  "id": 0,
  "vle": {
    "id": 0,
    "type": "string",
    "name": "string",
    "url": "string",
    "client_id": "string"
  },
  "vle_course_id": "string",
  "code": "string",
  "description": "string",
  "start": "2019-08-24T14:15:22Z",
  "end": "2019-08-24T14:15:22Z",
  "user_roles": "string",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
````
</details>


<div style="text-align:right">

[[top section]](#institution_course_management) [[top page]](#table-of-content) 
</div>
<br><br>




# 4. Institution Group Management <a name="institution_group_management"></a>
---
Set of API endpoint that allows Course Groups to be viewed or edited.

  4.1 GET: [List Institution Group](#institution_group_list)<br>
  4.2 POST: [Create Institution Group](#institution_group_create)<br>
  4.3 GET: [Read Institution Group](#institution_group_read)<br>
  4.4 PUT: [Update Institution Group](#institution_group_update)<br>
  4.5 PATCH: [Partial Update Institution Group](#institution_group_partial_update)<br>
  4.6 DEL: [Delete Institution Group](#institution_group_delete)<br>
<div style="text-align:right">

[[top page]](#table-of-content) 
</div>
<br>


<!--- institution_group_list --->
## 4.1 List Institution Group <a name="institution_group_list"></a>

API endpoint that lists exisiting Course Groups.

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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/group/</span></td>
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
                <td>name</td>
                <td>string</td>
                <td>-</td>
            </tr>
            <tr>
                <td>description</td>
                <td>string</td>
                <td>-</td>
            </tr>
            <tr>
                <td>parent</td>
                <td>string</td>
                <td>-</td>
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
            <td>Array of objects (InstitutionCourseGroup)</td>
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
      "institution": {
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
      },
      "parent": 0,
      "name": "string",
      "description": "string",
      "created_at": "2019-08-24T14:15:22Z",
      "updated_at": "2019-08-24T14:15:22Z"
    }
  ]
}
 ````

</details>

<div style="text-align:right">

[[top section]](#institution_group_management) [[top page]](#table-of-content) 
</div>
<br>


<!--- institution_group_create --->
## 4.2 Create Institution Group <a name="institution_group_create"></a>

API endpoint that creates Course Group.

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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/group/</span></td>
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
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td>institution</td>
                <td>object (Institution)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>parent</td>
                <td>integer (Parent)<br>Nullable.</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>name</strong><br><code>required</code></td>
                <td>string (Name)<br>[1 .. 250] characters</td>
                <td>Group name.</td>
            </tr>
            <tr>
                <td>description</td>
                <td>string (Description)<br>Nullable. </td>
                <td>Group description.</td>
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
                <td>id</td>
                <td>integer (ID)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>institution</td>
                <td>object (Institution)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>parent</td>
                <td>integer (Parent)<br>Nullable.</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>name</strong><br><code>required</code></td>
                <td>string (Name)<br>[1 .. 250] characters</td>
                <td>Group name.</td>
            </tr>
            <tr>
                <td>description</td>
                <td>string (Description)<br>Nullable. </td>
                <td>Group description.</td>
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

#### Request sample
`````json
{
  "institution": {
    "external_ic": true,
    "mail_domain": "string",
    "disable_vle_learner_creation": true,
    "disable_vle_instructor_creation": true,
    "disable_vle_user_creation": true,
    "allow_learner_report": true,
    "allow_learner_audit": true,
    "allow_valid_audit": true
  },
  "parent": 0,
  "name": "string",
  "description": "string"
}
`````

### Responses

#### Response sample
<!--- details and summary tags, both, needed for expandable code --->
<details>
  <summary>201</summary>

````json
{
  "id": 0,
  "institution": {
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
  },
  "parent": 0,
  "name": "string",
  "description": "string",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
````
</details>

<div style="text-align:right">

[[top section]](#institution_group_management) [[top page]](#table-of-content) 
</div>
<br>


<!--- institution_group_read --->
## 4.3 Read Institution Group <a name="institution_group_read"></a>

API endpoint that allows access to a Course Group data.

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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/group/{id}/</span></td>
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
                <td><strong>id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_institution_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
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
                <td>id</td>
                <td>integer (ID)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>institution</td>
                <td>object (Institution)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>parent</td>
                <td>integer (Parent)<br>Nullable.</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>name</strong><br><code>required</code></td>
                <td>string (Name)<br>[1 .. 250] characters</td>
                <td>Group name.</td>
            </tr>
            <tr>
                <td>description</td>
                <td>string (Description)<br>Nullable. </td>
                <td>Group description.</td>
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


### Responses

#### Response sample
<!--- details and summary tags, both, needed for expandable code --->
<details>
  <summary>200</summary>

````json
{
  "id": 0,
  "institution": {
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
  },
  "parent": 0,
  "name": "string",
  "description": "string",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
````
</details>


<div style="text-align:right">

[[top section]](#institution_group_management) [[top page]](#table-of-content) 
</div>

<br>

<!--- institution_group_update --->
## 4.4 Update Institution Group <a name="institution_group_update"></a>

API endpoint that updates Course Group data.

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
            <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/group/{id}/</span></td>
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
                <td><strong>id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_institution_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td>institution</td>
                <td>object (Institution)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>parent</td>
                <td>integer (Parent)<br>Nullable.</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>name</strong><br><code>required</code></td>
                <td>string (Name)<br>[1 .. 250] characters</td>
                <td>Group name.</td>
            </tr>
            <tr>
                <td>description</td>
                <td>string (Description)<br>Nullable. </td>
                <td>Group description.</td>
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
                <td>id</td>
                <td>integer (ID)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>institution</td>
                <td>object (Institution)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>parent</td>
                <td>integer (Parent)<br>Nullable.</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>name</strong><br><code>required</code></td>
                <td>string (Name)<br>[1 .. 250] characters</td>
                <td>Group name.</td>
            </tr>
            <tr>
                <td>description</td>
                <td>string (Description)<br>Nullable. </td>
                <td>Group description.</td>
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

#### Request sample

````json
{
  "institution": {
    "external_ic": true,
    "mail_domain": "string",
    "disable_vle_learner_creation": true,
    "disable_vle_instructor_creation": true,
    "disable_vle_user_creation": true,
    "allow_learner_report": true,
    "allow_learner_audit": true,
    "allow_valid_audit": true
  },
  "parent": 0,
  "name": "string",
  "description": "string"
}
````
        
### Responses

#### Response sample
<!--- details and summary tags, both, needed for expandable code --->
<details>
  <summary>200</summary>

````json
{
  "id": 0,
  "institution": {
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
  },
  "parent": 0,
  "name": "string",
  "description": "string",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
````

</details>

<div style="text-align:right">

[[top section]](#institution_group_management) [[top page]](#table-of-content) 
</div>
<br>

<!--- institution_group_partial_update --->
## 4.5 Partial Update Institution Group <a name="institution_group_partial_update"></a>

API endpoint that updates Course Group data.

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
            <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/group/{id}/</span></td>
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
                <td><strong>id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_institution_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td>institution</td>
                <td>object (Institution)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>parent</td>
                <td>integer (Parent)<br>Nullable.</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>name</strong><br><code>required</code></td>
                <td>string (Name)<br>[1 .. 250] characters</td>
                <td>Group name.</td>
            </tr>
            <tr>
                <td>description</td>
                <td>string (Description)<br>Nullable. </td>
                <td>Group description.</td>
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
                <td>id</td>
                <td>integer (ID)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>institution</td>
                <td>object (Institution)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>parent</td>
                <td>integer (Parent)<br>Nullable.</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>name</strong><br><code>required</code></td>
                <td>string (Name)<br>[1 .. 250] characters</td>
                <td>Group name.</td>
            </tr>
            <tr>
                <td>description</td>
                <td>string (Description)<br>Nullable. </td>
                <td>Group description.</td>
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

#### Request sample

````json
{
  "institution": {
    "external_ic": true,
    "mail_domain": "string",
    "disable_vle_learner_creation": true,
    "disable_vle_instructor_creation": true,
    "disable_vle_user_creation": true,
    "allow_learner_report": true,
    "allow_learner_audit": true,
    "allow_valid_audit": true
  },
  "parent": 0,
  "name": "string",
  "description": "string"
}
````
        
### Responses

#### Response sample
<!--- details and summary tags, both, needed for expandable code --->
<details>
  <summary>200</summary>

````json
{
  "id": 0,
  "institution": {
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
  },
  "parent": 0,
  "name": "string",
  "description": "string",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
````

</details>

<div style="text-align:right">

[[top section]](#institution_group_management) [[top page]](#table-of-content) 
</div>
<br>

<!--- institution_group_delete --->
## 4.6 Delete Institution Group <a name="institution_group_delete"></a>

API endpoint that deletes Course Group.


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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/group/{id}/</span></td>
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
                <td><strong>id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_institution_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
         </tbody>
        </table>
  {{</ tab >}}
{{</tabs>}}


### Responses

#### Response sample
<!--- details and summary tags, both, needed for expandable code --->
<details>
  <summary>204</summary>

  ````json
{
}
````
</details>

<div style="text-align:right">

[[top section]](#institution_group_management) [[top page]](#table-of-content) 
</div>
<br><br>



# 5. Institution Group Courses Management <a name="institution_group_courses_management"></a>
---
Set of API endpoint that allows Courses in Course Groups to be added or deleted.

  5.1 GET: [List Institution Group Courses](#institution_group_courses_list)<br>
  5.2 POST: [Create Institution Group Courses](#institution_group_courses_create)<br>
  5.3 GET: [Read Institution Group Courses](#institution_group_courses_read)<br>
  5.4 PUT: [Update Institution Group Courses](#institution_group_courses_update)<br>
  5.5 PATCH: [Partial Update Institution Group Courses](#institution_group_courses_partial_update)<br>
  5.6 DEL: [Delete Institution Group Courses](#institution_group_courses_delete)<br>
<div style="text-align:right">

[[top page]](#table-of-content) 
</div>
<br>


<!--- institution_group_courses_list --->
## 5.1 List Institution Group Courses <a name="institution_group_courses_list"></a>

API endpoint that lists Courses in a Course Group.

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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/group/{parent_lookup_id}/course/</span></td>
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
                <td><strong>parent_lookup_id</strong><br><code>required</code></td>
                <td>string </td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_institution_id</strong><br><code>required</code></td>
                <td>string </td>
                <td>Request path parameter.</td>
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
            <td>Array of objects (InstitutionCourseGroupCourse)</td>
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
      "vle_id": 0,
      "vle_course_id": "string",
      "code": "string",
      "description": "string",
      "start": "2019-08-24T14:15:22Z",
      "end": "2019-08-24T14:15:22Z",
      "created_at": "2019-08-24T14:15:22Z",
      "updated_at": "2019-08-24T14:15:22Z"
    }
  ]
}
 ````

</details>

<div style="text-align:right">

[[top section]](#institution_group_courses_management) [[top page]](#table-of-content) 
</div>
<br>


<!--- institution_group_courses_create --->
## 5.2 Create Institution Group Courses <a name="institution_group_courses_create"></a>

API endpoint that adds Course to a Course Group.

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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/group/{parent_lookup_id}/course/</span></td>
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
                <td><strong>parent_lookup_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_institution_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>id</strong><br><code>required</code></td>
                <td>integer (Id)</td>
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
                <td><strong>id</strong><br><code>required</code></td>
                <td>integer (ID)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>vle_id</td>
                <td>integer (VLE ID)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>vle_course_id</td>
                <td>string (VLE Course ID)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>code</td>
                <td>string (Code)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>description</td>
                <td>string (Description)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>start</td>
                <td>string &lt;date-time&gt; (Start)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>end</td>
                <td>string &lt;date-time&gt; (End)</td>
                <td>-</td>
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

#### Request sample
`````json
{
  "id": 0
}
`````

### Responses

#### Response sample
<!--- details and summary tags, both, needed for expandable code --->
<details>
  <summary>201</summary>

````json
{
  "id": 0,
  "vle_id": 0,
  "vle_course_id": "string",
  "code": "string",
  "description": "string",
  "start": "2019-08-24T14:15:22Z",
  "end": "2019-08-24T14:15:22Z",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
````
</details>

<div style="text-align:right">

[[top section]](#institution_group_courses_management) [[top page]](#table-of-content) 
</div>
<br>

<!--- institution_group_courses_read --->
## 5.3 Read Institution Group Courses <a name="institution_group_courses_read"></a>

API endpoint that allows access to Course data from a Course Group.

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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/group/{parent_lookup_id}/course/{id}/</span></td>
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
                <td><strong>id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_institution_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
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
                <td><strong>id</strong><br><code>required</code></td>
                <td>integer (ID)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>vle_id</td>
                <td>integer (VLE ID)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>vle_course_id</td>
                <td>string (VLE Course ID)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>code</td>
                <td>string (Code)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>description</td>
                <td>string (Description)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>start</td>
                <td>string &lt;date-time&gt; (Start)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>end</td>
                <td>string &lt;date-time&gt; (End)</td>
                <td>-</td>
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


### Responses

#### Response sample
<!--- details and summary tags, both, needed for expandable code --->
<details>
  <summary>200</summary>

````json
{
  "id": 0,
  "vle_id": 0,
  "vle_course_id": "string",
  "code": "string",
  "description": "string",
  "start": "2019-08-24T14:15:22Z",
  "end": "2019-08-24T14:15:22Z",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
````
</details>


<div style="text-align:right">

[[top section]](#institution_group_courses_management) [[top page]](#table-of-content) 
</div>

<br>

<!--- institution_group_courses_update --->
## 5.4 Update Institution Group Courses <a name="institution_group_courses_update"></a>

API endpoint that updates Course data from a Course Group .

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
            <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/group/{parent_lookup_id}/course/{id}/</span></td>
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
                <td><strong>id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_institution_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>id</strong><br><code>required</code></td>
                <td>integer (ID)</td>
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
                <td><strong>id</strong><br><code>required</code></td>
                <td>integer (ID)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>vle_id</td>
                <td>integer (VLE ID)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>vle_course_id</td>
                <td>string (VLE Course ID)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>code</td>
                <td>string (Code)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>description</td>
                <td>string (Description)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>start</td>
                <td>string &lt;date-time&gt; (Start)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>end</td>
                <td>string &lt;date-time&gt; (End)</td>
                <td>-</td>
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

#### Request sample

````json
{
  "id": 0
}
````
        
### Responses

#### Response sample
<!--- details and summary tags, both, needed for expandable code --->
<details>
  <summary>200</summary>

````json
{
  "id": 0,
  "vle_id": 0,
  "vle_course_id": "string",
  "code": "string",
  "description": "string",
  "start": "2019-08-24T14:15:22Z",
  "end": "2019-08-24T14:15:22Z",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
````

</details>

<div style="text-align:right">

[[top section]](#institution_group_courses_management) [[top page]](#table-of-content) 
</div>
<br>

<!--- institution_group_courses_partial_update --->
## 5.5 Partial Update Institution Group Courses <a name="institution_group_courses_partial_update"></a>

API endpoint that updates Course data from a Course Group .

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
            <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/group/{parent_lookup_id}/course/{id}/</span></td>
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
                <td><strong>id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_institution_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>id</strong><br><code>required</code></td>
                <td>integer (ID)</td>
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
                <td><strong>id</strong><br><code>required</code></td>
                <td>integer (ID)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>vle_id</td>
                <td>integer (VLE ID)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>vle_course_id</td>
                <td>string (VLE Course ID)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>code</td>
                <td>string (Code)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>description</td>
                <td>string (Description)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>start</td>
                <td>string &lt;date-time&gt; (Start)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>end</td>
                <td>string &lt;date-time&gt; (End)</td>
                <td>-</td>
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

#### Request sample

````json
{
  "id": 0
}
````
        
### Responses

#### Response sample
<!--- details and summary tags, both, needed for expandable code --->
<details>
  <summary>200</summary>

````json
{
  "id": 0,
  "vle_id": 0,
  "vle_course_id": "string",
  "code": "string",
  "description": "string",
  "start": "2019-08-24T14:15:22Z",
  "end": "2019-08-24T14:15:22Z",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
````

</details>

<div style="text-align:right">

[[top section]](#institution_group_courses_management) [[top page]](#table-of-content) 
</div>
<br>

<!--- institution_group_courses_delete --->
## 5.6 Delete Institution Group Courses <a name="institution_group_courses_delete"></a>

API endpoint that deletes course in a Course Group.


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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/group/{parent_lookup_id}/course/{id}/</span></td>
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
                <td><strong>id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_institution_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
         </tbody>
        </table>
  {{</ tab >}}
{{</tabs>}}


### Responses

#### Response sample
<!--- details and summary tags, both, needed for expandable code --->
<details>
  <summary>204</summary>

  ````json
{
}
````
</details>

<div style="text-align:right">

[[top section]](#institution_group_courses_management) [[top page]](#table-of-content) 
</div>
<br><br>



# 6. Institution IC Management <a name="institution_ic_management"></a>
---
Set of API endpoint that allows Informed Consent to be viewed or edited.


  6.1 GET: [List Institution IC](#institution_ic_list)<br>
  6.2 POST: [Create Institution IC](#institution_ic_create)<br>
  6.3 GET: [Current Institution IC](#institution_ic_current)<br>
  6.4 GET: [Read Institution IC](#institution_ic_read)<br>
  6.5 PUT: [Update Institution IC](#institution_ic_update)<br>
  6.6 PATCH: [Partial Update Institution IC](#institution_ic_partial_update)<br>
  6.7 DEL: [Delete Institution IC](#institution_ic_delete)<br>
<div style="text-align:right">

[[top page]](#table-of-content) 
</div>
<br>


<!--- institution_ic_list --->
## 6.1 List Institution IC <a name="institution_ic_list"></a>

API endpoint that lists Informed Consent in an Institution.


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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/ic/</span></td>
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
                <td>string</td>
                <td>A search term.</td>
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
            <td>Array of objects (InstitutionInformedConsent)</td>
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
      "institution": {
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
      },
      "version": "string",
      "valid_from": "2019-08-24T14:15:22Z",
      "created_at": "2019-08-24T14:15:22Z",
      "updated_at": "2019-08-24T14:15:22Z"
    }
  ]
}
 ````

</details>

<div style="text-align:right">

[[top section]](#institution_ic_management) [[top page]](#table-of-content) 
</div>
<br>


<!--- institution_ic_create --->
## 6.2 Create Institution IC <a name="institution_ic_create"></a>

API endpoint that adds Informed Consent to an Institution.

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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/ic/</span></td>
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
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td>institution</td>
                <td>object (Institution)</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>version</strong><br><code>required</code></td>
                <td>string (Version)<br>[1 .. 250] characters</td>
                <td>Informed Consent version.</td>
            </tr>
            <tr>
                <td><strong>valid_from</strong><br><code>required</code></td>
                <td>string &lt;date-time&gt; (Valid from)</td>
                <td>Informed Consent valid from.</td>
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
                <td>id</td>
                <td>integer (ID)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>institution</td>
                <td>object (Institution)</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>version</strong><br><code>required</code></td>
                <td>string (Version)<br>[1 .. 250] characters</td>
                <td>Informed Consent version.</td>
            </tr>
            <tr>
                <td><strong>valid_from</strong><br><code>required</code></td>
                <td>string &lt;date-time&gt; (Valid from)</td>
                <td>Informed Consent valid from.</td>
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

#### Request sample
`````json
{
  "institution": {
    "external_ic": true,
    "mail_domain": "string",
    "disable_vle_learner_creation": true,
    "disable_vle_instructor_creation": true,
    "disable_vle_user_creation": true,
    "allow_learner_report": true,
    "allow_learner_audit": true,
    "allow_valid_audit": true
  },
  "version": "string",
  "valid_from": "2019-08-24T14:15:22Z"
}
`````

### Responses

#### Response sample
<!--- details and summary tags, both, needed for expandable code --->
<details>
  <summary>201</summary>

````json
{
  "id": 0,
  "institution": {
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
  },
  "version": "string",
  "valid_from": "2019-08-24T14:15:22Z",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
````
</details>

<div style="text-align:right">

[[top section]](#institution_ic_management) [[top page]](#table-of-content) 
</div>
<br>

<!--- institution_ic_current --->
## 6.3 Current Institution IC <a name="institution_ic_current"></a>

API endpoint that retrieves the current Informed Consent.

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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/ic/current/</span></td>
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
                <td>string</td>
                <td>Request path parameter.</td>
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
            <td>Array of objects (InstitutionInformedConsent)</td>
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
      "institution": {
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
      },
      "version": "string",
      "valid_from": "2019-08-24T14:15:22Z",
      "created_at": "2019-08-24T14:15:22Z",
      "updated_at": "2019-08-24T14:15:22Z"
    }
  ]
}
 ````

</details>

<div style="text-align:right">

[[top section]](#institution_ic_management) [[top page]](#table-of-content) 
</div>
<br>


<!--- institution_ic_read --->
## 6.4 Read Institution IC <a name="institution_ic_read"></a>

API endpoint for reading an Informed Consent.

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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/ic/{id}/</span></td>
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
                <td><strong>id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_institution_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
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
                <td>id</td>
                <td>integer (ID)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>institution</td>
                <td>object (Institution)</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>version</strong><br><code>required</code></td>
                <td>string (Version)<br>[1 .. 250] characters</td>
                <td>Informed Consent version.</td>
            </tr>
            <tr>
                <td><strong>valid_from</strong><br><code>required</code></td>
                <td>string &lt;date-time&gt; (Valid from)</td>
                <td>Informed Consent valid from.</td>
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


### Responses

#### Response sample
<!--- details and summary tags, both, needed for expandable code --->
<details>
  <summary>200</summary>

````json
{
  "id": 0,
  "institution": {
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
  },
  "version": "string",
  "valid_from": "2019-08-24T14:15:22Z",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
````
</details>


<div style="text-align:right">

[[top section]](#institution_ic_management) [[top page]](#table-of-content) 
</div>

<br>

<!--- institution_ic_update --->
## 6.5 Update Institution IC <a name="institution_ic_update"></a>

API endpoint that updates Informed Consent data in an Institution.

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
            <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/ic/{id}/</span></td>
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
                <td><strong>id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_institution_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td>institution</td>
                <td>object (Institution)</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>version</strong><br><code>required</code></td>
                <td>string (Version)<br>[1 .. 250] characters</td>
                <td>Informed Consent version.</td>
            </tr>
            <tr>
                <td><strong>valid_from</strong><br><code>required</code></td>
                <td>string &lt;date-time&gt; (Valid from)</td>
                <td>Informed Consent valid from.</td>
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
                <td>id</td>
                <td>integer (ID)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>institution</td>
                <td>object (Institution)</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>version</strong><br><code>required</code></td>
                <td>string (Version)<br>[1 .. 250] characters</td>
                <td>Informed Consent version.</td>
            </tr>
            <tr>
                <td><strong>valid_from</strong><br><code>required</code></td>
                <td>string &lt;date-time&gt; (Valid from)</td>
                <td>Informed Consent valid from.</td>
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

#### Request sample

````json
{
  "institution": {
    "external_ic": true,
    "mail_domain": "string",
    "disable_vle_learner_creation": true,
    "disable_vle_instructor_creation": true,
    "disable_vle_user_creation": true,
    "allow_learner_report": true,
    "allow_learner_audit": true,
    "allow_valid_audit": true
  },
  "version": "string",
  "valid_from": "2019-08-24T14:15:22Z"
}
````
        
### Responses

#### Response sample
<!--- details and summary tags, both, needed for expandable code --->
<details>
  <summary>200</summary>

````json
{
  "id": 0,
  "institution": {
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
  },
  "version": "string",
  "valid_from": "2019-08-24T14:15:22Z",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
````

</details>

<div style="text-align:right">

[[top section]](#institution_ic_management) [[top page]](#table-of-content) 
</div>
<br>

<!--- institution_ic_partial_update --->
## 6.6 Partial Update Institution IC <a name="institution_ic_partial_update"></a>

API endpoint that removes an Informed Consent from an Institution.

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
            <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/ic/{id}/</span></td>
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
                <td><strong>id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_institution_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td>institution</td>
                <td>object (Institution)</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>version</strong><br><code>required</code></td>
                <td>string (Version)<br>[1 .. 250] characters</td>
                <td>Informed Consent version.</td>
            </tr>
            <tr>
                <td><strong>valid_from</strong><br><code>required</code></td>
                <td>string &lt;date-time&gt; (Valid from)</td>
                <td>Informed Consent valid from.</td>
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
                <td>id</td>
                <td>integer (ID)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>institution</td>
                <td>object (Institution)</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>version</strong><br><code>required</code></td>
                <td>string (Version)<br>[1 .. 250] characters</td>
                <td>Informed Consent version.</td>
            </tr>
            <tr>
                <td><strong>valid_from</strong><br><code>required</code></td>
                <td>string &lt;date-time&gt; (Valid from)</td>
                <td>Informed Consent valid from.</td>
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

#### Request sample

````json
{
  "institution": {
    "external_ic": true,
    "mail_domain": "string",
    "disable_vle_learner_creation": true,
    "disable_vle_instructor_creation": true,
    "disable_vle_user_creation": true,
    "allow_learner_report": true,
    "allow_learner_audit": true,
    "allow_valid_audit": true
  },
  "version": "string",
  "valid_from": "2019-08-24T14:15:22Z"
}
````
        
### Responses

#### Response sample
<!--- details and summary tags, both, needed for expandable code --->
<details>
  <summary>200</summary>

````json
{
  "id": 0,
  "institution": {
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
  },
  "version": "string",
  "valid_from": "2019-08-24T14:15:22Z",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
````

</details>

<div style="text-align:right">

[[top section]](#institution_ic_management) [[top page]](#table-of-content) 
</div>
<br>

<!--- institution_ic_delete --->
## 6.7 Delete Institution IC <a name="institution_ic_delete"></a>

API endpoint that deletes course in a Course Group.


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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/ic/{id}/</span></td>
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
                <td><strong>id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_institution_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
         </tbody>
        </table>
  {{</ tab >}}
{{</tabs>}}


### Responses

#### Response sample
<!--- details and summary tags, both, needed for expandable code --->
<details>
  <summary>204</summary>

  ````json
{
}
````
</details>

<div style="text-align:right">

[[top section]](#institution_ic_management) [[top page]](#table-of-content) 
</div>
<br><br>


888
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
