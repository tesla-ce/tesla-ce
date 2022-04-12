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

# Table of Contents

1. [Institution Management](#institution_management)
2. [Institution VLE Management](#institution_vle_management)
3. [Institution Course Management](#institution_course_management)
4. [Institution Group Management](#institution_group_management)
5. [Institution Group Courses Management](#institution_group_course_management)
6. [Institution IC Management](#institution_ic_management)
7. [Institution IC Document Management](#institution_ic_document_management)
8. [Institution Instrument Management](#institution_instrument_management)
9. [Institution UI Management](#institution_ui_management)
10. [Institution User Management](#institution_user_management)
11. [Institution Instructor Managament](#institution_instructor_management)
12. [Institution Learner Management](#institution_learner_management)
13. [Institution SEND Management](#institution_send_management)
14. [Institution learner SEND Management](#institution_learner_send_management)
15. [Institution Course Instructor Management](#institution_course_instructor_management)
16. [Institution Course Learner Management](#institution_course_learner_management)
17. [Institution Course Activity Management](#institution_course_activity_management)
18. [Institution Course Activity Instrument Management](#institution_course_activity_instrument_management)
19. [Institution Course Activity Report Management](#institution_course_activity_report_management)
20. [Institution Course Activity Report Request Management](#institution_course_activity_report_request_management)
21. [Institution Course Activity Report Audit Management](#institution_course_activity_report_audit_management)


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

[[top page]](#table-of-contents) 
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

[[top section]](#institution_management) [[top page]](#table-of-contents) 
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

[[top section]](#institution_management) [[top page]](#table-of-contents) 
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

[[top section]](#institution_management) [[top page]](#table-of-contents) 
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

[[top section]](#institution_management) [[top page]](#table-of-contents) 
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

[[top page]](#table-of-contents) 
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

[[top section]](#institution_vle_management) [[top page]](#table-of-contents) 
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

[[top section]](#institution_vle_management) [[top page]](#table-of-contents) 
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

[[top section]](#institution_vle_management) [[top page]](#table-of-contents) 
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

[[top section]](#institution_vle_management) [[top page]](#table-of-contents) 
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

[[top section]](#institution_vle_management) [[top page]](#table-of-contents) 
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

[[top section]](#institution_vle_management) [[top page]](#table-of-contents) 
</div>
<br><br>


# 3. Institution Course Management <a name="institution_course_management"></a>
---
Set of API endpoint that allows access to Institution Course data.

  3.1 GET: [List Institution Course](#institution_course_list)<br>
  3.3 GET: [Read Institution Course](#institution_course_read)<br>
<div style="text-align:right">

[[top page]](#table-of-contents) 
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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_vle__institution_id}/course/</span></td>
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

[[top section]](#institution_course_management) [[top page]](#table-of-contents) 
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

[[top section]](#institution_course_management) [[top page]](#table-of-contents) 
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

[[top page]](#table-of-contents) 
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

[[top section]](#institution_group_management) [[top page]](#table-of-contents) 
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

[[top section]](#institution_group_management) [[top page]](#table-of-contents) 
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

[[top section]](#institution_group_management) [[top page]](#table-of-contents) 
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

[[top section]](#institution_group_management) [[top page]](#table-of-contents) 
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

[[top section]](#institution_group_management) [[top page]](#table-of-contents) 
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

[[top section]](#institution_group_management) [[top page]](#table-of-contents) 
</div>
<br><br>



# 5. Institution Group Courses Management <a name="institution_group_course_management"></a>
---
Set of API endpoint that allows Courses in Course Groups to be added or deleted.

  5.1 GET: [List Institution Group Courses](#institution_group_course_list)<br>
  5.2 POST: [Create Institution Group Courses](#institution_group_course_create)<br>
  5.3 GET: [Read Institution Group Courses](#institution_group_course_read)<br>
  5.4 PUT: [Update Institution Group Courses](#institution_group_course_update)<br>
  5.5 PATCH: [Partial Update Institution Group Courses](#institution_group_course_partial_update)<br>
  5.6 DEL: [Delete Institution Group Courses](#institution_group_course_delete)<br>
<div style="text-align:right">

[[top page]](#table-of-contents) 
</div>
<br>


<!--- institution_group_course_list --->
## 5.1 List Institution Group Courses <a name="institution_group_course_list"></a>

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

[[top section]](#institution_group_course_management) [[top page]](#table-of-contents) 
</div>
<br>


<!--- institution_group_course_create --->
## 5.2 Create Institution Group Courses <a name="institution_group_course_create"></a>

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

[[top section]](#institution_group_course_management) [[top page]](#table-of-contents) 
</div>
<br>

<!--- institution_group_course_read --->
## 5.3 Read Institution Group Courses <a name="institution_group_course_read"></a>

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

[[top section]](#institution_group_course_management) [[top page]](#table-of-contents) 
</div>

<br>

<!--- institution_group_course_update --->
## 5.4 Update Institution Group Courses <a name="institution_group_course_update"></a>

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

[[top section]](#institution_group_course_management) [[top page]](#table-of-contents) 
</div>
<br>

<!--- institution_group_course_partial_update --->
## 5.5 Partial Update Institution Group Courses <a name="institution_group_course_partial_update"></a>

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

[[top section]](#institution_group_course_management) [[top page]](#table-of-contents) 
</div>
<br>

<!--- institution_group_course_delete --->
## 5.6 Delete Institution Group Courses <a name="institution_group_course_delete"></a>

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

[[top section]](#institution_group_course_management) [[top page]](#table-of-contents) 
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

[[top page]](#table-of-contents) 
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

[[top section]](#institution_ic_management) [[top page]](#table-of-contents) 
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

[[top section]](#institution_ic_management) [[top page]](#table-of-contents) 
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

[[top section]](#institution_ic_management) [[top page]](#table-of-contents) 
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

[[top section]](#institution_ic_management) [[top page]](#table-of-contents) 
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

[[top section]](#institution_ic_management) [[top page]](#table-of-contents) 
</div>
<br>

<!--- institution_ic_partial_update --->
## 6.6 Partial Update Institution IC <a name="institution_ic_partial_update"></a>

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

[[top section]](#institution_ic_management) [[top page]](#table-of-contents) 
</div>
<br>

<!--- institution_ic_delete --->
## 6.7 Delete Institution IC <a name="institution_ic_delete"></a>

API endpoint that deletes Informed Consent from an Institution.


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

[[top section]](#institution_ic_management) [[top page]](#table-of-contents) 
</div>
<br><br>



# 7. Institution IC Document Management <a name="institution_ic_document_management"></a>
---
Set of API endpoint that allows Informed Consent Document to be viewed or edited.


  7.1 GET: [List Institution IC Document](#institution_ic_document_list)<br>
  7.2 POST: [Create Institution IC Document](#institution_ic_document_create)<br>
  7.3 GET: [Read Institution IC Document](#institution_ic_document_read)<br>
  7.4 PUT: [Update Institution IC Document](#institution_ic_document_update)<br>
  7.5 PATCH: [Partial Update Institution IC Document](#institution_ic_document_partial_update)<br>
  7.6 DEL: [Delete Institution IC Document](#institution_ic_document_delete)<br>
<div style="text-align:right">

[[top page]](#table-of-contents) 
</div>
<br>


<!--- institution_ic_document_list --->
## 7.1 List Institution IC Document <a name="institution_ic_document_list"></a>

API endpoint that lists Informed Consent Documents.


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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/ic/{parent_lookup_informed_consent_id}/document/</span></td>
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
                <td><strong>parent_lookup_informed_consent_id</strong><br><code>required</code></td>
                <td>string </td>
                <td>Request path parameter.</td>
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
      "consent": {
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
      },
      "language": "string",
      "html": "string",
      "pdf": "http://example.com",
      "created_at": "2019-08-24T14:15:22Z",
      "updated_at": "2019-08-24T14:15:22Z"
    }
  ]
}
 ````

</details>

<div style="text-align:right">

[[top section]](#institution_ic_document_management) [[top page]](#table-of-contents) 
</div>
<br>


<!--- institution_ic_document_create --->
## 7.2 Create Institution IC Document <a name="institution_ic_document_create"></a>

API endpoint that creates an Informed Consent Document.

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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/ic/{parent_lookup_informed_consent_id}/document/</span></td>
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
                <td><strong>parent_lookup_informed_consent_id</strong><br><code>required</code></td>
                <td>string </td>
                <td>Request path parameter.</td>
            </tr>             
            <tr>
                <td><strong>parent_lookup_institution_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td>consent</td>
                <td>object (InstitutionInformedConsent)</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>language</strong><br><code>required</code></td>
                <td>string (Language)<br>[1 .. 30] characters</td>
                <td>-</td>
            </tr>
            <tr>
                <td>html</td>
                <td>string (Html)<br>Nullable.</td>
                <td>HMTL version of IC.</td>
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
                <td>consent</td>
                <td>object (InstitutionInformedConsent)</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>language</strong><br><code>required</code></td>
                <td>string (Language)<br>[1 .. 30] characters</td>
                <td>-</td>
            </tr>
            <tr>
                <td>html</td>
                <td>string (Html)<br>Nullable.</td>
                <td>HMTL version of IC.</td>
            </tr>
            <tr>
                <td>pdf</td>
                <td>string &lt;uri&gt; (Pdf)<br>Nullable.</td>
                <td>PDF version of IC.</td>
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
  "consent": {
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
  },
  "language": "string",
  "html": "string"
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
"consent": {
"id": 0,
"institution": {},
"version": "string",
"valid_from": "2019-08-24T14:15:22Z",
"created_at": "2019-08-24T14:15:22Z",
"updated_at": "2019-08-24T14:15:22Z"
},
"language": "string",
"html": "string",
"pdf": "http://example.com",
"created_at": "2019-08-24T14:15:22Z",
"updated_at": "2019-08-24T14:15:22Z"
}
````
</details>

<div style="text-align:right">

[[top section]](#institution_ic_document_management) [[top page]](#table-of-contents) 
</div>
<br>


<!--- institution_ic_document_read --->
## 7.3 Read Institution IC Document <a name="institution_ic_document_read"></a>

API endpoint for reading an Informed Consent Document.

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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/ic/{parent_lookup_informed_consent_id}/document/{language}/</span></td>
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
                <td><strong>language</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_informed_consent_id</strong><br><code>required</code></td>
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
                <td>consent</td>
                <td>object (InstitutionInformedConsent)</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>language</strong><br><code>required</code></td>
                <td>string (Language)<br>[1 .. 30] characters</td>
                <td>-</td>
            </tr>
            <tr>
                <td>html</td>
                <td>string (Html)<br>Nullable.</td>
                <td>HMTL version of IC.</td>
            </tr>
            <tr>
                <td>pdf</td>
                <td>string &lt;uri&gt; (Pdf)<br>Nullable.</td>
                <td>PDF version of IC.</td>
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
  "consent": {
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
  },
  "language": "string",
  "html": "string",
  "pdf": "http://example.com",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
````
</details>


<div style="text-align:right">

[[top section]](#institution_ic_document_management) [[top page]](#table-of-contents) 
</div>

<br>

<!--- institution_ic_document_update --->
## 7.4 Update Institution IC Document <a name="institution_ic_document_update"></a>

API endpoint that updates Informed Consent Document.

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
            <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/ic/{parent_lookup_informed_consent_id}/document/{language}/</span></td>
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
                <td><strong>language</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_informed_consent_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_institution_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td>consent</td>
                <td>object (InstitutionInformedConsent)</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>language</strong><br><code>required</code></td>
                <td>string (Language)<br>[1 .. 30] characters</td>
                <td>-</td>
            </tr>
            <tr>
                <td>html</td>
                <td>string (Html)<br>Nullable.</td>
                <td>HMTL version of IC.</td>
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
                <td>consent</td>
                <td>object (InstitutionInformedConsent)</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>language</strong><br><code>required</code></td>
                <td>string (Language)<br>[1 .. 30] characters</td>
                <td>-</td>
            </tr>
            <tr>
                <td>html</td>
                <td>string (Html)<br>Nullable.</td>
                <td>HMTL version of IC.</td>
            </tr>
            <tr>
                <td>pdf</td>
                <td>string &lt;uri&gt; (Pdf)<br>Nullable.</td>
                <td>PDF version of IC.</td>
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
  "consent": {
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
  },
  "language": "string",
  "html": "string"
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
  "consent": {
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
  },
  "language": "string",
  "html": "string",
  "pdf": "http://example.com",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
````

</details>

<div style="text-align:right">

[[top section]](#institution_ic_document_management) [[top page]](#table-of-contents) 
</div>
<br>

<!--- institution_ic_document_partial_update --->
## 7.5 Partial Update Institution IC Document <a name="institution_ic_document_partial_update"></a>

API endpoint that updates Informed Consent Document.

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
            <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/ic/{parent_lookup_informed_consent_id}/document/{language}/</span></td>
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
                <td><strong>language</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_informed_consent_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_institution_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td>consent</td>
                <td>object (InstitutionInformedConsent)</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>language</strong><br><code>required</code></td>
                <td>string (Language)<br>[1 .. 30] characters</td>
                <td>-</td>
            </tr>
            <tr>
                <td>html</td>
                <td>string (Html)<br>Nullable.</td>
                <td>HMTL version of IC.</td>
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
                <td>consent</td>
                <td>object (InstitutionInformedConsent)</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>language</strong><br><code>required</code></td>
                <td>string (Language)<br>[1 .. 30] characters</td>
                <td>-</td>
            </tr>
            <tr>
                <td>html</td>
                <td>string (Html)<br>Nullable.</td>
                <td>HMTL version of IC.</td>
            </tr>
            <tr>
                <td>pdf</td>
                <td>string &lt;uri&gt; (Pdf)<br>Nullable.</td>
                <td>PDF version of IC.</td>
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
  "consent": {
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
  },
  "language": "string",
  "html": "string"
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
  "consent": {
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
  },
  "language": "string",
  "html": "string",
  "pdf": "http://example.com",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
````

</details>

<div style="text-align:right">

[[top section]](#institution_ic_document_management) [[top page]](#table-of-contents) 
</div>
<br>

<!--- institution_ic_document_delete --->
## 7.6 Delete Institution IC Document <a name="institution_ic_document_delete"></a>

API endpoint that deletes Informed Consent Document.


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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/ic/{parent_lookup_informed_consent_id}/document/{language}/</span></td>
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
                <td><strong>language</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_informed_consent_id</strong><br><code>required</code></td>
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

[[top section]](#institution_ic_document_management) [[top page]](#table-of-contents) 
</div>
<br><br>




# 8. Institution Instrument Management <a name="institution_instrument_management"></a>
---
Set of API endpoint that allows read Instrument data.

  8.1 GET: [List Institution Instrument](#institution_instrument_list)<br>
  8.2 GET: [Read Institution Instrument](#institution_instrument_read)<br>
<div style="text-align:right">

[[top page]](#table-of-contents) 
</div>
<br>


<!--- institution_instrument_list --->
## 8.1 List Institution Instrument<a name="institution_instrument_list"></a>

API endpoint that lists Institution Instruments.

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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/instrument/</span></td>
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

<div style="text-align:right">

[[top section]](#institution_instrument_management) [[top page]](#table-of-contents) 
</div>
<br>



<!--- institution_instrument_read --->
## 8.2 Read Institution Instrument <a name="institution_instrument_read"></a>

API endpoint that allows read Instrument data.

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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/instrument/{id}/</span></td>
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
                <td>options_schema</td>
                <td>object (Options schema)<br>Nullable.</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>name</strong><br><code>required</code></td>
                <td>string (Name)<br>[1 .. 250] characters</td>
                <td>Instrument name.</td>
            </tr>
            <tr>
                <td><strong>acronym</strong><br><code>required</code></td>
                <td>string (Acronym)<br>[1 .. 30] characters</td>
                <td>Instrument Acronym.</td>
            </tr>
            <tr>
                <td><strong>queue</strong><br><code>required</code></td>
                <td>string (Queue)<br>non-empty</td>
                <td>Queue this instrument listens to.</td>
            </tr>
            <tr>
                <td>enabled</td>
                <td>boolean (Enabled)</td>
                <td>The instrument is enabled.</td>
            </tr>
            <tr>
                <td><requires_enrolment</td>
                <td>boolean (Requires enrolment)</td>
                <td>Whether this instrument requires enrolment.</td>
            </tr>
            <tr>
                <td>description</td>
                <td>string (Description)<br>Nullable.</td>
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
                <td>created_at</td>
                <td>string &lt;date-time&gt; (Created at)</td>
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


<div style="text-align:right">

[[top section]](#institution_instrument_management) [[top page]](#table-of-contents) 
</div>
<br><br>



# 9. Institution UI Management <a name="institution_ui_management"></a>
---
Set of API endpoint that allows Institution UI Options to be viewed or edited.

  9.1 GET: [List Institution UI](#institution_ui_list)<br>
  9.2 POST: [Create Institution UI](#institution_ui_create)<br>
  9.3 GET: [Read Institution UI](#institution_ui_read)<br>
  9.4 PUT: [Update Institution UI](#institution_ui_update)<br>
  9.5 PATCH: [Partial Update Institution UI](#institution_ui_partial_update)<br>
  9.6 DEL: [Delete Institution UI](#institution_ui_delete)<br>
<div style="text-align:right">

[[top page]](#table-of-contents) 
</div>
<br>


<!--- institution_ui_list --->
## 9.1 List Institution UI <a name="institution_ui_list"></a>

API endpoint that allows access to Institution UI data.

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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/ui/</span></td>
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
            <td>Array of objects (InstitutionUIOption)</td>
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
      "route": "string",
      "enabled": true,
      "roles": "string",
      "user": "string",
      "is_global": "string"
    }
  ]
}
 ````

</details>

<div style="text-align:right">

[[top section]](#institution_ui_management) [[top page]](#table-of-contents) 
</div>
<br>


<!--- institution_ui_create --->
## 9.2 Create Institution UI <a name="institution_ui_create"></a>

API endpoint that creates Institution UI.

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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/ui/</span></td>
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
                <td><strong>route</strong><br><code>required</code></td>
                <td>string (Route)<br>[1 .. 250] characters</td>
                <td>Affected Route.</td>
            </tr>
            <tr>
                <td>enabled</td>
                <td>boolean (Enabled)</td>
                <td>Status.</td>
            </tr>
            <tr>
                <td>user</td>
                <td>string (User)<br>Nullable. </td>
                <td>Affected User.</td>
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
                <td><strong>route</strong><br><code>required</code></td>
                <td>string (Route)<br>[1 .. 250] characters</td>
                <td>Affected Route.</td>
            </tr>
            <tr>
                <td>enabled</td>
                <td>boolean (Enabled)</td>
                <td>Status.</td>
            </tr>
            <tr>
                <td>roles</td>
                <td>string (Roles)</td>
                <td>Affected User.</td>
            </tr>
            <tr>
                <td>user</td>
                <td>string (User)<br>Nullable. </td>
                <td>Affected User.</td>
            </tr>
            <tr>
                <td>is_global</td>
                <td>string (Is global)</td>
                <td>-</td>
            </tr>
        </tbody>
    </table>
  {{</tab>}}
{{</tabs>}}

#### Request sample
`````json
{
  "route": "string",
  "enabled": true,
  "user": "string"
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
  "route": "string",
  "enabled": true,
  "roles": "string",
  "user": "string",
  "is_global": "string"
}
````
</details>

<div style="text-align:right">

[[top section]](#institution_ui_management) [[top page]](#table-of-contents) 
</div>
<br>


<!--- institution_ui_read --->
## 9.3 Read Institution UI <a name="institution_ui_read"></a>

API endpoint that allows access to Institution UI data.

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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/ui/{id}/</span></td>
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
                <td><strong>route</strong><br><code>required</code></td>
                <td>string (Route)<br>[1 .. 250] characters</td>
                <td>Affected Route.</td>
            </tr>
            <tr>
                <td>enabled</td>
                <td>boolean (Enabled)</td>
                <td>Status.</td>
            </tr>
            <tr>
                <td>roles</td>
                <td>string (Roles)</td>
                <td>Affected User.</td>
            </tr>
            <tr>
                <td>user</td>
                <td>string (User)<br>Nullable. </td>
                <td>Affected User.</td>
            </tr>
            <tr>
                <td>is_global</td>
                <td>string (Is global)</td>
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
  "route": "string",
  "enabled": true,
  "roles": "string",
  "user": "string",
  "is_global": "string"
}
````
</details>


<div style="text-align:right">

[[top section]](#institution_ui_management) [[top page]](#table-of-contents) 
</div>

<br>

<!--- institution_ui_update --->
## 9.4 Update Institution UI <a name="institution_ui_update"></a>

API endpoint that updates Institution UI data.

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
            <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/ui/{id}/</span></td>
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
                <td><strong>route</strong><br><code>required</code></td>
                <td>string (Route)<br>[1 .. 250] characters</td>
                <td>Affected Route.</td>
            </tr>
            <tr>
                <td>enabled</td>
                <td>boolean (Enabled)</td>
                <td>Status.</td>
            </tr>
            <tr>
                <td>user</td>
                <td>string (User)<br>Nullable. </td>
                <td>Affected User.</td>
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
                <td><strong>route</strong><br><code>required</code></td>
                <td>string (Route)<br>[1 .. 250] characters</td>
                <td>Affected Route.</td>
            </tr>
            <tr>
                <td>enabled</td>
                <td>boolean (Enabled)</td>
                <td>Status.</td>
            </tr>
            <tr>
                <td>roles</td>
                <td>string (Roles)</td>
                <td>Affected User.</td>
            </tr>
            <tr>
                <td>user</td>
                <td>string (User)<br>Nullable. </td>
                <td>Affected User.</td>
            </tr>
            <tr>
                <td>is_global</td>
                <td>string (Is global)</td>
                <td>-</td>
            </tr>
        </tbody>
    </table>
  {{</tab>}}
{{</tabs>}}

#### Request sample

````json
{
  "route": "string",
  "enabled": true,
  "user": "string"
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
  "route": "string",
  "enabled": true,
  "roles": "string",
  "user": "string",
  "is_global": "string"
}
````

</details>

<div style="text-align:right">

[[top section]](#institution_ui_management) [[top page]](#table-of-contents) 
</div>
<br>

<!--- institution_ui_partial_update --->
## 9.5 Partial Update Institution UI <a name="institution_ui_partial_update"></a>

API endpoint that updates Institution UI data.

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
            <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/ui/{id}/</span></td>
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
                <td><strong>route</strong><br><code>required</code></td>
                <td>string (Route)<br>[1 .. 250] characters</td>
                <td>Affected Route.</td>
            </tr>
            <tr>
                <td>enabled</td>
                <td>boolean (Enabled)</td>
                <td>Status.</td>
            </tr>
            <tr>
                <td>user</td>
                <td>string (User)<br>Nullable. </td>
                <td>Affected User.</td>
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
                <td><strong>route</strong><br><code>required</code></td>
                <td>string (Route)<br>[1 .. 250] characters</td>
                <td>Affected Route.</td>
            </tr>
            <tr>
                <td>enabled</td>
                <td>boolean (Enabled)</td>
                <td>Status.</td>
            </tr>
            <tr>
                <td>roles</td>
                <td>string (Roles)</td>
                <td>Affected User.</td>
            </tr>
            <tr>
                <td>user</td>
                <td>string (User)<br>Nullable. </td>
                <td>Affected User.</td>
            </tr>
            <tr>
                <td>is_global</td>
                <td>string (Is global)</td>
                <td>-</td>
            </tr>
        </tbody>
    </table>
  {{</tab>}}
{{</tabs>}}

#### Request sample

````json
{
  "route": "string",
  "enabled": true,
  "user": "string"
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
  "route": "string",
  "enabled": true,
  "roles": "string",
  "user": "string",
  "is_global": "string"
}
````

</details>

<div style="text-align:right">

[[top section]](#institution_ui_management) [[top page]](#table-of-contents) 
</div>
<br>

<!--- institution_ui_delete --->
## 9.6 Delete Institution UI <a name="institution_ui_delete"></a>

API endpoint that deletes Institution UI.


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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/ui/{id}/</span></td>
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

[[top section]](#institution_ui_management) [[top page]](#table-of-contents) 
</div>
<br><br>



# 10. Institution User Management <a name="institution_user_management"></a>
---
Set of API endpoint that allows Institution Users to be managed.

  10.1 GET: [List Institution User](#institution_user_list)<br>
  10.2 POST: [Create Institution User](#institution_user_create)<br>
  10.3 GET: [Read Institution User](#institution_user_read)<br>
  10.4 PUT: [Update Institution User](#institution_user_update)<br>
  10.5 PATCH: [Partial Update Institution User](#institution_user_partial_update)<br>
  10.6 DEL: [Delete Institution User](#institution_user_delete)<br>
<div style="text-align:right">

[[top page]](#table-of-contents) 
</div>
<br>


<!--- institution_user_list --->
## 10.1 List Institution User <a name="institution_user_list"></a>

API endpoint that allows Institution Users to be listed.

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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/user/</span></td>
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
                <td>username</td>
                <td>string </td>
                <td>-</td>
            </tr>
            <tr>
                <td>first_name</td>
                <td>string </td>
                <td>-</td>
            </tr>
            <tr>
                <td>last_name</td>
                <td>string </td>
                <td>-</td>
            </tr>
            <tr>
                <td>email</td>
                <td>string </td>
                <td>-</td>
            </tr>
            <tr>
                <td>roles</td>
                <td>string </td>
                <td>-</td>
            </tr>
            <tr>
                <td>uid</td>
                <td>string </td>
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
            <td>Array of objects (InstitutionUser)</td>
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
      "username": "string",
      "password": "string",
      "password2": "string",
      "last_login": "2019-08-24T14:15:22Z",
      "first_name": "string",
      "last_name": "string",
      "uid": "string",
      "email": "user@example.com",
      "locale": "string",
      "created_at": "2019-08-24T14:15:22Z",
      "updated_at": "2019-08-24T14:15:22Z",
      "inst_admin": true,
      "legal_admin": true,
      "send_admin": true,
      "data_admin": true
    }
  ]
}
 ````

</details>

<div style="text-align:right">

[[top section]](#institution_user_management) [[top page]](#table-of-contents) 
</div>
<br>


<!--- institution_user_create --->
## 10.2 Create Institution User <a name="institution_user_create"></a>

API endpoint that creates Institution User.

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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/user/</span></td>
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
                <td><strong>username</strong><br><code>required</code></td>
                <td>string (Username)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>password</td>
                <td>string (Password)<br>non-empty<br>Nullable. </td>
                <td>-</td>
            </tr>
            <tr>
                <td>password2</td>
                <td>string (Password2)<br>non-empty<br>Nullable. </td>
                <td>-</td>
            </tr>
            <tr>
                <td>first_name</td>
                <td>string (First name)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>last_name</td>
                <td>string (Last name)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>uid</strong><br><code>required</code></td>
                <td>string (Uid)<br>non-empty</td>
                <td>-</td>
            </tr>            <tr>
                <td>email</td>
                <td>string &lt;email&gt; (Email)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>locale</td>
                <td>string (Local)<br>[1 .. 10] characters<br>Nullable.</td>
                <td>Default locale for this user.</td>
            </tr>
            <tr>
                <td>inst_admin</td>
                <td>boolean (Inst admin)</td>
                <td>Whether this user is administrator of the institution.</td>
            </tr>
             <tr>
                <td>legal_admin</td>
                <td>boolean (Inst admin)</td>
                <td>Whether this user can manage legal data of the institution.</td>
            </tr>
           <tr>
                <td>send_admin</td>
                <td>boolean (Send admin)</td>
                <td>Whether this user can manage SEND data of the institution.</td>
            </tr>
            <tr>
                <td>data_admin</td>
                <td>boolean (Data admin)</td>
                <td>Whether this user can manage the data of the institution.</td>
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
                <td><strong>username</strong><br><code>required</code></td>
                <td>string (Username)<br>non-empty </td>
                <td>-</td>
            </tr>
             <tr>
                <td>password</td>
                <td>string (Password)<br>non-empty<br>Nullable. </td>
                <td>-</td>
            </tr>
             <tr>
                <td>password2</td>
                <td>string (Password2)<br>non-empty<br>Nullable. </td>
                <td>-</td>
            </tr>
            <tr>
                <td>last_login</td>
                <td>string &lt;date-time&gt; (Last login)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>first_name</td>
                <td>string (First name)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>last_name</td>
                <td>string (Last name)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>uid</strong><br><code>required</code></td>
                <td>string (Uid)<br>non-empty</td>
                <td>-</td>
            </tr>            
            <tr>
                <td>email</td>
                <td>string &lt;email&gt; (Email)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>locale</td>
                <td>string (Local)<br>[1 .. 10] characters<br>Nullable.</td>
                <td>Default locale for this user.</td>
            </tr>
            <tr>
                <td>created_at</td>
                <td>string &lt;date-time&gt; (Created at)</td>
                <td>Date when user was created.</td>
            </tr>
            <tr>
                <td>updated_at</td>
                <td>string &lt;date-time&gt; (Updated at)</td>
                <td>Last user modification.</td>
            </tr>
            <tr>
                <td>inst_admin</td>
                <td>boolean (Inst admin)</td>
                <td>Whether this user is administrator of the institution.</td>
            </tr>
             <tr>
                <td>legal_admin</td>
                <td>boolean (Inst admin)</td>
                <td>Whether this user can manage legal data of the institution.</td>
            </tr>
           <tr>
                <td>send_admin</td>
                <td>boolean (Send admin)</td>
                <td>Whether this user can manage SEND data of the institution.</td>
            </tr>
            <tr>
                <td>data_admin</td>
                <td>boolean (Data admin)</td>
                <td>Whether this user can manage the data of the institution.</td>
            </tr>
        </tbody>
    </table>
  {{</tab>}}
{{</tabs>}}

#### Request sample
`````json
{
  "username": "string",
  "password": "string",
  "password2": "string",
  "first_name": "string",
  "last_name": "string",
  "uid": "string",
  "email": "user@example.com",
  "locale": "string",
  "inst_admin": true,
  "legal_admin": true,
  "send_admin": true,
  "data_admin": true
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
  "username": "string",
  "password": "string",
  "password2": "string",
  "last_login": "2019-08-24T14:15:22Z",
  "first_name": "string",
  "last_name": "string",
  "uid": "string",
  "email": "user@example.com",
  "locale": "string",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z",
  "inst_admin": true,
  "legal_admin": true,
  "send_admin": true,
  "data_admin": true
}
````
</details>

<div style="text-align:right">

[[top section]](#institution_user_management) [[top page]](#table-of-contents) 
</div>
<br>


<!--- institution_user_read --->
## 10.3 Read Institution User <a name="institution_user_read"></a>

API endpoint that allows access to Institution User data.

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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/user/{id}/</span></td>
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
                <td><strong>username</strong><br><code>required</code></td>
                <td>string (Username)<br>non-empty </td>
                <td>-</td>
            </tr>
             <tr>
                <td>password</td>
                <td>string (Password)<br>non-empty<br>Nullable. </td>
                <td>-</td>
            </tr>
             <tr>
                <td>password2</td>
                <td>string (Password2)<br>non-empty<br>Nullable. </td>
                <td>-</td>
            </tr>
            <tr>
                <td>last_login</td>
                <td>string &lt;date-time&gt; (Last login)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>first_name</td>
                <td>string (First name)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>last_name</td>
                <td>string (Last name)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>uid</strong><br><code>required</code></td>
                <td>string (Uid)<br>non-empty</td>
                <td>-</td>
            </tr>            
            <tr>
                <td>email</td>
                <td>string &lt;email&gt; (Email)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>locale</td>
                <td>string (Local)<br>[1 .. 10] characters<br>Nullable.</td>
                <td>Default locale for this user.</td>
            </tr>
            <tr>
                <td>created_at</td>
                <td>string &lt;date-time&gt; (Created at)</td>
                <td>Date when user was created.</td>
            </tr>
            <tr>
                <td>updated_at</td>
                <td>string &lt;date-time&gt; (Updated at)</td>
                <td>Last user modification.</td>
            </tr>
            <tr>
                <td>inst_admin</td>
                <td>boolean (Inst admin)</td>
                <td>Whether this user is administrator of the institution.</td>
            </tr>
             <tr>
                <td>legal_admin</td>
                <td>boolean (Inst admin)</td>
                <td>Whether this user can manage legal data of the institution.</td>
            </tr>
           <tr>
                <td>send_admin</td>
                <td>boolean (Send admin)</td>
                <td>Whether this user can manage SEND data of the institution.</td>
            </tr>
            <tr>
                <td>data_admin</td>
                <td>boolean (Data admin)</td>
                <td>Whether this user can manage the data of the institution.</td>
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
  "username": "string",
  "password": "string",
  "password2": "string",
  "last_login": "2019-08-24T14:15:22Z",
  "first_name": "string",
  "last_name": "string",
  "uid": "string",
  "email": "user@example.com",
  "locale": "string",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z",
  "inst_admin": true,
  "legal_admin": true,
  "send_admin": true,
  "data_admin": true
}
````
</details>


<div style="text-align:right">

[[top section]](#institution_user_management) [[top page]](#table-of-contents) 
</div>

<br>

<!--- institution_user_update --->
## 10.4 Update Institution User <a name="institution_user_update"></a>

API endpoint that updates Institution User data.

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
            <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/user/{id}/</span></td>
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
                <td><strong>username</strong><br><code>required</code></td>
                <td>string (Username)<br>non-empty </td>
                <td>-</td>
            </tr>
             <tr>
                <td>password</td>
                <td>string (Password)<br>non-empty<br>Nullable. </td>
                <td>-</td>
            </tr>
             <tr>
                <td>password2</td>
                <td>string (Password2)<br>non-empty<br>Nullable. </td>
                <td>-</td>
            </tr>
            <tr>
                <td>first_name</td>
                <td>string (First name)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>last_name</td>
                <td>string (Last name)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>uid</strong><br><code>required</code></td>
                <td>string (Uid)<br>non-empty</td>
                <td>-</td>
            </tr>            
            <tr>
                <td>email</td>
                <td>string &lt;email&gt; (Email)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>locale</td>
                <td>string (Local)<br>[1 .. 10] characters<br>Nullable.</td>
                <td>Default locale for this user.</td>
            </tr>
            <tr>
                <td>inst_admin</td>
                <td>boolean (Inst admin)</td>
                <td>Whether this user is administrator of the institution.</td>
            </tr>
             <tr>
                <td>legal_admin</td>
                <td>boolean (Inst admin)</td>
                <td>Whether this user can manage legal data of the institution.</td>
            </tr>
           <tr>
                <td>send_admin</td>
                <td>boolean (Send admin)</td>
                <td>Whether this user can manage SEND data of the institution.</td>
            </tr>
            <tr>
                <td>data_admin</td>
                <td>boolean (Data admin)</td>
                <td>Whether this user can manage the data of the institution.</td>
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
                <td><strong>username</strong><br><code>required</code></td>
                <td>string (Username)<br>non-empty </td>
                <td>-</td>
            </tr>
             <tr>
                <td>password</td>
                <td>string (Password)<br>non-empty<br>Nullable. </td>
                <td>-</td>
            </tr>
             <tr>
                <td>password2</td>
                <td>string (Password2)<br>non-empty<br>Nullable. </td>
                <td>-</td>
            </tr>
            <tr>
                <td>last_login</td>
                <td>string &lt;date-time&gt; (Last login)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>first_name</td>
                <td>string (First name)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>last_name</td>
                <td>string (Last name)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>uid</strong><br><code>required</code></td>
                <td>string (Uid)<br>non-empty</td>
                <td>-</td>
            </tr>            
            <tr>
                <td>email</td>
                <td>string &lt;email&gt; (Email)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>locale</td>
                <td>string (Local)<br>[1 .. 10] characters<br>Nullable.</td>
                <td>Default locale for this user.</td>
            </tr>
            <tr>
                <td>created_at</td>
                <td>string &lt;date-time&gt; (Created at)</td>
                <td>Date when user was created.</td>
            </tr>
            <tr>
                <td>updated_at</td>
                <td>string &lt;date-time&gt; (Updated at)</td>
                <td>Last user modification.</td>
            </tr>
            <tr>
                <td>inst_admin</td>
                <td>boolean (Inst admin)</td>
                <td>Whether this user is administrator of the institution.</td>
            </tr>
             <tr>
                <td>legal_admin</td>
                <td>boolean (Inst admin)</td>
                <td>Whether this user can manage legal data of the institution.</td>
            </tr>
           <tr>
                <td>send_admin</td>
                <td>boolean (Send admin)</td>
                <td>Whether this user can manage SEND data of the institution.</td>
            </tr>
            <tr>
                <td>data_admin</td>
                <td>boolean (Data admin)</td>
                <td>Whether this user can manage the data of the institution.</td>
            </tr>
        </tbody>
    </table>
  {{</tab>}}
{{</tabs>}}

#### Request sample

````json
{
  "username": "string",
  "password": "string",
  "password2": "string",
  "first_name": "string",
  "last_name": "string",
  "uid": "string",
  "email": "user@example.com",
  "locale": "string",
  "inst_admin": true,
  "legal_admin": true,
  "send_admin": true,
  "data_admin": true
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
  "username": "string",
  "password": "string",
  "password2": "string",
  "last_login": "2019-08-24T14:15:22Z",
  "first_name": "string",
  "last_name": "string",
  "uid": "string",
  "email": "user@example.com",
  "locale": "string",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z",
  "inst_admin": true,
  "legal_admin": true,
  "send_admin": true,
  "data_admin": true
}
````

</details>

<div style="text-align:right">

[[top section]](#institution_user_management) [[top page]](#table-of-contents) 
</div>
<br>

<!--- institution_user_partial_update --->
## 10.5 Partial Update Institution User <a name="institution_user_partial_update"></a>

API endpoint that updates Institution User data.

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
            <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/user/{id}/</span></td>
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
                <td><strong>username</strong><br><code>required</code></td>
                <td>string (Username)<br>non-empty </td>
                <td>-</td>
            </tr>
             <tr>
                <td>password</td>
                <td>string (Password)<br>non-empty<br>Nullable. </td>
                <td>-</td>
            </tr>
             <tr>
                <td>password2</td>
                <td>string (Password2)<br>non-empty<br>Nullable. </td>
                <td>-</td>
            </tr>
            <tr>
                <td>first_name</td>
                <td>string (First name)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>last_name</td>
                <td>string (Last name)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>uid</strong><br><code>required</code></td>
                <td>string (Uid)<br>non-empty</td>
                <td>-</td>
            </tr>            
            <tr>
                <td>email</td>
                <td>string &lt;email&gt; (Email)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>locale</td>
                <td>string (Local)<br>[1 .. 10] characters<br>Nullable.</td>
                <td>Default locale for this user.</td>
            </tr>
            <tr>
                <td>inst_admin</td>
                <td>boolean (Inst admin)</td>
                <td>Whether this user is administrator of the institution.</td>
            </tr>
             <tr>
                <td>legal_admin</td>
                <td>boolean (Inst admin)</td>
                <td>Whether this user can manage legal data of the institution.</td>
            </tr>
           <tr>
                <td>send_admin</td>
                <td>boolean (Send admin)</td>
                <td>Whether this user can manage SEND data of the institution.</td>
            </tr>
            <tr>
                <td>data_admin</td>
                <td>boolean (Data admin)</td>
                <td>Whether this user can manage the data of the institution.</td>
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
                <td><strong>username</strong><br><code>required</code></td>
                <td>string (Username)<br>non-empty </td>
                <td>-</td>
            </tr>
             <tr>
                <td>password</td>
                <td>string (Password)<br>non-empty<br>Nullable. </td>
                <td>-</td>
            </tr>
             <tr>
                <td>password2</td>
                <td>string (Password2)<br>non-empty<br>Nullable. </td>
                <td>-</td>
            </tr>
            <tr>
                <td>last_login</td>
                <td>string &lt;date-time&gt; (Last login)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>first_name</td>
                <td>string (First name)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>last_name</td>
                <td>string (Last name)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>uid</strong><br><code>required</code></td>
                <td>string (Uid)<br>non-empty</td>
                <td>-</td>
            </tr>            
            <tr>
                <td>email</td>
                <td>string &lt;email&gt; (Email)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>locale</td>
                <td>string (Local)<br>[1 .. 10] characters<br>Nullable.</td>
                <td>Default locale for this user.</td>
            </tr>
            <tr>
                <td>created_at</td>
                <td>string &lt;date-time&gt; (Created at)</td>
                <td>Date when user was created.</td>
            </tr>
            <tr>
                <td>updated_at</td>
                <td>string &lt;date-time&gt; (Updated at)</td>
                <td>Last user modification.</td>
            </tr>
            <tr>
                <td>inst_admin</td>
                <td>boolean (Inst admin)</td>
                <td>Whether this user is administrator of the institution.</td>
            </tr>
             <tr>
                <td>legal_admin</td>
                <td>boolean (Inst admin)</td>
                <td>Whether this user can manage legal data of the institution.</td>
            </tr>
           <tr>
                <td>send_admin</td>
                <td>boolean (Send admin)</td>
                <td>Whether this user can manage SEND data of the institution.</td>
            </tr>
            <tr>
                <td>data_admin</td>
                <td>boolean (Data admin)</td>
                <td>Whether this user can manage the data of the institution.</td>
            </tr>
        </tbody>
    </table>
  {{</tab>}}
{{</tabs>}}

#### Request sample

````json
{
  "username": "string",
  "password": "string",
  "password2": "string",
  "first_name": "string",
  "last_name": "string",
  "uid": "string",
  "email": "user@example.com",
  "locale": "string",
  "inst_admin": true,
  "legal_admin": true,
  "send_admin": true,
  "data_admin": true
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
  "username": "string",
  "password": "string",
  "password2": "string",
  "last_login": "2019-08-24T14:15:22Z",
  "first_name": "string",
  "last_name": "string",
  "uid": "string",
  "email": "user@example.com",
  "locale": "string",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z",
  "inst_admin": true,
  "legal_admin": true,
  "send_admin": true,
  "data_admin": true
}
````

</details>

<div style="text-align:right">

[[top section]](#institution_user_management) [[top page]](#table-of-contents) 
</div>
<br>

<!--- institution_user_delete --->
## 10.6 Delete Institution User <a name="institution_user_delete"></a>

API endpoint that deletes Institution User.


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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/user/{id}/</span></td>
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

[[top section]](#institution_user_management) [[top page]](#table-of-contents) 
</div>
<br><br>


# 11. Institution Instructor Management <a name="institution_instructor_management"></a>
---
Set of API endpoint that allows Institution Instructors to be viewed or edited.

  11.1 GET: [List Institution Instructor](#institution_instructor_list)<br>
  11.2 POST: [Create Institution Instructor](#institution_instructor_create)<br>
  11.3 GET: [Read Institution Instructor](#institution_instructor_read)<br>
  11.4 PUT: [Update Institution Instructor](#institution_instructor_update)<br>
  11.5 PATCH: [Partial Update Institution Instructor](#institution_instructor_partial_update)<br>
  11.6 DEL: [Delete Institution Instructor](#institution_instructor_delete)<br>
<div style="text-align:right">

[[top page]](#table-of-contents) 
</div>
<br>


<!--- institution_instructor_list --->
## 11.1 List Institution Instructor <a name="institution_instructor_list"></a>

API endpoint that allows Institution Instructors to be listed.

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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/instructor/</span></td>
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
            <td>Array of objects (InstitutionInstructor)</td>
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
      "username": "string",
      "last_login": "2019-08-24T14:15:22Z",
      "first_name": "string",
      "last_name": "string",
      "email": "user@example.com",
      "locale": "string",
      "created_at": "2019-08-24T14:15:22Z",
      "updated_at": "2019-08-24T14:15:22Z",
      "uid": "string",
      "inst_admin": true,
      "legal_admin": true,
      "send_admin": true,
      "data_admin": true
    }
  ]
}
 ````

</details>

<div style="text-align:right">

[[top section]](#institution_instructor_management) [[top page]](#table-of-contents) 
</div>
<br>


<!--- institution_instructor_create --->
## 11.2 Create Institution Instructor <a name="institution_instructor_create"></a>

API endpoint that creates Institution Instructor.

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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/instructor/</span></td>
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
                <td>first_name</td>
                <td>string (First name)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>last_name</td>
                <td>string (Last name)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>email</td>
                <td>string &lt;email&gt; (Email)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>locale</td>
                <td>string (Local)<br>[1 .. 10] characters<br>Nullable.</td>
                <td>Default locale for this user.</td>
            </tr>
            <tr>
                <td><strong>uid</strong><br><code>required</code></td>
                <td>string (Uid)<br>[1 .. 255] characters</td>
                <td>Unique User Identifier for the institution.</td>
            </tr>
            <tr>
                <td>inst_admin</td>
                <td>boolean (Inst admin)</td>
                <td>Whether this user is administrator of the institution.</td>
            </tr>
             <tr>
                <td>legal_admin</td>
                <td>boolean (Inst admin)</td>
                <td>Whether this user can manage legal data of the institution.</td>
            </tr>
           <tr>
                <td>send_admin</td>
                <td>boolean (Send admin)</td>
                <td>Whether this user can manage SEND data of the institution.</td>
            </tr>
            <tr>
                <td>data_admin</td>
                <td>boolean (Data admin)</td>
                <td>Whether this user can manage the data of the institution.</td>
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
                <td>username</td>
                <td>string (Username)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>last_login</td>
                <td>string &lt;date-time&gt; (Last login)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>first_name</td>
                <td>string (First name)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>last_name</td>
                <td>string (Last name)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>email</td>
                <td>string &lt;email&gt; (Email)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>locale</td>
                <td>string (Local)<br>[1 .. 10] characters<br>Nullable.</td>
                <td>Default locale for this user.</td>
            </tr>
            <tr>
                <td>created_at</td>
                <td>string &lt;date-time&gt; (Created at)</td>
                <td>Date when user was created.</td>
            </tr>
            <tr>
                <td>updated_at</td>
                <td>string &lt;date-time&gt; (Updated at)</td>
                <td>Last user modification.</td>
            </tr>
            <tr>
                <td><strong>uid</strong><br><code>required</code></td>
                <td>string (Uid)<br>[1 .. 255] characters</td>
                <td>Unique User Identifier for the institution.</td>
            </tr>
            <tr>
                <td>inst_admin</td>
                <td>boolean (Inst admin)</td>
                <td>Whether this user is administrator of the institution.</td>
            </tr>
             <tr>
                <td>legal_admin</td>
                <td>boolean (Inst admin)</td>
                <td>Whether this user can manage legal data of the institution.</td>
            </tr>
           <tr>
                <td>send_admin</td>
                <td>boolean (Send admin)</td>
                <td>Whether this user can manage SEND data of the institution.</td>
            </tr>
            <tr>
                <td>data_admin</td>
                <td>boolean (Data admin)</td>
                <td>Whether this user can manage the data of the institution.</td>
            </tr>
        </tbody>
    </table>
  {{</tab>}}
{{</tabs>}}

#### Request sample
`````json
{
  "first_name": "string",
  "last_name": "string",
  "email": "user@example.com",
  "locale": "string",
  "uid": "string",
  "inst_admin": true,
  "legal_admin": true,
  "send_admin": true,
  "data_admin": true
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
  "username": "string",
  "last_login": "2019-08-24T14:15:22Z",
  "first_name": "string",
  "last_name": "string",
  "email": "user@example.com",
  "locale": "string",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z",
  "uid": "string",
  "inst_admin": true,
  "legal_admin": true,
  "send_admin": true,
  "data_admin": true
}
````
</details>

<div style="text-align:right">

[[top section]](#institution_instructor_management) [[top page]](#table-of-contents) 
</div>
<br>


<!--- institution_instructor_read --->
## 11.3 Read Institution Instructor <a name="institution_instructor_read"></a>

API endpoint that allows access to Institution Instructor data.

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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/instructor/{id}/</span></td>
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
                <td>username</td>
                <td>string (Username)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>last_login</td>
                <td>string &lt;date-time&gt; (Last login)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>first_name</td>
                <td>string (First name)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>last_name</td>
                <td>string (Last name)<br>non-empty</td>
                <td>-</td>
            </tr> 
            <tr>
                <td>email</td>
                <td>string &lt;email&gt; (Email)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>locale</td>
                <td>string (Local)<br>[1 .. 10] characters<br>Nullable.</td>
                <td>Default locale for this user.</td>
            </tr>
            <tr>
                <td>created_at</td>
                <td>string &lt;date-time&gt; (Created at)</td>
                <td>Date when user was created.</td>
            </tr>
            <tr>
                <td>updated_at</td>
                <td>string &lt;date-time&gt; (Updated at)</td>
                <td>Last user modification.</td>
            </tr>
            <tr>
                <td><strong>uid</strong><br><code>required</code></td>
                <td>string (Uid)<br>[1 .. 255] characters</td>
                <td>Unique User Identifier for the Institution.</td>
            </tr>  
            <tr>
                <td>inst_admin</td>
                <td>boolean (Inst admin)</td>
                <td>Whether this user is administrator of the institution.</td>
            </tr>
             <tr>
                <td>legal_admin</td>
                <td>boolean (Inst admin)</td>
                <td>Whether this user can manage legal data of the institution.</td>
            </tr>
           <tr>
                <td>send_admin</td>
                <td>boolean (Send admin)</td>
                <td>Whether this user can manage SEND data of the institution.</td>
            </tr>
            <tr>
                <td>data_admin</td>
                <td>boolean (Data admin)</td>
                <td>Whether this user can manage the data of the institution.</td>
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
  "username": "string",
  "last_login": "2019-08-24T14:15:22Z",
  "first_name": "string",
  "last_name": "string",
  "email": "user@example.com",
  "locale": "string",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z",
  "uid": "string",
  "inst_admin": true,
  "legal_admin": true,
  "send_admin": true,
  "data_admin": true
}
````
</details>


<div style="text-align:right">

[[top section]](#institution_instructor_management) [[top page]](#table-of-contents) 
</div>

<br>

<!--- institution_instructor_update --->
## 11.4 Update Institution Instructor <a name="institution_instructor_update"></a>

API endpoint that updates Institution Instructor data.

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
            <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/instructor/{id}/</span></td>
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
                <td>first_name</td>
                <td>string (First name)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>last_name</td>
                <td>string (Last name)<br>non-empty</td>
                <td>-</td>
            </tr> 
            <tr>
                <td>email</td>
                <td>string &lt;email&gt; (Email)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>locale</td>
                <td>string (Local)<br>[1 .. 10] characters<br>Nullable.</td>
                <td>Default locale for this user.</td>
            </tr>
             <tr>
                <td><strong>uid</strong><br><code>required</code></td>
                <td>string (Uid)<br>[1 .. 255] characters</td>
                <td>Unique User Identifier for the institution.</td>
            </tr>  
            <tr>
                <td>inst_admin</td>
                <td>boolean (Inst admin)</td>
                <td>Whether this user is administrator of the institution.</td>
            </tr>
             <tr>
                <td>legal_admin</td>
                <td>boolean (Inst admin)</td>
                <td>Whether this user can manage legal data of the institution.</td>
            </tr>
           <tr>
                <td>send_admin</td>
                <td>boolean (Send admin)</td>
                <td>Whether this user can manage SEND data of the institution.</td>
            </tr>
            <tr>
                <td>data_admin</td>
                <td>boolean (Data admin)</td>
                <td>Whether this user can manage the data of the institution.</td>
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
                <td><strong>username</strong><br><code>required</code></td>
                <td>string (Username)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>last_login</td>
                <td>string &lt;date-time&gt; (Last login)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>first_name</td>
                <td>string (First name)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>last_name</td>
                <td>string (Last name)<br>non-empty</td>
                <td>-</td>
            </tr> 
            <tr>
                <td>email</td>
                <td>string &lt;email&gt; (Email)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>locale</td>
                <td>string (Local)<br>[1 .. 10] characters<br>Nullable.</td>
                <td>Default locale for this user.</td>
            </tr>
            <tr>
                <td>created_at</td>
                <td>string &lt;date-time&gt; (Created at)</td>
                <td>Date when user was created.</td>
            </tr>
            <tr>
                <td>updated_at</td>
                <td>string &lt;date-time&gt; (Updated at)</td>
                <td>Last user modification.</td>
            </tr>
            <tr>
                <td><strong>uid</strong><br><code>required</code></td>
                <td>string (Uid)<br>[1 .. 255] characters</td>
                <td>Unique User Identifier for the institution.</td>
            </tr>  
            <tr>
                <td>inst_admin</td>
                <td>boolean (Inst admin)</td>
                <td>Whether this user is administrator of the institution.</td>
            </tr>
             <tr>
                <td>legal_admin</td>
                <td>boolean (Inst admin)</td>
                <td>Whether this user can manage legal data of the institution.</td>
            </tr>
           <tr>
                <td>send_admin</td>
                <td>boolean (Send admin)</td>
                <td>Whether this user can manage SEND data of the institution.</td>
            </tr>
            <tr>
                <td>data_admin</td>
                <td>boolean (Data admin)</td>
                <td>Whether this user can manage the data of the institution.</td>
            </tr>
        </tbody>
    </table>
  {{</tab>}}
{{</tabs>}}

#### Request sample

````json
{
  "first_name": "string",
  "last_name": "string",
  "email": "user@example.com",
  "locale": "string",
  "uid": "string",
  "inst_admin": true,
  "legal_admin": true,
  "send_admin": true,
  "data_admin": true
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
  "username": "string",
  "last_login": "2019-08-24T14:15:22Z",
  "first_name": "string",
  "last_name": "string",
  "email": "user@example.com",
  "locale": "string",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z",
  "uid": "string",
  "inst_admin": true,
  "legal_admin": true,
  "send_admin": true,
  "data_admin": true
}
````

</details>

<div style="text-align:right">

[[top section]](#institution_instructor_management) [[top page]](#table-of-contents) 
</div>
<br>

<!--- institution_instructor_partial_update --->
## 11.5 Partial Update Institution Instructor <a name="institution_instructor_partial_update"></a>

API endpoint that updates Institution Instructor data.

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
            <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/instructor/{id}/</span></td>
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
                <td>first_name</td>
                <td>string (First name)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>last_name</td>
                <td>string (Last name)<br>non-empty</td>
                <td>-</td>
            </tr> 
            <tr>
                <td>email</td>
                <td>string &lt;email&gt; (Email)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>locale</td>
                <td>string (Local)<br>[1 .. 10] characters<br>Nullable.</td>
                <td>Default locale for this user.</td>
            </tr>
             <tr>
                <td><strong>uid</strong><br><code>required</code></td>
                <td>string (Uid)<br>[1 .. 255] characters</td>
                <td>Unique User Identifier for the institution.</td>
            </tr>  
            <tr>
                <td>inst_admin</td>
                <td>boolean (Inst admin)</td>
                <td>Whether this user is administrator of the institution.</td>
            </tr>
             <tr>
                <td>legal_admin</td>
                <td>boolean (Inst admin)</td>
                <td>Whether this user can manage legal data of the institution.</td>
            </tr>
           <tr>
                <td>send_admin</td>
                <td>boolean (Send admin)</td>
                <td>Whether this user can manage SEND data of the institution.</td>
            </tr>
            <tr>
                <td>data_admin</td>
                <td>boolean (Data admin)</td>
                <td>Whether this user can manage the data of the institution.</td>
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
                <td><strong>username</strong><br><code>required</code></td>
                <td>string (Username)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>last_login</td>
                <td>string &lt;date-time&gt; (Last login)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>first_name</td>
                <td>string (First name)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>last_name</td>
                <td>string (Last name)<br>non-empty</td>
                <td>-</td>
            </tr> 
            <tr>
                <td>email</td>
                <td>string &lt;email&gt; (Email)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>locale</td>
                <td>string (Local)<br>[1 .. 10] characters<br>Nullable.</td>
                <td>Default locale for this user.</td>
            </tr>
            <tr>
                <td>created_at</td>
                <td>string &lt;date-time&gt; (Created at)</td>
                <td>Date when user was created.</td>
            </tr>
            <tr>
                <td>updated_at</td>
                <td>string &lt;date-time&gt; (Updated at)</td>
                <td>Last user modification.</td>
            </tr>
            <tr>
                <td><strong>uid</strong><br><code>required</code></td>
                <td>string (Uid)<br>[1 .. 255] characters</td>
                <td>Unique User Identifier for the institution.</td>
            </tr>  
            <tr>
                <td>inst_admin</td>
                <td>boolean (Inst admin)</td>
                <td>Whether this user is administrator of the institution.</td>
            </tr>
             <tr>
                <td>legal_admin</td>
                <td>boolean (Inst admin)</td>
                <td>Whether this user can manage legal data of the institution.</td>
            </tr>
           <tr>
                <td>send_admin</td>
                <td>boolean (Send admin)</td>
                <td>Whether this user can manage SEND data of the institution.</td>
            </tr>
            <tr>
                <td>data_admin</td>
                <td>boolean (Data admin)</td>
                <td>Whether this user can manage the data of the institution.</td>
            </tr>
        </tbody>
    </table>
  {{</tab>}}
{{</tabs>}}

#### Request sample

````json
{
  "first_name": "string",
  "last_name": "string",
  "email": "user@example.com",
  "locale": "string",
  "uid": "string",
  "inst_admin": true,
  "legal_admin": true,
  "send_admin": true,
  "data_admin": true
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
  "username": "string",
  "last_login": "2019-08-24T14:15:22Z",
  "first_name": "string",
  "last_name": "string",
  "email": "user@example.com",
  "locale": "string",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z",
  "uid": "string",
  "inst_admin": true,
  "legal_admin": true,
  "send_admin": true,
  "data_admin": true
}
````

</details>

<div style="text-align:right">

[[top section]](#institution_instructor_management) [[top page]](#table-of-contents) 
</div>
<br>

<!--- institution_instructor_delete --->
## 11.6 Delete Institution Instructor <a name="institution_instructor_delete"></a>

API endpoint that deletes Institution Instructor.


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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/instructor/{id}/</span></td>
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

[[top section]](#institution_instructor_management) [[top page]](#table-of-contents) 
</div>
<br><br>



# 12. Institution Learner Management <a name="institution_learner_management"></a>
---
Set of API endpoint that allows Institution Learners to be viewed or edited.

  12.1 GET: [List Institution Learner](#institution_learner_list)<br>
  12.2 POST: [Create Institution Learner](#institution_learner_create)<br>
  12.3 GET: [Read Institution Learner](#institution_learner_read)<br>
  12.4 PUT: [Update Institution Learner](#institution_learner_update)<br>
  12.5 PATCH: [Partial Update Institution Learner](#institution_learner_partial_update)<br>
  12.6 DEL: [Delete Institution Learner](#institution_learner_delete)<br>
  12.7 GET: [Enrolment Institution Learner](#institution_learner_enrolment)<br>
  12.8 POST: [Create Institution Learner IC](#institution_learner_ic_create)<br>
  12.9 DEL: [Delete Institution Learner IC](#institution_learner_ic_delete)<br>


<div style="text-align:right">

[[top page]](#table-of-contents) 
</div>
<br>


<!--- institution_learner_list --->
## 12.1 List Institution Learner <a name="institution_learner_list"></a>

API endpoint that allows Institution Learners to be listed.

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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/learner/</span></td>
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
            <td>Array of objects (InstitutionLearner)</td>
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
      "username": "string",
      "consent": {
        "version": "string",
        "status": "string"
      },
      "consent_accepted": "2019-08-24T14:15:22Z",
      "consent_rejected": "2019-08-24T14:15:22Z",
      "learner_id": "2df776db-09df-4cb9-a2af-db56cada6cb7",
      "last_login": "2019-08-24T14:15:22Z",
      "send": {},
      "email": "user@example.com",
      "ic_status": "string",
      "login_allowed": false,
      "first_name": "string",
      "last_name": "string",
      "locale": "string",
      "created_at": "2019-08-24T14:15:22Z",
      "updated_at": "2019-08-24T14:15:22Z",
      "uid": "string",
      "inst_admin": true,
      "legal_admin": true,
      "send_admin": true,
      "data_admin": true,
      "joined_at": "2019-08-24T14:15:22Z"
    }
  ]
}
 ````

</details>

<div style="text-align:right">

[[top section]](#institution_learner_management) [[top page]](#table-of-contents) 
</div>
<br>


<!--- institution_learner_create --->
## 12.2 Create Institution Learner <a name="institution_learner_create"></a>

API endpoint that creates Institution Learner.

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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/learner/</span></td>
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
                <td>consent</td>
                <td>object (InstitutionLearnerConsent)<br>Nullable.</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>email</strong><br><code>required</code></td>
                <td>string &lt;email&gt; (Email)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>first_name</td>
                <td>string (First name)<br><= 150 characters</td>
                <td>-</td>
            </tr>
            <tr>
                <td>last_name</td>
                <td>string (Last name)<br><= 150 characters</td>
                <td>-</td>
            </tr>
            <tr>
                <td>locale</td>
                <td>string (Local)<br>[1 .. 10] characters<br>Nullable.</td>
                <td>Default locale for this user.</td>
            </tr>
            <tr>
                <td><strong>uid</strong><br><code>required</code></td>
                <td>string (Uid)<br>[1 .. 255] characters</td>
                <td>Unique User Identifier for the institution.</td>
            </tr>
            <tr>
                <td>inst_admin</td>
                <td>boolean (Inst admin)</td>
                <td>Whether this user is administrator of the institution.</td>
            </tr>
             <tr>
                <td>legal_admin</td>
                <td>boolean (Inst admin)</td>
                <td>Whether this user can manage legal data of the institution.</td>
            </tr>
           <tr>
                <td>send_admin</td>
                <td>boolean (Send admin)</td>
                <td>Whether this user can manage SEND data of the institution.</td>
            </tr>
            <tr>
                <td>data_admin</td>
                <td>boolean (Data admin)</td>
                <td>Whether this user can manage the data of the institution.</td>
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
                <td>username</td>
                <td>string (Username)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>consent</td>
                <td>object (InstitutionLearnerConsent)<br>Nullable.</td>
                <td>-</td>
            </tr>
            <tr>
                <td>consent_accepted</td>
                <td>string &lt;date-time&gt; (Consent accepted)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>consent_rejected</td>
                <td>string &lt;date-time&gt; (Consent rejected)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>learner_id</td>
                <td>string &lt;uuid&gt; (Learner id)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>last_login</td>
                <td>string &lt;date-time&gt; (Last login)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>send</td>
                <td>object (Send)</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>email</strong><br><code>required</code></td>
                <td>string &lt;email&gt; (Email)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>ic_status</td>
                <td>string (IC status)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>login_allowed</td>
                <td>boolean (Login allowed)</td>
                <td>Default: false</td>
            </tr>
            <tr>
                <td>first_name</td>
                <td>string (First name)<br><=150 characters></td>
                <td>-</td>
            </tr>
            <tr>
                <td>last_name</td>
                <td>string (Last name)<br><=150 characters</td>
                <td>-</td>
            </tr>
            <tr>
                <td>locale</td>
                <td>string (Local)<br>[1 .. 10] characters<br>Nullable.</td>
                <td>Default locale for this user.</td>
            </tr>
            <tr>
                <td>created_at</td>
                <td>string &lt;date-time&gt; (Created at)</td>
                <td>Date when user was created.</td>
            </tr>
            <tr>
                <td>updated_at</td>
                <td>string &lt;date-time&gt; (Updated at)</td>
                <td>Last user modification.</td>
            </tr>
            <tr>
                <td><strong>uid</strong><br><code>required</code></td>
                <td>string (Uid)<br>[1 .. 255] characters</td>
                <td>Unique User Identifier for the institution.</td>
            </tr>
            <tr>
                <td>inst_admin</td>
                <td>boolean (Inst admin)</td>
                <td>Whether this user is administrator of the institution.</td>
            </tr>
             <tr>
                <td>legal_admin</td>
                <td>boolean (Inst admin)</td>
                <td>Whether this user can manage legal data of the institution.</td>
            </tr>
           <tr>
                <td>send_admin</td>
                <td>boolean (Send admin)</td>
                <td>Whether this user can manage SEND data of the institution.</td>
            </tr>
            <tr>
                <td>data_admin</td>
                <td>boolean (Data admin)</td>
                <td>Whether this user can manage the data of the institution.</td>
            </tr>
            <tr>
                <td>joined_at</td>
                <td>string &lt;date-time&gt; (Joined at)</td>
                <td>Date the learner joined for this institution.</td>
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
  "consent": {
    "version": "string"
  },
  "email": "user@example.com",
  "first_name": "string",
  "last_name": "string",
  "locale": "string",
  "uid": "string",
  "inst_admin": true,
  "legal_admin": true,
  "send_admin": true,
  "data_admin": true
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
  "username": "string",
  "consent": {
    "version": "string",
    "status": "string"
  },
  "consent_accepted": "2019-08-24T14:15:22Z",
  "consent_rejected": "2019-08-24T14:15:22Z",
  "learner_id": "2df776db-09df-4cb9-a2af-db56cada6cb7",
  "last_login": "2019-08-24T14:15:22Z",
  "send": {},
  "email": "user@example.com",
  "ic_status": "string",
  "login_allowed": false,
  "first_name": "string",
  "last_name": "string",
  "locale": "string",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z",
  "uid": "string",
  "inst_admin": true,
  "legal_admin": true,
  "send_admin": true,
  "data_admin": true,
  "joined_at": "2019-08-24T14:15:22Z"
}
````
</details>

<div style="text-align:right">

[[top section]](#institution_learner_management) [[top page]](#table-of-contents) 
</div>
<br>


<!--- institution_learner_read --->
## 12.3 Read Institution Learner <a name="institution_learner_read"></a>

API endpoint that allows access to Institution Learner data.

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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/learner/{id}/</span></td>
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
                <td>username</td>
                <td>string (Username)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>consent</td>
                <td>object (InstitutionLearnerConsent)<br>Nullable.</td>
                <td>-</td>
            </tr>
            <tr>
                <td>consent_accepted</td>
                <td>string &lt;date-time&gt; (Consent accepted)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>consent_rejected</td>
                <td>string &lt;date-time&gt; (Consent rejected)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>learner_id</td>
                <td>string &lt;uuid&gt; (Learner id)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>last_login</td>
                <td>string &lt;date-time&gt; (Last login)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>send</td>
                <td>object (Send)</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>email</strong><br><code>required</code></td>
                <td>string &lt;email&gt; (Email)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>ic_status</td>
                <td>string (IC status)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>login_allowed</td>
                <td>boolean (Login allowed)</td>
                <td>Default: false</td>
            </tr>
            <tr>
                <td>first_name</td>
                <td>string (First name)<br><=150 characters></td>
                <td>-</td>
            </tr>
            <tr>
                <td>last_name</td>
                <td>string (Last name)<br><=150 characters</td>
                <td>-</td>
            </tr>
            <tr>
                <td>locale</td>
                <td>string (Local)<br>[1 .. 10] characters<br>Nullable.</td>
                <td>Default locale for this user.</td>
            </tr>
            <tr>
                <td>created_at</td>
                <td>string &lt;date-time&gt; (Created at)</td>
                <td>Date when user was created.</td>
            </tr>
            <tr>
                <td>updated_at</td>
                <td>string &lt;date-time&gt; (Updated at)</td>
                <td>Last user modification.</td>
            </tr>
            <tr>
                <td><strong>uid</strong><br><code>required</code></td>
                <td>string (Uid)<br>[1 .. 255] characters</td>
                <td>Unique User Identifier for the institution.</td>
            </tr>
            <tr>
                <td>inst_admin</td>
                <td>boolean (Inst admin)</td>
                <td>Whether this user is administrator of the institution.</td>
            </tr>
             <tr>
                <td>legal_admin</td>
                <td>boolean (Inst admin)</td>
                <td>Whether this user can manage legal data of the institution.</td>
            </tr>
           <tr>
                <td>send_admin</td>
                <td>boolean (Send admin)</td>
                <td>Whether this user can manage SEND data of the institution.</td>
            </tr>
            <tr>
                <td>data_admin</td>
                <td>boolean (Data admin)</td>
                <td>Whether this user can manage the data of the institution.</td>
            </tr>
            <tr>
                <td>joined_at</td>
                <td>string &lt;date-time&gt; (Joined at)</td>
                <td>Date the learner joined for this institution.</td>
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
  "username": "string",
  "consent": {
    "version": "string",
    "status": "string"
  },
  "consent_accepted": "2019-08-24T14:15:22Z",
  "consent_rejected": "2019-08-24T14:15:22Z",
  "learner_id": "2df776db-09df-4cb9-a2af-db56cada6cb7",
  "last_login": "2019-08-24T14:15:22Z",
  "send": {},
  "email": "user@example.com",
  "ic_status": "string",
  "login_allowed": false,
  "first_name": "string",
  "last_name": "string",
  "locale": "string",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z",
  "uid": "string",
  "inst_admin": true,
  "legal_admin": true,
  "send_admin": true,
  "data_admin": true,
  "joined_at": "2019-08-24T14:15:22Z"
}
````
</details>


<div style="text-align:right">

[[top section]](#institution_learner_management) [[top page]](#table-of-contents) 
</div>

<br>

<!--- institution_learner_update --->
## 12.4 Update Institution Learner <a name="institution_learner_update"></a>

API endpoint that updates Institution Learner data.

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
            <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/learner/{id}/</span></td>
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
                <td>consent</td>
                <td>object (InstitutionLearnerConsent)<br>Nullable.</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>email</strong><br><code>required</code></td>
                <td>string &lt;email&gt; (Email)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>first_name</td>
                <td>string (First name)<br><=150 characters></td>
                <td>-</td>
            </tr>
            <tr>
                <td>last_name</td>
                <td>string (Last name)<br><=150 characters</td>
                <td>-</td>
            </tr>
            <tr>
                <td>locale</td>
                <td>string (Local)<br>[1 .. 10] characters<br>Nullable.</td>
                <td>Default locale for this user.</td>
            </tr>
            <tr>
                <td><strong>uid</strong><br><code>required</code></td>
                <td>string (Uid)<br>[1 .. 255] characters</td>
                <td>Unique User Identifier for the institution.</td>
            </tr>
            <tr>
                <td>inst_admin</td>
                <td>boolean (Inst admin)</td>
                <td>Whether this user is administrator of the institution.</td>
            </tr>
             <tr>
                <td>legal_admin</td>
                <td>boolean (Inst admin)</td>
                <td>Whether this user can manage legal data of the institution.</td>
            </tr>
           <tr>
                <td>send_admin</td>
                <td>boolean (Send admin)</td>
                <td>Whether this user can manage SEND data of the institution.</td>
            </tr>
            <tr>
                <td>data_admin</td>
                <td>boolean (Data admin)</td>
                <td>Whether this user can manage the data of the institution.</td>
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
                <td>username</td>
                <td>string (Username)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>consent</td>
                <td>object (InstitutionLearnerConsent)<br>Nullable.</td>
                <td>-</td>
            </tr>
            <tr>
                <td>consent_accepted</td>
                <td>string &lt;date-time&gt; (Consent accepted)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>consent_rejected</td>
                <td>string &lt;date-time&gt; (Consent rejected)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>learner_id</td>
                <td>string &lt;uuid&gt; (Learner id)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>last_login</td>
                <td>string &lt;date-time&gt; (Last login)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>send</td>
                <td>object (Send)</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>email</strong><br><code>required</code></td>
                <td>string &lt;email&gt; (Email)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>ic_status</td>
                <td>string (IC status)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>login_allowed</td>
                <td>boolean (Login allowed)</td>
                <td>Default: false</td>
            </tr>
            <tr>
                <td>first_name</td>
                <td>string (First name)<br><=150 characters></td>
                <td>-</td>
            </tr>
            <tr>
                <td>last_name</td>
                <td>string (Last name)<br><=150 characters</td>
                <td>-</td>
            </tr>
            <tr>
                <td>locale</td>
                <td>string (Local)<br>[1 .. 10] characters<br>Nullable.</td>
                <td>Default locale for this user.</td>
            </tr>
            <tr>
                <td>created_at</td>
                <td>string &lt;date-time&gt; (Created at)</td>
                <td>Date when user was created.</td>
            </tr>
            <tr>
                <td>updated_at</td>
                <td>string &lt;date-time&gt; (Updated at)</td>
                <td>Last user modification.</td>
            </tr>
            <tr>
                <td><strong>uid</strong><br><code>required</code></td>
                <td>string (Uid)<br>[1 .. 255] characters</td>
                <td>Unique User Identifier for the institution.</td>
            </tr>
            <tr>
                <td>inst_admin</td>
                <td>boolean (Inst admin)</td>
                <td>Whether this user is administrator of the institution.</td>
            </tr>
             <tr>
                <td>legal_admin</td>
                <td>boolean (Inst admin)</td>
                <td>Whether this user can manage legal data of the institution.</td>
            </tr>
           <tr>
                <td>send_admin</td>
                <td>boolean (Send admin)</td>
                <td>Whether this user can manage SEND data of the institution.</td>
            </tr>
            <tr>
                <td>data_admin</td>
                <td>boolean (Data admin)</td>
                <td>Whether this user can manage the data of the institution.</td>
            </tr>
            <tr>
                <td>joined_at</td>
                <td>string &lt;date-time&gt; (Joined at)</td>
                <td>Date the learner joined for this institution.</td>
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
  "consent": {
    "version": "string"
  },
  "email": "user@example.com",
  "first_name": "string",
  "last_name": "string",
  "locale": "string",
  "uid": "string",
  "inst_admin": true,
  "legal_admin": true,
  "send_admin": true,
  "data_admin": true
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
  "username": "string",
  "consent": {
    "version": "string",
    "status": "string"
  },
  "consent_accepted": "2019-08-24T14:15:22Z",
  "consent_rejected": "2019-08-24T14:15:22Z",
  "learner_id": "2df776db-09df-4cb9-a2af-db56cada6cb7",
  "last_login": "2019-08-24T14:15:22Z",
  "send": {},
  "email": "user@example.com",
  "ic_status": "string",
  "login_allowed": false,
  "first_name": "string",
  "last_name": "string",
  "locale": "string",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z",
  "uid": "string",
  "inst_admin": true,
  "legal_admin": true,
  "send_admin": true,
  "data_admin": true,
  "joined_at": "2019-08-24T14:15:22Z"
}
````

</details>

<div style="text-align:right">

[[top section]](#institution_learner_management) [[top page]](#table-of-contents) 
</div>
<br>

<!--- institution_learner_partial_update --->
## 12.5 Partial Update Institution Learner <a name="institution_learner_partial_update"></a>

API endpoint that updates Institution Learner data.

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
            <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/learner/{id}/</span></td>
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
                <td>consent</td>
                <td>object (InstitutionLearnerConsent)<br>Nullable.</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>email</strong><br><code>required</code></td>
                <td>string &lt;email&gt; (Email)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>first_name</td>
                <td>string (First name)<br><=150 characters></td>
                <td>-</td>
            </tr>
            <tr>
                <td>last_name</td>
                <td>string (Last name)<br><=150 characters</td>
                <td>-</td>
            </tr>
            <tr>
                <td>locale</td>
                <td>string (Local)<br>[1 .. 10] characters<br>Nullable.</td>
                <td>Default locale for this user.</td>
            </tr>
            <tr>
                <td><strong>uid</strong><br><code>required</code></td>
                <td>string (Uid)<br>[1 .. 255] characters</td>
                <td>Unique User Identifier for the institution.</td>
            </tr>
            <tr>
                <td>inst_admin</td>
                <td>boolean (Inst admin)</td>
                <td>Whether this user is administrator of the institution.</td>
            </tr>
             <tr>
                <td>legal_admin</td>
                <td>boolean (Inst admin)</td>
                <td>Whether this user can manage legal data of the institution.</td>
            </tr>
           <tr>
                <td>send_admin</td>
                <td>boolean (Send admin)</td>
                <td>Whether this user can manage SEND data of the institution.</td>
            </tr>
            <tr>
                <td>data_admin</td>
                <td>boolean (Data admin)</td>
                <td>Whether this user can manage the data of the institution.</td>
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
                <td>username</td>
                <td>string (Username)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>consent</td>
                <td>object (InstitutionLearnerConsent)<br>Nullable.</td>
                <td>-</td>
            </tr>
            <tr>
                <td>consent_accepted</td>
                <td>string &lt;date-time&gt; (Consent accepted)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>consent_rejected</td>
                <td>string &lt;date-time&gt; (Consent rejected)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>learner_id</td>
                <td>string &lt;uuid&gt; (Learner id)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>last_login</td>
                <td>string &lt;date-time&gt; (Last login)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>send</td>
                <td>object (Send)</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>email</strong><br><code>required</code></td>
                <td>string &lt;email&gt; (Email)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>ic_status</td>
                <td>string (IC status)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>login_allowed</td>
                <td>boolean (Login allowed)</td>
                <td>Default: false</td>
            </tr>
            <tr>
                <td>first_name</td>
                <td>string (First name)<br><=150 characters></td>
                <td>-</td>
            </tr>
            <tr>
                <td>last_name</td>
                <td>string (Last name)<br><=150 characters</td>
                <td>-</td>
            </tr>
            <tr>
                <td>locale</td>
                <td>string (Local)<br>[1 .. 10] characters<br>Nullable.</td>
                <td>Default locale for this user.</td>
            </tr>
            <tr>
                <td>created_at</td>
                <td>string &lt;date-time&gt; (Created at)</td>
                <td>Date when user was created.</td>
            </tr>
            <tr>
                <td>updated_at</td>
                <td>string &lt;date-time&gt; (Updated at)</td>
                <td>Last user modification.</td>
            </tr>
            <tr>
                <td><strong>uid</strong><br><code>required</code></td>
                <td>string (Uid)<br>[1 .. 255] characters</td>
                <td>Unique User Identifier for the institution.</td>
            </tr>
            <tr>
                <td>inst_admin</td>
                <td>boolean (Inst admin)</td>
                <td>Whether this user is administrator of the institution.</td>
            </tr>
             <tr>
                <td>legal_admin</td>
                <td>boolean (Inst admin)</td>
                <td>Whether this user can manage legal data of the institution.</td>
            </tr>
           <tr>
                <td>send_admin</td>
                <td>boolean (Send admin)</td>
                <td>Whether this user can manage SEND data of the institution.</td>
            </tr>
            <tr>
                <td>data_admin</td>
                <td>boolean (Data admin)</td>
                <td>Whether this user can manage the data of the institution.</td>
            </tr>
            <tr>
                <td>joined_at</td>
                <td>string &lt;date-time&gt; (Joined at)</td>
                <td>Date the learner joined for this institution.</td>
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
  "consent": {
    "version": "string"
  },
  "email": "user@example.com",
  "first_name": "string",
  "last_name": "string",
  "locale": "string",
  "uid": "string",
  "inst_admin": true,
  "legal_admin": true,
  "send_admin": true,
  "data_admin": true
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
  "username": "string",
  "consent": {
    "version": "string",
    "status": "string"
  },
  "consent_accepted": "2019-08-24T14:15:22Z",
  "consent_rejected": "2019-08-24T14:15:22Z",
  "learner_id": "2df776db-09df-4cb9-a2af-db56cada6cb7",
  "last_login": "2019-08-24T14:15:22Z",
  "send": {},
  "email": "user@example.com",
  "ic_status": "string",
  "login_allowed": false,
  "first_name": "string",
  "last_name": "string",
  "locale": "string",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z",
  "uid": "string",
  "inst_admin": true,
  "legal_admin": true,
  "send_admin": true,
  "data_admin": true,
  "joined_at": "2019-08-24T14:15:22Z"
}
````

</details>

<div style="text-align:right">

[[top section]](#institution_learner_management) [[top page]](#table-of-contents) 
</div>
<br>

<!--- institution_learner_delete --->
## 12.6 Delete Institution Learner <a name="institution_learner_delete"></a>

API endpoint that deletes Institution Learner.


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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/learner/{id}/</span></td>
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

[[top section]](#institution_learner_management) [[top page]](#table-of-contents) 
</div>
<br>


<!--- institution_learner_enrolment --->
## 12.7 Enrolment Institution Learner <a name="institution_learner_enrolment"></a>

API endpoint that allows learner enrolment status to be viewed.

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
            <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/learner/{id}/enrolment/</span></td>
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
                <td>username</td>
                <td>string (Username)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>consent</td>
                <td>object (InstitutionLearnerConsent)<br>Nullable.</td>
                <td>-</td>
            </tr>
            <tr>
                <td>consent_accepted</td>
                <td>string &lt;date-time&gt; (Consent accepted)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>consent_rejected</td>
                <td>string &lt;date-time&gt; (Consent rejected)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>learner_id</td>
                <td>string &lt;uuid&gt; (Learner id)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>last_login</td>
                <td>string &lt;date-time&gt; (Last login)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>send</td>
                <td>object (Send)</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>email</strong><br><code>required</code></td>
                <td>string &lt;email&gt; (Email)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>ic_status</td>
                <td>string (IC status)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>login_allowed</td>
                <td>boolean (Login allowed)</td>
                <td>Default: false</td>
            </tr>
            <tr>
                <td>first_name</td>
                <td>string (First name)<br><=150 characters></td>
                <td>-</td>
            </tr>
            <tr>
                <td>last_name</td>
                <td>string (Last name)<br><=150 characters</td>
                <td>-</td>
            </tr>
            <tr>
                <td>locale</td>
                <td>string (Local)<br>[1 .. 10] characters<br>Nullable.</td>
                <td>Default locale for this user.</td>
            </tr>
            <tr>
                <td>created_at</td>
                <td>string &lt;date-time&gt; (Created at)</td>
                <td>Date when user was created.</td>
            </tr>
            <tr>
                <td>updated_at</td>
                <td>string &lt;date-time&gt; (Updated at)</td>
                <td>Last user modification.</td>
            </tr>
            <tr>
                <td><strong>uid</strong><br><code>required</code></td>
                <td>string (Uid)<br>[1 .. 255] characters</td>
                <td>Unique User Identifier for the institution.</td>
            </tr>
            <tr>
                <td>inst_admin</td>
                <td>boolean (Inst admin)</td>
                <td>Whether this user is administrator of the institution.</td>
            </tr>
             <tr>
                <td>legal_admin</td>
                <td>boolean (Inst admin)</td>
                <td>Whether this user can manage legal data of the institution.</td>
            </tr>
           <tr>
                <td>send_admin</td>
                <td>boolean (Send admin)</td>
                <td>Whether this user can manage SEND data of the institution.</td>
            </tr>
            <tr>
                <td>data_admin</td>
                <td>boolean (Data admin)</td>
                <td>Whether this user can manage the data of the institution.</td>
            </tr>
            <tr>
                <td>joined_at</td>
                <td>string &lt;date-time&gt; (Joined at)</td>
                <td>Date the learner joined for this institution.</td>
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
  "username": "string",
  "consent": {
    "version": "string",
    "status": "string"
  },
  "consent_accepted": "2019-08-24T14:15:22Z",
  "consent_rejected": "2019-08-24T14:15:22Z",
  "learner_id": "2df776db-09df-4cb9-a2af-db56cada6cb7",
  "last_login": "2019-08-24T14:15:22Z",
  "send": {},
  "email": "user@example.com",
  "ic_status": "string",
  "login_allowed": false,
  "first_name": "string",
  "last_name": "string",
  "locale": "string",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z",
  "uid": "string",
  "inst_admin": true,
  "legal_admin": true,
  "send_admin": true,
  "data_admin": true,
  "joined_at": "2019-08-24T14:15:22Z"
}
````

</details>

<div style="text-align:right">

[[top section]](#institution_learner_management) [[top page]](#table-of-contents) 
</div>
<br>


<!--- institution_learner_ic_create --->
## 12.8 Create Institution Learner IC <a name="institution_learner_ic_create"></a>

API endpoint that manages learner informed consent.

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
            <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/learner/{id}/ic/</span></td>
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
                <td>consent</td>
                <td>object (InstitutionLearnerConsent)<br>Nullable.</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>email</strong><br><code>required</code></td>
                <td>string &lt;email&gt; (Email)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>first_name</td>
                <td>string (First name)<br><=150 characters></td>
                <td>-</td>
            </tr>
            <tr>
                <td>last_name</td>
                <td>string (Last name)<br><=150 characters</td>
                <td>-</td>
            </tr>
            <tr>
                <td>locale</td>
                <td>string (Local)<br>[1 .. 10] characters<br>Nullable.</td>
                <td>Default locale for this user.</td>
            </tr>
            <tr>
                <td><strong>uid</strong><br><code>required</code></td>
                <td>string (Uid)<br>[1 .. 255] characters</td>
                <td>Unique User Identifier for the institution.</td>
            </tr>
            <tr>
                <td>inst_admin</td>
                <td>boolean (Inst admin)</td>
                <td>Whether this user is administrator of the institution.</td>
            </tr>
             <tr>
                <td>legal_admin</td>
                <td>boolean (Inst admin)</td>
                <td>Whether this user can manage legal data of the institution.</td>
            </tr>
           <tr>
                <td>send_admin</td>
                <td>boolean (Send admin)</td>
                <td>Whether this user can manage SEND data of the institution.</td>
            </tr>
            <tr>
                <td>data_admin</td>
                <td>boolean (Data admin)</td>
                <td>Whether this user can manage the data of the institution.</td>
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
                <td>username</td>
                <td>string (Username)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>consent</td>
                <td>object (InstitutionLearnerConsent)<br>Nullable.</td>
                <td>-</td>
            </tr>
            <tr>
                <td>consent_accepted</td>
                <td>string &lt;date-time&gt; (Consent accepted)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>consent_rejected</td>
                <td>string &lt;date-time&gt; (Consent rejected)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>learner_id</td>
                <td>string &lt;uuid&gt; (Learner id)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>last_login</td>
                <td>string &lt;date-time&gt; (Last login)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>send</td>
                <td>object (Send)</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>email</strong><br><code>required</code></td>
                <td>string &lt;email&gt; (Email)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>ic_status</td>
                <td>string (IC status)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>login_allowed</td>
                <td>boolean (Login allowed)</td>
                <td>Default: false</td>
            </tr>
            <tr>
                <td>first_name</td>
                <td>string (First name)<br><=150 characters></td>
                <td>-</td>
            </tr>
            <tr>
                <td>last_name</td>
                <td>string (Last name)<br><=150 characters</td>
                <td>-</td>
            </tr>
            <tr>
                <td>locale</td>
                <td>string (Local)<br>[1 .. 10] characters<br>Nullable.</td>
                <td>Default locale for this user.</td>
            </tr>
            <tr>
                <td>created_at</td>
                <td>string &lt;date-time&gt; (Created at)</td>
                <td>Date when user was created.</td>
            </tr>
            <tr>
                <td>updated_at</td>
                <td>string &lt;date-time&gt; (Updated at)</td>
                <td>Last user modification.</td>
            </tr>
            <tr>
                <td><strong>uid</strong><br><code>required</code></td>
                <td>string (Uid)<br>[1 .. 255] characters</td>
                <td>Unique User Identifier for the institution.</td>
            </tr>
            <tr>
                <td>inst_admin</td>
                <td>boolean (Inst admin)</td>
                <td>Whether this user is administrator of the institution.</td>
            </tr>
             <tr>
                <td>legal_admin</td>
                <td>boolean (Inst admin)</td>
                <td>Whether this user can manage legal data of the institution.</td>
            </tr>
           <tr>
                <td>send_admin</td>
                <td>boolean (Send admin)</td>
                <td>Whether this user can manage SEND data of the institution.</td>
            </tr>
            <tr>
                <td>data_admin</td>
                <td>boolean (Data admin)</td>
                <td>Whether this user can manage the data of the institution.</td>
            </tr>
            <tr>
                <td>joined_at</td>
                <td>string &lt;date-time&gt; (Joined at)</td>
                <td>Date the learner joined for this institution.</td>
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
  "consent": {
    "version": "string"
  },
  "email": "user@example.com",
  "first_name": "string",
  "last_name": "string",
  "locale": "string",
  "uid": "string",
  "inst_admin": true,
  "legal_admin": true,
  "send_admin": true,
  "data_admin": true
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
  "username": "string",
  "consent": {
    "version": "string",
    "status": "string"
  },
  "consent_accepted": "2019-08-24T14:15:22Z",
  "consent_rejected": "2019-08-24T14:15:22Z",
  "learner_id": "2df776db-09df-4cb9-a2af-db56cada6cb7",
  "last_login": "2019-08-24T14:15:22Z",
  "send": {},
  "email": "user@example.com",
  "ic_status": "string",
  "login_allowed": false,
  "first_name": "string",
  "last_name": "string",
  "locale": "string",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z",
  "uid": "string",
  "inst_admin": true,
  "legal_admin": true,
  "send_admin": true,
  "data_admin": true,
  "joined_at": "2019-08-24T14:15:22Z"
}
````

</details>

<div style="text-align:right">

[[top section]](#institution_learner_management) [[top page]](#table-of-contents) 
</div>
<br>


<!--- institution_learner_ic_delete --->
## 12.9 Delete Institution Learner IC <a name="institution_learner_ic_delete"></a>

API endpoint that deletes Institution Learner Informed Consent.


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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/learner/{id}/ic/</span></td>
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

[[top section]](#institution_learner_management) [[top page]](#table-of-contents) 
</div>
<br><br>



# 13. Institution SEND Management <a name="institution_send_management"></a>
---
Set of API endpoint that allows Institution SEND Category Data to be viewed or edited.

  13.1 GET: [List Institution SEND](#institution_send_list)<br>
  13.2 POST: [Create Institution SEND](#institution_send_create)<br>
  13.3 GET: [Read Institution SEND](#institution_send_read)<br>
  13.4 PUT: [Update Institution SEND](#institution_send_update)<br>
  13.5 PATCH: [Partial Update Institution SEND](#institution_send_partial_update)<br>
  13.6 DEL: [Delete Institution SEND](#institution_send_delete)<br>
<div style="text-align:right">

[[top page]](#table-of-contents) 
</div>
<br>


<!--- institution_send_list --->
## 13.1 List Institution SEND <a name="institution_send_list"></a>

API endpoint that allows Institution SEND Categories to be listed.

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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/send/</span></td>
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
            <td>Array of objects (InstitutionSENDCategory)</td>
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
      "data": {},
      "description": "string",
      "created_at": "2019-08-24T14:15:22Z",
      "updated_at": "2019-08-24T14:15:22Z"
    }
  ]
}
 ````

</details>

<div style="text-align:right">

[[top section]](#institution_send_management) [[top page]](#table-of-contents) 
</div>
<br>


<!--- institution_send_create --->
## 13.2 Create Institution SEND <a name="institution_send_create"></a>

API endpoint that creates Institution SEND Category.

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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/send/</span></td>
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
                <td>data</td>
                <td>object (InstitutionSENDCategoryData)</td>
                <td>Default: {}</td>
            </tr>
            <tr>
                <td><strong>description</strong><br><code>required</code></td>
                <td>string (Description)<br>non-empty</td>
                <td>Category description.</td>
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
                <td>data</td>
                <td>object (InstitutionSENDCategoryData)</td>
                <td>Default: {}</td>
            </tr>
            <tr>
                <td><strong>description</strong><br><code>required</code></td>
                <td>string (Description)<br>non-empty</td>
                <td>Category description.</td>
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
  "data": {},
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
  "data": {},
  "description": "string",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
````
</details>

<div style="text-align:right">

[[top section]](#institution_send_management) [[top page]](#table-of-contents) 
</div>
<br>


<!--- institution_send_read --->
## 13.3 Read Institution SEND <a name="institution_send_read"></a>

API endpoint that allows access to Institution SEND Category data.

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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/send/{id}/</span></td>
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
                <td>data</td>
                <td>object (InstitutionSENDCategoryData)</td>
                <td>Default: {}</td>
            </tr>
            <tr>
                <td><strong>description</strong><br><code>required</code></td>
                <td>string (Description)<br>non-empty</td>
                <td>Category description.</td>
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
  "data": {},
  "description": "string",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
````
</details>


<div style="text-align:right">

[[top section]](#institution_send_management) [[top page]](#table-of-contents) 
</div>

<br>

<!--- institution_send_update --->
## 13.4 Update Institution SEND <a name="institution_send_update"></a>

API endpoint that updates Institution SEND Category data.

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
            <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/send/{id}/</span></td>
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
                <td>data</td>
                <td>object (InstitutionSENDCategoryData)</td>
                <td>Default: {}</td>
            </tr>
            <tr>
                <td><strong>description</strong><br><code>required</code></td>
                <td>string (Description)<br>non-empty</td>
                <td>Category description.</td>
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
                <td>data</td>
                <td>object (InstitutionSENDCategoryData)</td>
                <td>Default: {}</td>
            </tr>
            <tr>
                <td><strong>description</strong><br><code>required</code></td>
                <td>string (Description)<br>non-empty</td>
                <td>Category description.</td>
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
  "data": {},
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
  "data": {},
  "description": "string",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
````

</details>

<div style="text-align:right">

[[top section]](#institution_send_management) [[top page]](#table-of-contents) 
</div>
<br>

<!--- institution_send_partial_update --->
## 13.5 Partial Update Institution SEND <a name="institution_send_partial_update"></a>

API endpoint that updates Institution SEND Category data.

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
            <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/send/{id}/</span></td>
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
                <td>data</td>
                <td>object (InstitutionSENDCategoryData)</td>
                <td>Default: {}</td>
            </tr>
            <tr>
                <td><strong>description</strong><br><code>required</code></td>
                <td>string (Description)<br>non-empty</td>
                <td>Category description.</td>
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
                <td>data</td>
                <td>object (InstitutionSENDCategoryData)</td>
                <td>Default: {}</td>
            </tr>
            <tr>
                <td><strong>description</strong><br><code>required</code></td>
                <td>string (Description)<br>non-empty</td>
                <td>Category description.</td>
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
  "data": {},
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
  "data": {},
  "description": "string",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
````

</details>

<div style="text-align:right">

[[top section]](#institution_send_management) [[top page]](#table-of-contents) 
</div>
<br>

<!--- institution_send_delete --->
## 13.6 Delete Institution SEND <a name="institution_send_delete"></a>

API endpoint that deletes Institution SEND Category.


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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_institution_id}/send/{id}/</span></td>
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

[[top section]](#institution_send_management) [[top page]](#table-of-contents) 
</div>
<br><br>





# 14. Institution Learner SEND Management <a name="institution_learner_send_management"></a>
---
Set of API endpoint that allows Institution Learner SEND Data to be viewed or edited.

  14.1 GET: [List Institution Learner SEND](#institution_learner_send_list)<br>
  14.2 POST: [Create Institution Learner SEND](#institution_learner_send_create)<br>
  14.3 GET: [Read Institution Learner SEND](#institution_learner_send_read)<br>
  14.4 PUT: [Update Institution Learner SEND](#institution_learner_send_update)<br>
  14.5 PATCH: [Partial Update Institution Learner SEND](#institution_learner_send_partial_update)<br>
  14.6 DEL: [Delete Institution Learner SEND](#institution_learner_send_delete)<br>
<div style="text-align:right">

[[top page]](#table-of-contents) 
</div>
<br>


<!--- institution_learner_send_list --->
## 14.1 List Institution Learner SEND <a name="institution_learner_send_list"></a>

API endpoint that allows Institution Learner SEND to be listed.

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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_learner__institution_id}/learner/{parent_lookup_learner_id}/send/</span></td>
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
                <td><strong>parent_lookup_learner_id</strong><br><code>required</code></td>
                <td>string </td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_learner__institution_id</strong><br><code>required</code></td>
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
            <td>Array of objects (InstitutionSENDLearner)</td>
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
      "expires_at": "2019-08-24T14:15:22Z",
      "category": 0,
      "info": {
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
        "data": {},
        "description": "string",
        "created_at": "2019-08-24T14:15:22Z",
        "updated_at": "2019-08-24T14:15:22Z"
      }
    }
  ]
}
 ````

</details>

<div style="text-align:right">

[[top section]](#institution_learner_send_management) [[top page]](#table-of-contents) 
</div>
<br>


<!--- institution_learner_send_create --->
## 14.2 Create Institution Learner SEND <a name="institution_learner_send_create"></a>

API endpoint that creates Institution Learner SEND.

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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_learner__institution_id}/learner/{parent_lookup_learner_id}/send/</span></td>
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
                <td><strong>parent_lookup_learner_id</strong><br><code>required</code></td>
                <td>string </td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_learner__institution_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td>expires_at</td>
                <td>string &lt;date-time&gt; (Expires at)<br>Nullable.</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>category</strong><br><code>required</code></td>
                <td>integer (Category)</td>
                <td>Category description.</td>
            </tr>
            <tr>
                <td>info</td>
                <td>object (InstitutionSENDCategory)</td>
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
                <td>id</td>
                <td>integer (ID)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>expires_at</td>
                <td>string &lt;date-time&gt; (Expires at)<br>Nullable.</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>category</strong><br><code>required</code></td>
                <td>integer (Category)</td>
                <td>Category description.</td>
            </tr>
            <tr>
                <td>info</td>
                <td>object (InstitutionSENDCategory)</td>
                <td>-</td>
            </tr>
        </tbody>
    </table>
  {{</tab>}}
{{</tabs>}}

#### Request sample
`````json
{
  "expires_at": "2019-08-24T14:15:22Z",
  "category": 0,
  "info": {
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
    "data": {},
    "description": "string"
  }
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
  "expires_at": "2019-08-24T14:15:22Z",
  "category": 0,
  "info": {
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
    "data": {},
    "description": "string",
    "created_at": "2019-08-24T14:15:22Z",
    "updated_at": "2019-08-24T14:15:22Z"
  }
}
````
</details>

<div style="text-align:right">

[[top section]](#institution_learner_send_management) [[top page]](#table-of-contents) 
</div>
<br>


<!--- institution_learner_send_read --->
## 14.3 Read Institution Learner SEND <a name="institution_learner_send_read"></a>

API endpoint that allows access to Institution Learner SEND data.

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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_learner__institution_id}/learner/{parent_lookup_learner_id}/send/{id}/</span></td>
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
                <td><strong>parent_lookup_learner_id</strong><br><code>required</code></td>
                <td>string </td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_learner__institution_id</strong><br><code>required</code></td>
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
                <td>expires_at</td>
                <td>string &lt;date-time&gt; (Expires at)<br>Nullable.</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>category</strong><br><code>required</code></td>
                <td>integer (Category)</td>
                <td>Category description.</td>
            </tr>
            <tr>
                <td>info</td>
                <td>object (InstitutionSENDCategory)</td>
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
  "expires_at": "2019-08-24T14:15:22Z",
  "category": 0,
  "info": {
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
    "data": {},
    "description": "string",
    "created_at": "2019-08-24T14:15:22Z",
    "updated_at": "2019-08-24T14:15:22Z"
  }
}
````
</details>


<div style="text-align:right">

[[top section]](#institution_learner_send_management) [[top page]](#table-of-contents) 
</div>

<br>

<!--- institution_learner_send_update --->
## 14.4 Update Institution Learner SEND <a name="institution_learner_send_update"></a>

API endpoint that updates Institution Learner SEND data.

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
            <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_learner__institution_id}/learner/{parent_lookup_learner_id}/send/{id}/</span></td>
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
                <td><strong>parent_lookup_learner_id</strong><br><code>required</code></td>
                <td>string </td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_learner__institution_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td>expires_at</td>
                <td>string &lt;date-time&gt; (Expires at)<br>Nullable.</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>category</strong><br><code>required</code></td>
                <td>integer (Category)</td>
                <td>Category description.</td>
            </tr>
            <tr>
                <td>info</td>
                <td>object (InstitutionSENDCategory)</td>
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
                <td>id</td>
                <td>integer (ID)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>expires_at</td>
                <td>string &lt;date-time&gt; (Expires at)<br>Nullable.</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>category</strong><br><code>required</code></td>
                <td>integer (Category)</td>
                <td>Category description.</td>
            </tr>
            <tr>
                <td>info</td>
                <td>object (InstitutionSENDCategory)</td>
                <td>-</td>
            </tr>
        </tbody>
    </table>
  {{</tab>}}
{{</tabs>}}

#### Request sample

````json
{
  "expires_at": "2019-08-24T14:15:22Z",
  "category": 0,
  "info": {
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
    "data": {},
    "description": "string"
  }
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
  "expires_at": "2019-08-24T14:15:22Z",
  "category": 0,
  "info": {
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
    "data": {},
    "description": "string",
    "created_at": "2019-08-24T14:15:22Z",
    "updated_at": "2019-08-24T14:15:22Z"
  }
}
````

</details>

<div style="text-align:right">

[[top section]](#institution_learner_send_management) [[top page]](#table-of-contents) 
</div>
<br>

<!--- institution_learner_send_partial_update --->
## 14.5 Partial Update Institution Learner SEND <a name="institution_learner_send_partial_update"></a>

API endpoint that updates Institution Learner SEND data.

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
            <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_learner__institution_id}/learner/{parent_lookup_learner_id}/send/{id}/</span></td>
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
                <td><strong>parent_lookup_learner_id</strong><br><code>required</code></td>
                <td>string </td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_learner__institution_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td>expires_at</td>
                <td>string &lt;date-time&gt; (Expires at)<br>Nullable.</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>category</strong><br><code>required</code></td>
                <td>integer (Category)</td>
                <td>Category description.</td>
            </tr>
            <tr>
                <td>info</td>
                <td>object (InstitutionSENDCategory)</td>
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
                <td>id</td>
                <td>integer (ID)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>expires_at</td>
                <td>string &lt;date-time&gt; (Expires at)<br>Nullable.</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>category</strong><br><code>required</code></td>
                <td>integer (Category)</td>
                <td>Category description.</td>
            </tr>
            <tr>
                <td>info</td>
                <td>object (InstitutionSENDCategory)</td>
                <td>-</td>
            </tr>
        </tbody>
    </table>
  {{</tab>}}
{{</tabs>}}

#### Request sample

````json
{
  "expires_at": "2019-08-24T14:15:22Z",
  "category": 0,
  "info": {
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
    "data": {},
    "description": "string"
  }
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
  "expires_at": "2019-08-24T14:15:22Z",
  "category": 0,
  "info": {
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
    "data": {},
    "description": "string",
    "created_at": "2019-08-24T14:15:22Z",
    "updated_at": "2019-08-24T14:15:22Z"
  }
}
````

</details>

<div style="text-align:right">

[[top section]](#institution_learner_send_management) [[top page]](#table-of-contents) 
</div>
<br>

<!--- institution_learner_send_delete --->
## 14.6 Delete Institution Learner SEND <a name="institution_learner_send_delete"></a>

API endpoint that deletes Institution Learner SEND.


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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_learner__institution_id}/learner/{parent_lookup_learner_id}/send/{id}/</span></td>
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
                <td><strong>parent_lookup_learner_id</strong><br><code>required</code></td>
                <td>string </td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_learner__institution_id</strong><br><code>required</code></td>
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

[[top section]](#institution_learner_send_management) [[top page]](#table-of-contents) 
</div>
<br><br>




# 15. Institution Course Instructor Management <a name="institution_course_instructor_management"></a>
---
Set of API endpoint that allows Institution Course Instructors to be viewed or edited.

  15.1 GET: [List Institution Course Instructor](#institution_course_instructor_list)<br>
  15.2 POST: [Create Institution Course Instructor](#institution_course_instructor_create)<br>
  15.3 GET: [Read Institution Course Instructor](#institution_course_instructor_read)<br>
  15.4 PUT: [Update Institution Course Instructor](#institution_course_instructor_update)<br>
  15.5 PATCH: [Partial Update Institution Course Instructor](#institution_course_instructor_partial_update)<br>
  15.6 DEL: [Delete Institution Course Instructor](#institution_course_instructor_delete)<br>
<div style="text-align:right">

[[top page]](#table-of-contents) 
</div>
<br>


<!--- institution_course_instructor_list --->
## 15.1 List Institution Course Instructor <a name="institution_course_instructor_list"></a>

API endpoint that allows Institution Course Instructors to be listed.

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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_vle__institution_id}/course/{parent_lookup_id}/instructor/</span></td>
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
            <td>Array of objects (InstitutionInstructor)</td>
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
      "username": "string",
      "uid": "string",
      "first_name": "string",
      "last_name": "string",
      "email": "user@example.com",
      "created_at": "2019-08-24T14:15:22Z",
      "updated_at": "2019-08-24T14:15:22Z"
    }
  ]
}
````

</details>

<div style="text-align:right">

[[top section]](#institution_course_instructor_management) [[top page]](#table-of-contents) 
</div>
<br>


<!--- institution_course_instructor_create --->
## 15.2 Create Institution Course Instructor <a name="institution_course_instructor_create"></a>

API endpoint that creates Institution Course Instructor.

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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_vle__institution_id}/course/{parent_lookup_id}/instructor/</span></td>
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
                <td><strong>parent_lookup_vle__institution_id</strong><br><code>required</code></td>
                <td>string </td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>uid</strong><br><code>required</code></td>
                <td>string (Uid)<br>non-empty </td>
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
                <td>id</td>
                <td>integer (ID)</td>
                <td>-</td>
            </tr>
             <tr>
                <td>username</td>
                <td>string (Username)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>uid</strong><br><code>required</code></td>
                <td>string (Uid)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>first_name</td>
                <td>string (First name)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>last_name</td>
                <td>string (Last name)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>email</td>
                <td>string &lt;email&gt; (Email)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>created_at</td>
                <td>string &lt;date-time&gt; (Created at)</td>
                <td>Date when user was created.</td>
            </tr>
            <tr>
                <td>updated_at</td>
                <td>string &lt;date-time&gt; (Updated at)</td>
                <td>Last user modification.</td>
            </tr>
        </tbody>
    </table>
  {{</tab>}}
{{</tabs>}}

#### Request sample
`````json
{
  "uid": "string"
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
  "username": "string",
  "uid": "string",
  "first_name": "string",
  "last_name": "string",
  "email": "user@example.com",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
````
</details>

<div style="text-align:right">

[[top section]](#institution_course_instructor_management) [[top page]](#table-of-contents) 
</div>
<br>


<!--- institution_course_instructor_read --->
## 15.3 Read Institution Course Instructor <a name="institution_course_instructor_read"></a>

API endpoint that allows access to Institution Course Instructor data.

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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_vle__institution_id}/course/{parent_lookup_id}/instructor/{id}/</span></td>
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
                <td>string </td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_vle__institution_id</strong><br><code>required</code></td>
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
                <td>integer (ID)</td>
                <td>-</td>
            </tr>
             <tr>
                <td>username</td>
                <td>string (Username)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>uid</strong><br><code>required</code></td>
                <td>string (Uid)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>first_name</td>
                <td>string (First name)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>last_name</td>
                <td>string (Last name)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>email</td>
                <td>string &lt;email&gt; (Email)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>created_at</td>
                <td>string &lt;date-time&gt; (Created at)</td>
                <td>Date when user was created.</td>
            </tr>
            <tr>
                <td>updated_at</td>
                <td>string &lt;date-time&gt; (Updated at)</td>
                <td>Last user modification.</td>
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
  "username": "string",
  "uid": "string",
  "first_name": "string",
  "last_name": "string",
  "email": "user@example.com",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
````
</details>


<div style="text-align:right">

[[top section]](#institution_course_instructor_management) [[top page]](#table-of-contents) 
</div>

<br>

<!--- institution_course_instructor_update --->
## 15.4 Update Institution Course Instructor <a name="institution_course_instructor_update"></a>

API endpoint that updates Institution Course Instructor data.

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
            <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_vle__institution_id}/course/{parent_lookup_id}/instructor/{id}/</span></td>
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
                <td>string </td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_vle__institution_id</strong><br><code>required</code></td>
                <td>string </td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>uid</strong><br><code>required</code></td>
                <td>string (Uid)<br>non-empty </td>
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
                <td>id</td>
                <td>integer (ID)</td>
                <td>-</td>
            </tr>
             <tr>
                <td>username</td>
                <td>string (Username)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>uid</strong><br><code>required</code></td>
                <td>string (Uid)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>first_name</td>
                <td>string (First name)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>last_name</td>
                <td>string (Last name)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>email</td>
                <td>string &lt;email&gt; (Email)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>created_at</td>
                <td>string &lt;date-time&gt; (Created at)</td>
                <td>Date when user was created.</td>
            </tr>
            <tr>
                <td>updated_at</td>
                <td>string &lt;date-time&gt; (Updated at)</td>
                <td>Last user modification.</td>
            </tr>
        </tbody>
    </table>
  {{</tab>}}
{{</tabs>}}

#### Request sample

````json
{
  "uid": "string"
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
  "username": "string",
  "uid": "string",
  "first_name": "string",
  "last_name": "string",
  "email": "user@example.com",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
````

</details>

<div style="text-align:right">

[[top section]](#institution_course_instructor_management) [[top page]](#table-of-contents) 
</div>
<br>

<!--- institution_course_instructor_partial_update --->
## 15.5 Partial Update Institution Course Instructor <a name="institution_course_instructor_partial_update"></a>

API endpoint that updates Institution Course Instructor data.

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
        <tr>
            <td>Path</td>
            <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_vle__institution_id}/course/{parent_lookup_id}/instructor/{id}/</span></td>
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
                <td>string </td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_vle__institution_id</strong><br><code>required</code></td>
                <td>string </td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>uid</strong><br><code>required</code></td>
                <td>string (Uid)<br>non-empty </td>
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
                <td>id</td>
                <td>integer (ID)</td>
                <td>-</td>
            </tr>
             <tr>
                <td>username</td>
                <td>string (Username)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>uid</strong><br><code>required</code></td>
                <td>string (Uid)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>first_name</td>
                <td>string (First name)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>last_name</td>
                <td>string (Last name)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>email</td>
                <td>string &lt;email&gt; (Email)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>created_at</td>
                <td>string &lt;date-time&gt; (Created at)</td>
                <td>Date when user was created.</td>
            </tr>
            <tr>
                <td>updated_at</td>
                <td>string &lt;date-time&gt; (Updated at)</td>
                <td>Last user modification.</td>
            </tr>
        </tbody>
    </table>
  {{</tab>}}
{{</tabs>}}

#### Request sample

````json
{
  "uid": "string"
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
  "username": "string",
  "uid": "string",
  "first_name": "string",
  "last_name": "string",
  "email": "user@example.com",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
````

</details>

<div style="text-align:right">

[[top section]](#institution_course_instructor_management) [[top page]](#table-of-contents) 
</div>
<br>

<!--- institution_course_instructor_delete --->
## 15.6 Delete Institution Course Instructor <a name="institution_course_instructor_delete"></a>

API endpoint that deletes Institution Course Instructor.


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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_vle__institution_id}/course/{parent_lookup_id}/instructor/{id}/</span></td>
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
                <td>string </td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_vle__institution_id</strong><br><code>required</code></td>
                <td>string </td>
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

[[top section]](#institution_course_instructor_management) [[top page]](#table-of-contents) 
</div>
<br><br>



# 16. Institution Course Learner Management <a name="institution_course_learner_management"></a>
---
Set of API endpoint that allows Institution Course Learners to be viewed or edited.

  16.1 GET: [List Institution Course Learner](#institution_course_learner_list)<br>
  16.2 POST: [Create Institution Course Learner](#institution_course_learner_create)<br>
  16.3 GET: [Read Institution Course Learner](#institution_course_learner_read)<br>
  16.4 PUT: [Update Institution Course Learner](#institution_course_learner_update)<br>
  16.5 PATCH: [Partial Update Institution Course Learner](#institution_course_learner_partial_update)<br>
  16.6 DEL: [Delete Institution Course Learner](#institution_course_learner_delete)<br>
<div style="text-align:right">

[[top page]](#table-of-contents) 
</div>
<br>


<!--- institution_course_learner_list --->
## 16.1 List Institution Course Learner <a name="institution_course_learner_list"></a>

API endpoint that allows Institution Course Learners to be listed.

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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_vle__institution_id}/course/{parent_lookup_id}/learner/</span></td>
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
            <td>Array of objects (InstitutionLearner)</td>
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
      "username": "string",
      "uid": "string",
      "first_name": "string",
      "last_name": "string",
      "locale": "string",
      "consent": {
        "version": "string",
        "status": "string"
      },
      "consent_accepted": "2019-08-24T14:15:22Z",
      "consent_rejected": "2019-08-24T14:15:22Z",
      "learner_id": "2df776db-09df-4cb9-a2af-db56cada6cb7",
      "last_login": "2019-08-24T14:15:22Z",
      "send": {},
      "email": "user@example.com",
      "ic_status": "string",
      "login_allowed": false,
      "created_at": "2019-08-24T14:15:22Z",
      "updated_at": "2019-08-24T14:15:22Z",
      "joined_at": "2019-08-24T14:15:22Z"
    }
  ]
}
 ````

</details>

<div style="text-align:right">

[[top section]](#institution_course_learner_management) [[top page]](#table-of-contents) 
</div>
<br>


<!--- institution_course_learner_create --->
## 16.2 Create Institution Course Learner <a name="institution_course_learner_create"></a>

API endpoint that creates Institution Course Learner.

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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_vle__institution_id}/course/{parent_lookup_id}/learner/</span></td>
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
                <td><strong>parent_lookup_vle__institution_id</strong><br><code>required</code></td>
                <td>string </td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td>institution</td>
                <td>object (Institution)</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>uid</strong><br><code>required</code></td>
                <td>string (Uid)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>consent</td>
                <td>object (InstitutionLearnerConsent)<br>Nullable.</td>
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
                <td>username</td>
                <td>string (Username)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>uid</strong><br><code>required</code></td>
                <td>string (Uid)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>first_name</td>
                <td>string (First name)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>last_name</td>
                <td>string (Last name)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>locale</td>
                <td>string (Local)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>consent</td>
                <td>object (InstitutionLearnerConsent)<br>Nullable.</td>
                <td>-</td>
            </tr>
            <tr>
                <td>consent_accepted</td>
                <td>string &lt;date-time&gt; (Consent accepted)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>consent_rejected</td>
                <td>string &lt;date-time&gt; (Consent rejected)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>learner_id</td>
                <td>string &lt;uuid&gt; (Learner id)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>last_login</td>
                <td>string &lt;date-time&gt; (Last login)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>send</td>
                <td>object (Send)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>email</td>
                <td>string &lt;email&gt; (Email)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>ic_status</td>
                <td>string (IC status)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>login_allowed</td>
                <td>boolean (Login allowed)</td>
                <td>Default: false</td>
            </tr>
            <tr>
                <td>created_at</td>
                <td>string &lt;date-time&gt; (Created at)</td>
                <td>Date when user was created.</td>
            </tr>
            <tr>
                <td>updated_at</td>
                <td>string &lt;date-time&gt; (Updated at)</td>
                <td>Last user modification.</td>
            </tr>
            <tr>
                <td>joined_at</td>
                <td>string &lt;date-time&gt; (Joined at)</td>
                <td>Date the learner joined for this institution.</td>
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
  "uid": "string",
  "consent": {
    "version": "string"
  }
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
  "username": "string",
  "uid": "string",
  "first_name": "string",
  "last_name": "string",
  "locale": "string",
  "consent": {
    "version": "string",
    "status": "string"
  },
  "consent_accepted": "2019-08-24T14:15:22Z",
  "consent_rejected": "2019-08-24T14:15:22Z",
  "learner_id": "2df776db-09df-4cb9-a2af-db56cada6cb7",
  "last_login": "2019-08-24T14:15:22Z",
  "send": {},
  "email": "user@example.com",
  "ic_status": "string",
  "login_allowed": false,
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z",
  "joined_at": "2019-08-24T14:15:22Z"
}
````
</details>

<div style="text-align:right">

[[top section]](#institution_course_learner_management) [[top page]](#table-of-contents) 
</div>
<br>


<!--- institution_course_learner_read --->
## 16.3 Read Institution Course Learner <a name="institution_course_learner_read"></a>

API endpoint that allows access to Institution Course Learner data.

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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_vle__institution_id}/course/{parent_lookup_id}/learner/{id}/</span></td>
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
                <td>string </td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_vle__institution_id</strong><br><code>required</code></td>
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
                <td>integer (ID)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>institution</td>
                <td>object (Institution)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>username</td>
                <td>string (Username)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>uid</strong><br><code>required</code></td>
                <td>string (Uid)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>first_name</td>
                <td>string (First name)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>last_name</td>
                <td>string (Last name)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>locale</td>
                <td>string (Local)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>consent</td>
                <td>object (InstitutionLearnerConsent)<br>Nullable.</td>
                <td>-</td>
            </tr>
            <tr>
                <td>consent_accepted</td>
                <td>string &lt;date-time&gt; (Consent accepted)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>consent_rejected</td>
                <td>string &lt;date-time&gt; (Consent rejected)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>learner_id</td>
                <td>string &lt;uuid&gt; (Learner id)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>last_login</td>
                <td>string &lt;date-time&gt; (Last login)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>send</td>
                <td>object (Send)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>email</td>
                <td>string &lt;email&gt; (Email)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>ic_status</td>
                <td>string (IC status)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>login_allowed</td>
                <td>boolean (Login allowed)</td>
                <td>Default: false</td>
            </tr>
            <tr>
                <td>created_at</td>
                <td>string &lt;date-time&gt; (Created at)</td>
                <td>Date when user was created.</td>
            </tr>
            <tr>
                <td>updated_at</td>
                <td>string &lt;date-time&gt; (Updated at)</td>
                <td>Last user modification.</td>
            </tr>
            <tr>
                <td>joined_at</td>
                <td>string &lt;date-time&gt; (Joined at)</td>
                <td>Date the learner joined for this institution.</td>
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
  "username": "string",
  "uid": "string",
  "first_name": "string",
  "last_name": "string",
  "locale": "string",
  "consent": {
    "version": "string",
    "status": "string"
  },
  "consent_accepted": "2019-08-24T14:15:22Z",
  "consent_rejected": "2019-08-24T14:15:22Z",
  "learner_id": "2df776db-09df-4cb9-a2af-db56cada6cb7",
  "last_login": "2019-08-24T14:15:22Z",
  "send": {},
  "email": "user@example.com",
  "ic_status": "string",
  "login_allowed": false,
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z",
  "joined_at": "2019-08-24T14:15:22Z"
}
````
</details>


<div style="text-align:right">

[[top section]](#institution_course_learner_management) [[top page]](#table-of-contents) 
</div>

<br>

<!--- institution_course_learner_update --->
## 16.4 Update Institution Course Learner <a name="institution_course_learner_update"></a>

API endpoint that updates Institution Course Learner data.

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
            <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_vle__institution_id}/course/{parent_lookup_id}/learner/{id}/</span></td>
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
                <td>string </td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_vle__institution_id</strong><br><code>required</code></td>
                <td>string </td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td>institution</td>
                <td>object (Institution)</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>uid</strong><br><code>required</code></td>
                <td>string (Uid)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>consent</td>
                <td>object (InstitutionLearnerConsent)<br>Nullable.</td>
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
                <td>username</td>
                <td>string (Username)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>uid</strong><br><code>required</code></td>
                <td>string (Uid)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>first_name</td>
                <td>string (First name)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>last_name</td>
                <td>string (Last name)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>locale</td>
                <td>string (Local)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>consent</td>
                <td>object (InstitutionLearnerConsent)<br>Nullable.</td>
                <td>-</td>
            </tr>
            <tr>
                <td>consent_accepted</td>
                <td>string &lt;date-time&gt; (Consent accepted)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>consent_rejected</td>
                <td>string &lt;date-time&gt; (Consent rejected)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>learner_id</td>
                <td>string &lt;uuid&gt; (Learner id)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>last_login</td>
                <td>string &lt;date-time&gt; (Last login)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>send</td>
                <td>object (Send)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>email</td>
                <td>string &lt;email&gt; (Email)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>ic_status</td>
                <td>string (IC status)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>login_allowed</td>
                <td>boolean (Login allowed)</td>
                <td>Default: false</td>
            </tr>
            <tr>
                <td>created_at</td>
                <td>string &lt;date-time&gt; (Created at)</td>
                <td>Date when user was created.</td>
            </tr>
            <tr>
                <td>updated_at</td>
                <td>string &lt;date-time&gt; (Updated at)</td>
                <td>Last user modification.</td>
            </tr>
            <tr>
                <td>joined_at</td>
                <td>string &lt;date-time&gt; (Joined at)</td>
                <td>Date the learner joined for this institution.</td>
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
  "uid": "string",
  "consent": {
    "version": "string"
  }
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
  "username": "string",
  "uid": "string",
  "first_name": "string",
  "last_name": "string",
  "locale": "string",
  "consent": {
    "version": "string",
    "status": "string"
  },
  "consent_accepted": "2019-08-24T14:15:22Z",
  "consent_rejected": "2019-08-24T14:15:22Z",
  "learner_id": "2df776db-09df-4cb9-a2af-db56cada6cb7",
  "last_login": "2019-08-24T14:15:22Z",
  "send": {},
  "email": "user@example.com",
  "ic_status": "string",
  "login_allowed": false,
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z",
  "joined_at": "2019-08-24T14:15:22Z"
}
````

</details>

<div style="text-align:right">

[[top section]](#institution_course_learner_management) [[top page]](#table-of-contents) 
</div>
<br>

<!--- institution_course_learner_partial_update --->
## 16.5 Partial Update Institution Course Learner <a name="institution_course_learner_partial_update"></a>

API endpoint that updates Institution Course Learner data.

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
            <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_vle__institution_id}/course/{parent_lookup_id}/learner/{id}/</span></td>
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
                <td>string </td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_vle__institution_id</strong><br><code>required</code></td>
                <td>string </td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td>institution</td>
                <td>object (Institution)</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>uid</strong><br><code>required</code></td>
                <td>string (Uid)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>consent</td>
                <td>object (InstitutionLearnerConsent)<br>Nullable.</td>
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
                <td>username</td>
                <td>string (Username)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>uid</strong><br><code>required</code></td>
                <td>string (Uid)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>first_name</td>
                <td>string (First name)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>last_name</td>
                <td>string (Last name)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>locale</td>
                <td>string (Local)<br>non-empty</td>
                <td>-</td>
            </tr>
            <tr>
                <td>consent</td>
                <td>object (InstitutionLearnerConsent)<br>Nullable.</td>
                <td>-</td>
            </tr>
            <tr>
                <td>consent_accepted</td>
                <td>string &lt;date-time&gt; (Consent accepted)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>consent_rejected</td>
                <td>string &lt;date-time&gt; (Consent rejected)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>learner_id</td>
                <td>string &lt;uuid&gt; (Learner id)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>last_login</td>
                <td>string &lt;date-time&gt; (Last login)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>send</td>
                <td>object (Send)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>email</td>
                <td>string &lt;email&gt; (Email)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>ic_status</td>
                <td>string (IC status)<br>non-empty </td>
                <td>-</td>
            </tr>
            <tr>
                <td>login_allowed</td>
                <td>boolean (Login allowed)</td>
                <td>Default: false</td>
            </tr>
            <tr>
                <td>created_at</td>
                <td>string &lt;date-time&gt; (Created at)</td>
                <td>Date when user was created.</td>
            </tr>
            <tr>
                <td>updated_at</td>
                <td>string &lt;date-time&gt; (Updated at)</td>
                <td>Last user modification.</td>
            </tr>
            <tr>
                <td>joined_at</td>
                <td>string &lt;date-time&gt; (Joined at)</td>
                <td>Date the learner joined for this institution.</td>
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
  "uid": "string",
  "consent": {
    "version": "string"
  }
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
  "username": "string",
  "uid": "string",
  "first_name": "string",
  "last_name": "string",
  "locale": "string",
  "consent": {
    "version": "string",
    "status": "string"
  },
  "consent_accepted": "2019-08-24T14:15:22Z",
  "consent_rejected": "2019-08-24T14:15:22Z",
  "learner_id": "2df776db-09df-4cb9-a2af-db56cada6cb7",
  "last_login": "2019-08-24T14:15:22Z",
  "send": {},
  "email": "user@example.com",
  "ic_status": "string",
  "login_allowed": false,
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z",
  "joined_at": "2019-08-24T14:15:22Z"
}
````

</details>

<div style="text-align:right">

[[top section]](#institution_course_learner_management) [[top page]](#table-of-contents) 
</div>
<br>

<!--- institution_course_learner_delete --->
## 16.6 Delete Institution Course Learner <a name="institution_course_learner_delete"></a>

API endpoint that deletes Institution Course Learner.


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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_vle__institution_id}/course/{parent_lookup_id}/learner/{id}/</span></td>
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
                <td>string </td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_vle__institution_id</strong><br><code>required</code></td>
                <td>string </td>
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

[[top section]](#institution_course_learner_management) [[top page]](#table-of-contents) 
</div>
<br><br>




# 17. Institution Course Activity Management <a name="institution_course_activity_management"></a>
---
Set of API endpoint that allows Institution Course Activity Data to be viewed or edited.

  17.1 GET: [List Institution Course Activity](#institution_course_activity_list)<br>
  17.2 POST: [Create Institution Course Activity](#institution_course_activity_create)<br>
  17.3 GET: [Read Institution Course Activity](#institution_course_activity_read)<br>
  17.4 PUT: [Update Institution Course Activity](#institution_course_activity_update)<br>
  17.5 PATCH: [Partial Update Institution Course Activity](#institution_course_activity_partial_update)<br>
  17.6 DEL: [Delete Institution Course Activity](#institution_course_activity_delete)<br>
<div style="text-align:right">

[[top page]](#table-of-contents) 
</div>
<br>


<!--- institution_course_activity_list --->
## 17.1 List Institution Course Activity <a name="institution_course_activity_list"></a>

API endpoint that allows Institution Course Activity to be listed.

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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_vle__institution_id}/course/{parent_lookup_course_id}/activity/</span></td>
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
                <td><strong>parent_lookup_course_id</strong><br><code>required</code></td>
                <td>string </td>
                <td>Request path parameter.</td>
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
            <td>Array of objects (InstitutionCourseActivity)</td>
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
      "vle_activity_type": "string",
      "vle_activity_id": "string",
      "name": "string",
      "start": "string",
      "end": "string",
      "description": "string",
      "enabled": true,
      "conf": "string",
      "created_at": "2019-08-24T14:15:22Z",
      "updated_at": "2019-08-24T14:15:22Z"
    }
  ]
}
 ````

</details>

<div style="text-align:right">

[[top section]](#institution_course_activity_management) [[top page]](#table-of-contents) 
</div>
<br>


<!--- institution_course_activity_create --->
## 17.2 Create Institution Course Activity <a name="institution_course_activity_create"></a>

API endpoint that creates Institution Course Activity.

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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_vle__institution_id}/course/{parent_lookup_course_id}/activity/</span></td>
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
                <td><strong>parent_lookup_course_id</strong><br><code>required</code></td>
                <td>string </td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_vle__institution_id</strong><br><code>required</code></td>
                <td>string </td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td>enabled</td>
                <td>boolean (Enabled)</td>
                <td>Whether this activity is enabled or not.</td>
            </tr>
            <tr>
                <td>conf</td>
                <td>string (Conf)<br>Nullable.</td>
                <td>Activity conf.</td>
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
                <td>vle_activity_type</td>
                <td>string (VLE activity type)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>vle_activity_id</td>
                <td>string (VLE activity ID)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>name</td>
                <td>string (Name)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>start</td>
                <td>string (Start)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>end</td>
                <td>string (End)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>description</td>
                <td>string (Description)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>enabled</td>
                <td>boolean (Enabled)</td>
                <td>Whether this activity is enabled or not.</td>
            </tr>
            <tr>
                <td>conf</td>
                <td>string (Conf)<br>Nullable.</td>
                <td>Activity conf.</td>
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
  "enabled": true,
  "conf": "string"
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
  "vle_activity_type": "string",
  "vle_activity_id": "string",
  "name": "string",
  "start": "string",
  "end": "string",
  "description": "string",
  "enabled": true,
  "conf": "string",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
````
</details>

<div style="text-align:right">

[[top section]](#institution_course_activity_management) [[top page]](#table-of-contents) 
</div>
<br>


<!--- institution_course_activity_read --->
## 17.3 Read Institution Course Activity <a name="institution_course_activity_read"></a>

API endpoint that allows access to Institution Course Activity data.

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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_vle__institution_id}/course/{parent_lookup_course_id}/activity/{id}/</span></td>
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
                <td><strong>parent_lookup_course_id</strong><br><code>required</code></td>
                <td>string </td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_vle__institution_id</strong><br><code>required</code></td>
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
                <td>integer (ID)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>vle_activity_type</td>
                <td>string (VLE activity type)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>vle_activity_id</td>
                <td>string (VLE activity ID)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>name</td>
                <td>string (Name)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>start</td>
                <td>string (Start)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>end</td>
                <td>string (End)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>description</td>
                <td>string (Description)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>enabled</td>
                <td>boolean (Enabled)</td>
                <td>Whether this activity is enabled or not.</td>
            </tr>
            <tr>
                <td>conf</td>
                <td>string (Conf)<br>Nullable.</td>
                <td>Activity conf.</td>
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
  "vle_activity_type": "string",
  "vle_activity_id": "string",
  "name": "string",
  "start": "string",
  "end": "string",
  "description": "string",
  "enabled": true,
  "conf": "string",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
````
</details>


<div style="text-align:right">

[[top section]](#institution_course_activity_management) [[top page]](#table-of-contents) 
</div>

<br>

<!--- institution_course_activity_update --->
## 17.4 Update Institution Course Activity <a name="institution_course_activity_update"></a>

API endpoint that updates Institution Course Activity data.

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
            <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_vle__institution_id}/course/{parent_lookup_course_id}/activity/{id}/</span></td>
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
                <td><strong>parent_lookup_course_id</strong><br><code>required</code></td>
                <td>string </td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_vle__institution_id</strong><br><code>required</code></td>
                <td>string </td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td>enabled</td>
                <td>boolean (Enabled)</td>
                <td>Whether this activity is enabled or not.</td>
            </tr>
            <tr>
                <td>conf</td>
                <td>string (Conf)<br>Nullable.</td>
                <td>Activity conf.</td>
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
                <td>vle_activity_type</td>
                <td>string (VLE activity type)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>vle_activity_id</td>
                <td>string (VLE activity ID)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>name</td>
                <td>string (Name)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>start</td>
                <td>string (Start)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>end</td>
                <td>string (End)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>description</td>
                <td>string (Description)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>enabled</td>
                <td>boolean (Enabled)</td>
                <td>Whether this activity is enabled or not.</td>
            </tr>
            <tr>
                <td>conf</td>
                <td>string (Conf)<br>Nullable.</td>
                <td>Activity conf.</td>
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
  "enabled": true,
  "conf": "string"
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
  "vle_activity_type": "string",
  "vle_activity_id": "string",
  "name": "string",
  "start": "string",
  "end": "string",
  "description": "string",
  "enabled": true,
  "conf": "string",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
````

</details>

<div style="text-align:right">

[[top section]](#institution_course_activity_management) [[top page]](#table-of-contents) 
</div>
<br>

<!--- institution_course_activity_partial_update --->
## 17.5 Partial Update Institution Course Activity <a name="institution_course_activity_partial_update"></a>

API endpoint that updates Institution Course Activity data.

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
            <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_vle__institution_id}/course/{parent_lookup_course_id}/activity/{id}/</span></td>
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
                <td><strong>parent_lookup_course_id</strong><br><code>required</code></td>
                <td>string </td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_vle__institution_id</strong><br><code>required</code></td>
                <td>string </td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td>enabled</td>
                <td>boolean (Enabled)</td>
                <td>Whether this activity is enabled or not.</td>
            </tr>
            <tr>
                <td>conf</td>
                <td>string (Conf)<br>Nullable.</td>
                <td>Activity conf.</td>
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
                <td>vle_activity_type</td>
                <td>string (VLE activity type)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>vle_activity_id</td>
                <td>string (VLE activity ID)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>name</td>
                <td>string (Name)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>start</td>
                <td>string (Start)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>end</td>
                <td>string (End)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>description</td>
                <td>string (Description)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>enabled</td>
                <td>boolean (Enabled)</td>
                <td>Whether this activity is enabled or not.</td>
            </tr>
            <tr>
                <td>conf</td>
                <td>string (Conf)<br>Nullable.</td>
                <td>Activity conf.</td>
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
  "enabled": true,
  "conf": "string"
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
  "vle_activity_type": "string",
  "vle_activity_id": "string",
  "name": "string",
  "start": "string",
  "end": "string",
  "description": "string",
  "enabled": true,
  "conf": "string",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
````

</details>

<div style="text-align:right">

[[top section]](#institution_course_activity_management) [[top page]](#table-of-contents) 
</div>
<br>

<!--- institution_course_activity_delete --->
## 17.6 Delete Institution Course Activity <a name="institution_course_activity_delete"></a>

API endpoint that deletes Institution Course Activity.


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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_vle__institution_id}/course/{parent_lookup_course_id}/activity/{id}/</span></td>
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
                <td><strong>parent_lookup_course_id</strong><br><code>required</code></td>
                <td>string </td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_vle__institution_id</strong><br><code>required</code></td>
                <td>string </td>
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

[[top section]](#institution_course_activity_management) [[top page]](#table-of-contents) 
</div>
<br><br>




# 18. Institution Course Activity Instrument Management <a name="institution_course_activity_instrument_management"></a>
---
Set of API endpoint that allows Institution Course Activity Instrument Data to be viewed or edited.

  18.1 GET: [List Institution Course Activity Instrument](#institution_course_activity_instrument_list)<br>
  18.2 POST: [Create Institution Course Activity Instrument](#institution_course_activity_instrument_create)<br>
  18.3 GET: [Read Institution Course Activity Instrument](#institution_course_activity_instrument_read)<br>
  18.4 PUT: [Update Institution Course Activity Instrument](#institution_course_activity_instrument_update)<br>
  18.5 PATCH: [Partial Update Institution Course Activity Instrument](#institution_course_activity_instrument_partial_update)<br>
  18.6 DEL: [Delete Institution Course Activity Instrument](#institution_course_activity_instrument_delete)<br>
<div style="text-align:right">

[[top page]](#table-of-contents) 
</div>
<br>


<!--- institution_course_activity_instrument_list --->
## 18.1 List Institution Course Activity Instrument <a name="institution_course_activity_instrument_list"></a>

API endpoint that allows Institution Course Activity Instrument to be listed.

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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_activity__vle__institution_id}/course/{parent_lookup_activity__course_id}/activity/{parent_lookup_activity_id}/instrument/</span></td>
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
                <td><strong>parent_lookup_activity_id</strong><br><code>required</code></td>
                <td>string </td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_activity__course_id</strong><br><code>required</code></td>
                <td>string </td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_activity__vle__institution_id</strong><br><code>required</code></td>
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
            <td>Array of objects (InstitutionCourseActivityInstrument)</td>
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
      "options": {},
      "instrument": {
        "id": 0,
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
        "options_schema": "string",
        "created_at": "2019-08-24T14:15:22Z",
        "updated_at": "2019-08-24T14:15:22Z"
      },
      "instrument_id": 0,
      "active": true,
      "created_at": "2019-08-24T14:15:22Z",
      "updated_at": "2019-08-24T14:15:22Z",
      "alternative_to": 0
    }
  ]
}
 ````

</details>

<div style="text-align:right">

[[top section]](#institution_course_activity_instrument_management) [[top page]](#table-of-contents) 
</div>
<br>


<!--- institution_course_activity_instrument_create --->
## 18.2 Create Institution Course Activity Instrument <a name="institution_course_activity_instrument_create"></a>

API endpoint that creates Institution Course Activity Instrument.

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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_activity__vle__institution_id}/course/{parent_lookup_activity__course_id}/activity/{parent_lookup_activity_id}/instrument/</span></td>
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
    <table  style="table-layout: fixed; width: 100%">
        <tbody>
            <tr>
                <td><strong>Name</strong></td>
                <td><strong>Type</strong></td>
                <td><strong>Comments</strong></td>
            </tr>
            <tr>
                <td><strong><span style="word-wrap: break-word">parent_lookup_activity_id</span></strong><br><code>required</code></td>
                <td>string </td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong><span style="word-wrap: break-word">parent_lookup_activity__course_id</span></strong><br><code>required</code></td>
                <td>string </td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong><span style="word-wrap: break-word">parent_lookup_activity__vle__institution_id</span></strong><br><code>required</code></td>
                <td>string </td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td>options</td>
                <td>object (Options)<br>Nullable.</td>
                <td>-</td>
            </tr>
            <tr>
                <td>instrument</td>
                <td><span style="word-wrap: break-word">object (InstitutionCourseActivityInstrumentInfo)</span></td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>instrument_id</strong><br><code>required</code></td>
                <td>integer (Instrument ID) </td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>active</strong><br><code>required</code></td>
                <td>boolean (Active) </td>
                <td>Is Instrument active?</td>
            </tr>
            <tr>
                <td>alternative_to</td>
                <td>integer (Alternative to)<br>Nullable.</td>
                <td>Primary Instrument to be used.</td>
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
                <td>options</td>
                <td>object (Options)<br>Nullable.</td>
                <td>-</td>
            </tr>
            <tr>
                <td>instrument</td>
                <td><span style="word-wrap: break-word">object (InstitutionCourseActivityInstrumentInfo)</span></td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>instrument_id</strong><br><code>required</code></td>
                <td>integer (Instrument ID) </td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>active</strong><br><code>required</code></td>
                <td>boolean (Active) </td>
                <td>Is Instrument active?</td>
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
            <tr>
                <td>alternative_to</td>
                <td>integer (Alternative to)<br>Nullable.</td>
                <td>Primary Instrument to be used.</td>
            </tr>
        </tbody>
    </table>
  {{</tab>}}
{{</tabs>}}

#### Request sample
`````json
{
  "options": {},
  "instrument": {
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
    "options_schema": "string"
  },
  "instrument_id": 0,
  "active": true,
  "alternative_to": 0
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
  "options": {},
  "instrument": {
    "id": 0,
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
    "options_schema": "string",
    "created_at": "2019-08-24T14:15:22Z",
    "updated_at": "2019-08-24T14:15:22Z"
  },
  "instrument_id": 0,
  "active": true,
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z",
  "alternative_to": 0
}
````
</details>

<div style="text-align:right">

[[top section]](#institution_course_activity_instrument_management) [[top page]](#table-of-contents) 
</div>
<br>


<!--- institution_course_activity_instrument_read --->
## 18.3 Read Institution Course Activity Instrument <a name="institution_course_activity_instrument_read"></a>

API endpoint that allows access to Institution Course Activity Instrument data.

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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_activity__vle__institution_id}/course/{parent_lookup_activity__course_id}/activity/{parent_lookup_activity_id}/instrument/{id}/</span></td>
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
                <td>Request path parameter. A unique integer value identifying this activity instrument.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_activity_id</strong><br><code>required</code></td>
                <td>string </td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_activity__course_id</strong><br><code>required</code></td>
                <td>string </td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_activity__vle__institution_id</strong><br><code>required</code></td>
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
                <td>integer (ID)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>options</td>
                <td>object (Options)<br>Nullable.</td>
                <td>-</td>
            </tr>
            <tr>
                <td>instrument</td>
                <td>object (InstitutionCourseActivityInstrumentInfo)</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>instrument_id</strong><br><code>required</code></td>
                <td>integer (Instrument ID) </td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>active</strong><br><code>required</code></td>
                <td>boolean (Active) </td>
                <td>Is Instrument active?</td>
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
            <tr>
                <td>alternative_to</td>
                <td>integer (Alternative to)<br>Nullable.</td>
                <td>Primary Instrument to be used.</td>
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
  "options": {},
  "instrument": {
    "id": 0,
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
    "options_schema": "string",
    "created_at": "2019-08-24T14:15:22Z",
    "updated_at": "2019-08-24T14:15:22Z"
  },
  "instrument_id": 0,
  "active": true,
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z",
  "alternative_to": 0
}
````
</details>


<div style="text-align:right">

[[top section]](#institution_course_activity_instrument_management) [[top page]](#table-of-contents) 
</div>

<br>

<!--- institution_course_activity_instrument_update --->
## 18.4 Update Institution Course Activity Instrument <a name="institution_course_activity_instrument_update"></a>

API endpoint that updates Institution Course Activity Instrument data.

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
            <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_activity__vle__institution_id}/course/{parent_lookup_activity__course_id}/activity/{parent_lookup_activity_id}/instrument/{id}/</span></td>
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
        <table  style="table-layout: fixed; width: 100%">
            <tbody>
                <tr>
                    <td><strong>Name</strong></td>
                    <td><strong>Type</strong></td>
                    <td><strong>Comments</strong></td>
                </tr>
                <tr>
                    <td><strong><span style="word-wrap: break-word">parent_lookup_activity_id</span></strong><br><code>required</code></td>
                    <td>string </td>
                    <td>Request path parameter.</td>
                </tr>
                <tr>
                    <td><strong><span style="word-wrap: break-word">parent_lookup_activity__course_id</span></strong><br><code>required</code></td>
                    <td>string </td>
                    <td>Request path parameter.</td>
                </tr>
                <tr>
                    <td><strong><span style="word-wrap: break-word">parent_lookup_activity__vle__institution_id</span></strong><br><code>required</code></td>
                    <td>string </td>
                    <td>Request path parameter.</td>
                </tr>
                <tr>
                    <td>options</td>
                    <td>object (Options)<br>Nullable.</td>
                    <td>-</td>
                </tr>
                <tr>
                    <td>instrument</td>
                    <td><span style="word-wrap: break-word">object (InstitutionCourseActivityInstrumentInfo)</span></td>
                    <td>-</td>
                </tr>
                <tr>
                    <td><strong>instrument_id</strong><br><code>required</code></td>
                    <td>integer (Instrument ID) </td>
                    <td>-</td>
                </tr>
                <tr>
                    <td><strong>active</strong><br><code>required</code></td>
                    <td>boolean (Active) </td>
                    <td>Is Instrument active?</td>
                </tr>
                <tr>
                    <td>alternative_to</td>
                    <td>integer (Alternative to)<br>Nullable.</td>
                    <td>Primary Instrument to be used.</td>
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
                <td>options</td>
                <td>object (Options)<br>Nullable.</td>
                <td>-</td>
            </tr>
            <tr>
                <td>instrument</td>
                <td>object (InstitutionCourseActivityInstrumentInfo)</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>instrument_id</strong><br><code>required</code></td>
                <td>integer (Instrument ID) </td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>active</strong><br><code>required</code></td>
                <td>boolean (Active) </td>
                <td>Is Instrument active?</td>
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
            <tr>
                <td>alternative_to</td>
                <td>integer (Alternative to)<br>Nullable.</td>
                <td>Primary Instrument to be used.</td>
            </tr>
        </tbody>
    </table>
  {{</tab>}}
{{</tabs>}}


#### Request sample

````json
{
  "options": {},
  "instrument": {
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
    "options_schema": "string"
  },
  "instrument_id": 0,
  "active": true,
  "alternative_to": 0
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
  "options": {},
  "instrument": {
    "id": 0,
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
    "options_schema": "string",
    "created_at": "2019-08-24T14:15:22Z",
    "updated_at": "2019-08-24T14:15:22Z"
  },
  "instrument_id": 0,
  "active": true,
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z",
  "alternative_to": 0
}
````

</details>

<div style="text-align:right">

[[top section]](#institution_course_activity_instrument_management) [[top page]](#table-of-contents) 
</div>
<br>

<!--- institution_course_activity_instrument_partial_update --->
## 18.5 Partial Update Institution Course Activity Instrument <a name="institution_course_activity_instrument_partial_update"></a>

API endpoint that updates Institution Course Activity Instrument data.

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
            <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_activity__vle__institution_id}/course/{parent_lookup_activity__course_id}/activity/{parent_lookup_activity_id}/instrument/{id}/</span></td>
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
        <table  style="table-layout: fixed; width: 100%">
            <tbody>
                <tr>
                    <td><strong>Name</strong></td>
                    <td><strong>Type</strong></td>
                    <td><strong>Comments</strong></td>
                </tr>
                <tr>
                    <td><strong><span style="word-wrap: break-word">parent_lookup_activity_id</span></strong><br><code>required</code></td>
                    <td>string </td>
                    <td>Request path parameter.</td>
                </tr>
                <tr>
                    <td><strong><span style="word-wrap: break-word">parent_lookup_activity__course_id</span></strong><br><code>required</code></td>
                    <td>string </td>
                    <td>Request path parameter.</td>
                </tr>
                <tr>
                    <td><strong><span style="word-wrap: break-word">parent_lookup_activity__vle__institution_id</span></strong><br><code>required</code></td>
                    <td>string </td>
                    <td>Request path parameter.</td>
                </tr>
                <tr>
                    <td>options</td>
                    <td>object (Options)<br>Nullable.</td>
                    <td>-</td>
                </tr>
                <tr>
                    <td>instrument</td>
                    <td><span style="word-wrap: break-word">object (InstitutionCourseActivityInstrumentInfo)</span></td>
                    <td>-</td>
                </tr>
                <tr>
                    <td><strong>instrument_id</strong><br><code>required</code></td>
                    <td>integer (Instrument ID) </td>
                    <td>-</td>
                </tr>
                <tr>
                    <td><strong>active</strong><br><code>required</code></td>
                    <td>boolean (Active) </td>
                    <td>Is Instrument active?</td>
                </tr>
                <tr>
                    <td>alternative_to</td>
                    <td>integer (Alternative to)<br>Nullable.</td>
                    <td>Primary Instrument to be used.</td>
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
                <td>options</td>
                <td>object (Options)<br>Nullable.</td>
                <td>-</td>
            </tr>
            <tr>
                <td>instrument</td>
                <td>object (InstitutionCourseActivityInstrumentInfo)</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>instrument_id</strong><br><code>required</code></td>
                <td>integer (Instrument ID) </td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>active</strong><br><code>required</code></td>
                <td>boolean (Active) </td>
                <td>Is Instrument active?</td>
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
            <tr>
                <td>alternative_to</td>
                <td>integer (Alternative to)<br>Nullable.</td>
                <td>Primary Instrument to be used.</td>
            </tr>
        </tbody>
    </table>
  {{</tab>}}
{{</tabs>}}

#### Request sample

````json
{
  "options": {},
  "instrument": {
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
    "options_schema": "string"
  },
  "instrument_id": 0,
  "active": true,
  "alternative_to": 0
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
  "options": {},
  "instrument": {
    "id": 0,
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
    "options_schema": "string",
    "created_at": "2019-08-24T14:15:22Z",
    "updated_at": "2019-08-24T14:15:22Z"
  },
  "instrument_id": 0,
  "active": true,
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z",
  "alternative_to": 0
}
````

</details>

<div style="text-align:right">

[[top section]](#institution_course_activity_instrument_management) [[top page]](#table-of-contents) 
</div>
<br>

<!--- institution_course_activity_instrument_delete --->
## 18.6 Delete Institution Course Activity Instrument <a name="institution_course_activity_instrument_delete"></a>

API endpoint that deletes Institution Course Activity Instrument.


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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_activity__vle__institution_id}/course/{parent_lookup_activity__course_id}/activity/{parent_lookup_activity_id}/instrument/{id}/</span></td>
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
                <td><strong>parent_lookup_activity_id</strong><br><code>required</code></td>
                <td>string </td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_activity__course_id</strong><br><code>required</code></td>
                <td>string </td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_activity__vle__institution_id</strong><br><code>required</code></td>
                <td>string </td>
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

[[top section]](#institution_course_activity_instrument_management) [[top page]](#table-of-contents) 
</div>
<br><br>



# 19. Institution Course Activity Report Management <a name="institution_course_activity_report_management"></a>
---
Set of API endpoint that allows view Activity Reports from a Course.

  19.1 GET: [List Institution Course Activity Report](#institution_course_activity_report_list)<br>
  19.2 GET: [Read Institution Course Activity Report](#institution_course_activity_report_read)<br>
<div style="text-align:right">

[[top page]](#table-of-contents) 
</div>
<br>


<!--- institution_course_activity_report_list --->
## 19.1 List Institution Course Activity Report <a name="institution_course_activity_report_list"></a>

API endpoint that lists Activity Reports in a Course.

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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_activity__vle__institution_id}/course/{parent_lookup_activity__course_id}/activity/{parent_lookup_activity_id}/report/</span></td>
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
                <td><strong>parent_lookup_activity_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_activity__course_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_activity__vle__institution_id</strong><br><code>required</code></td>
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
            <td>Array of objects (InstitutionCourseActivityReport)</td>
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
      "learner": {
        "id": 0,
        "uid": "string",
        "first_name": "string",
        "last_name": "string",
        "email": "user@example.com",
        "learner_id": "2df776db-09df-4cb9-a2af-db56cada6cb7"
      },
      "detail": [
        {
          "instrument": "string",
          "enrolment": 0,
          "confidence": 0,
          "result": 0,
          "identity_level": 0,
          "content_level": 0,
          "integrity_level": 0,
          "instrument_id": 0
        }
      ],
      "identity_level": 0,
      "content_level": 0,
      "integrity_level": 0
    }
  ]
}
 ````

</details>

<div style="text-align:right">

[[top section]](#institution_course_activity_report_management) [[top page]](#table-of-contents) 
</div>
<br>




<!--- institution_course_activity_report_read --->
## 19.2 Read Institution Course Activity Report <a name="institution_course_activity_report_read"></a>

API endpoint that allows view Activity Reports data from a Course.

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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_activity__vle__institution_id}/course/{parent_lookup_activity__course_id}/activity/{parent_lookup_activity_id}/report/{id}/</span></td>
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
                <td>Request path parameter. A unique integer value identifying this Report Activity.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_activity_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_activity__course_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_activity__vle__institution_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr> 
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
                <td><strong>learner</strong><br><code>required</code></td>
                <td>object (InstitutionCourseActivityReportLearner)</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>detail</strong><br><code>required</code></td>
                <td>Array of objects (InstitutionCourseActivityReportDetail)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>identity_level</td>
                <td>integer (Identity Level)<br>Enum: 0, 1, 2, 3, 4</td>
                <td>Alert level for learner identity.</td>
            </tr>
            <tr>
                <td>content_level</td>
                <td>integer (Content Level)<br>Enum: 0, 1, 2, 3, 4</td>
                <td>Alert level for content authorship.</td>
            </tr>
            <tr>
                <td>integrity_level</td>
                <td>integer (Integrity Level)<br>Enum: 0, 1, 2, 3, 4</td>
                <td>Alert level for system integrity.</td>
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
  "learner": {
    "id": 0,
    "uid": "string",
    "first_name": "string",
    "last_name": "string",
    "email": "user@example.com",
    "learner_id": "2df776db-09df-4cb9-a2af-db56cada6cb7"
  },
  "detail": [
    {
      "instrument": "string",
      "enrolment": 0,
      "confidence": 0,
      "result": 0,
      "identity_level": 0,
      "content_level": 0,
      "integrity_level": 0,
      "instrument_id": 0
    }
  ],
  "identity_level": 0,
  "content_level": 0,
  "integrity_level": 0
}
````
</details>


<div style="text-align:right">

[[top section]](#institution_course_activity_report_management) [[top page]](#table-of-contents) 
</div>
<br><br>




# 20. Institution Course Activity Report Request Management <a name="institution_course_activity_report_request_management"></a>
---
Set of API endpoint that allows view Activity Reports Requests in a Course.

  20.1 GET: [List Institution Course Activity Report Request](#institution_course_activity_report_request_list)<br>
  20.2 GET: [Read Institution Course Activity Report Request](#institution_course_activity_report_request_read)<br>
<div style="text-align:right">

[[top page]](#table-of-contents) 
</div>
<br>


<!--- institution_course_activity_report_request_list --->
## 20.1 List Institution Course Activity Report Request <a name="institution_course_activity_report_request_list"></a>

API endpoint that lists Activity Reports Requests in a Course.

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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_activity__vle__institution_id}/course/{parent_lookup_activity__course_id}/activity/{parent_lookup_activity_id}/report/{parent_lookup_id}/request/</span></td>
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
                <td><strong>parent_lookup_activity_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_activity__course_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_activity__vle__institution_id</strong><br><code>required</code></td>
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
            <td>Array of objects (InstitutionCourseActivityReportRequest)</td>
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
      "result": [
        {
          "id": 0,
          "status": 0,
          "result": 0,
          "error_message": "string",
          "code": 0,
          "audit": "http://example.com",
          "created_at": "2019-08-24T14:15:22Z",
          "updated_at": "2019-08-24T14:15:22Z",
          "request": 0,
          "instrument": 0,
          "message_code": "string"
        }
      ],
      "status": 0,
      "data": "http://example.com",
      "error_message": "string",
      "created_at": "2019-08-24T14:15:22Z",
      "updated_at": "2019-08-24T14:15:22Z",
      "learner": "string",
      "activity": 0,
      "session": 0,
      "message_code": "string",
      "instruments": [
        0
      ]
    }
  ]
}
 ````

</details>

<div style="text-align:right">

[[top section]](#institution_course_activity_report_request_management) [[top page]](#table-of-contents) 
</div>
<br>




<!--- institution_course_activity_report_request_read --->
## 20.2 Read Institution Course Activity Report Request <a name="institution_course_activity_report_request_read"></a>

API endpoint that allows view Activity Reports Requests data from a Course.

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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_activity__vle__institution_id}/course/{parent_lookup_activity__course_id}/activity/{parent_lookup_activity_id}/report/{parent_lookup_id}/request/{id}/</span></td>
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
                <td>Request path parameter. A unique integer value identifying this Report Activity.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_activity_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_activity__course_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_activity__vle__institution_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr> 
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
                <td><strong>result</strong><br><code>required</code></td>
                <td>Array of objects (InstitutionCourseActivityReportRequestResult)</td>
                <td>-</td>
            </tr>
           <tr>
                <td>status</td>
                <td>integer (Status)<br>Enum: 0, 1, 2, 3, 4, 5, 6</td>
                <td>Status for this request.</td>
            </tr>
           <tr>
                <td>data</td>
                <td>string &lt;uri&gt; (Data)</td>
                <td>Data path on storage.</td>
            </tr>
           <tr>
                <td>error_message</td>
                <td>string (Error message)<br>non-empty<br>Nullable.</td>
                <td>Error message when status is error.</td>
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
            <tr>
                <td><strong>learner</strong><br><code>required</code></td>
                <td>string (Learner)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>activity</td>
                <td>integer (Activity)<br>Nullable.</td>
                <td>-</td>
            </tr>
            <tr>
                <td>session</td>
                <td>integer (Session)<br>Nullable.</td>
                <td>Assessment session for this request</td>
            </tr>
            <tr>
                <td>message_code</td>
                <td>string (Message code)<br>Nullable.</td>
                <td>Related message code.</td>
            </tr>
            <tr>
                <td><strong>instruments</strong><br><code>required</code></td>
                <td>Array of integers</td>
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
  "result": [
    {
      "id": 0,
      "status": 0,
      "result": 0,
      "error_message": "string",
      "code": 0,
      "audit": "http://example.com",
      "created_at": "2019-08-24T14:15:22Z",
      "updated_at": "2019-08-24T14:15:22Z",
      "request": 0,
      "instrument": 0,
      "message_code": "string"
    }
  ],
  "status": 0,
  "data": "http://example.com",
  "error_message": "string",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z",
  "learner": "string",
  "activity": 0,
  "session": 0,
  "message_code": "string",
  "instruments": [
    0
  ]
}
````
</details>


<div style="text-align:right">

[[top section]](#institution_course_activity_report_request_management) [[top page]](#table-of-contents) 
</div>
<br><br>




# 21. Institution Course Activity Report Audit Management <a name="institution_course_activity_report_audit_management"></a>
---
Set of API endpoint that allows view Activity Report Audit data.

  21.1 GET: [List Institution Course Activity Report Audit](#institution_course_activity_report_audit_list)<br>
  21.2 GET: [Read Institution Course Activity Report Audit](#institution_course_activity_report_audit_read)<br>
<div style="text-align:right">

[[top page]](#table-of-contents) 
</div>
<br>


<!--- institution_course_activity_report_audit_list --->
## 21.1 List Institution Course Activity Report Audit <a name="institution_course_activity_report_audit_list"></a>

API endpoint that lists Activity Report Audit data.

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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_report__activity__vle__institution_id}/course/{parent_lookup_report__activity__course_id}/activity/{parent_lookup_report__activity_id}/report/{parent_lookup_report_id}/audit/</span></td>
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
                <td><strong>parent_lookup_report_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_report__activity_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_report__activity__course_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_report__activity__vle__institution_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
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
            <td>Array of objects (InstitutionCourseActivityReportAudit)</td>
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
      "enrolment": -32768,
      "confidence": -32768,
      "result": -32768,
      "identity_level": 0,
      "content_level": 0,
      "integrity_level": 0,
      "audit_data": "http://example.com",
      "created_at": "2019-08-24T14:15:22Z",
      "updated_at": "2019-08-24T14:15:22Z",
      "report": 0,
      "instrument": 0
    }
  ]
}
 ````

</details>

<div style="text-align:right">

[[top section]](#institution_course_activity_report_audit_management) [[top page]](#table-of-contents) 
</div>
<br>




<!--- institution_course_activity_report_audit_read --->
## 21.2 Read Institution Course Activity Report Audit <a name="institution_course_activity_report_audit_read"></a>

API endpoint that allows view Activity Reports Audits data from a Course.

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
        <td><span style="word-wrap: break-word">/api/v2/institution/{parent_lookup_report__activity__vle__institution_id}/course/{parent_lookup_report__activity__course_id}/activity/{parent_lookup_report__activity_id}/report/{parent_lookup_report_id}/audit/{instrument_id}/</span></td>
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
                <td><strong>instrument_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter. </td>
            </tr>
            <tr>
                <td><strong>parent_lookup_report_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_report__activity_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_report__activity__course_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_report__activity__vle__institution_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
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
                <td><strong>enrolment</strong><br><code>required</code></td>
                <td>integer (Enrolment)<br>[ -32768 .. 32767 ]</td>
                <td>Enrolment percentage.</td>
            </tr>
            <tr>
                <td><strong>confidence</strong><br><code>required</code></td>
                <td>integer (Confidence)<br>[ -32768 .. 32767 ]</td>
                <td>Confidence percentage.</td>
            </tr>
            <tr>
                <td><strong>result</strong><br><code>required</code></td>
                <td>integer (Result)<br>[ -32768 .. 32767 ]</td>
                <td>Result percentage.</td>
            </tr>
           <tr>
                <td>identity_level</td>
                <td>integer (Identity level)<br>Enum: 0, 1, 2, 3, 4</td>
                <td>Alert level for learner identity.</td>
            </tr>
           <tr>
                <td>content_level</td>
                <td>integer (Content level)<br>Enum: 0, 1, 2, 3, 4</td>
                <td>Alert level for content authorship.</td>
            </tr>
           <tr>
                <td>integrity_level</td>
                <td>integer (Integrity level)<br>Enum: 0, 1, 2, 3, 4</td>
                <td>Alert level for system integrity.</td>
            </tr>
           <tr>
                <td>audit_data</td>
                <td>string &lt;uri&gt; (Audit data)<br>Nullable.</td>
                <td>Path to the audit data.</td>
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
            <tr>
                <td><strong>report</strong><br><code>required</code></td>
                <td>integer (Report)</td>
                <td>Related Activity Report.</td>
            </tr>
            <tr>
                <td><strong>instrument</strong><br><code>required</code></td>
                <td>integer (Instrument)</td>
                <td>Instrument related to this report detail.</td>
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
  "enrolment": -32768,
  "confidence": -32768,
  "result": -32768,
  "identity_level": 0,
  "content_level": 0,
  "integrity_level": 0,
  "audit_data": "http://example.com",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z",
  "report": 0,
  "instrument": 0
}
````
</details>


<div style="text-align:right">

[[top section]](#institution_course_activity_report_audit_management) [[top page]](#table-of-contents) 
</div>
<br><br>




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
