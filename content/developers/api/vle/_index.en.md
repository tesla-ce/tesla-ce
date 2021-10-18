---
title: "VLE"
weight: 5
draft: false
# search related keywords
keywords: ["API","vle"]
---

{{< notice info >}}
  **This page is under construction** <br>
  We're working on it!
{{</ notice >}}

Set of API endpoints that allows access to VLE related models.

<table><tr><td>

# Table of Content
1. [VLE Management](#vle_management)
2. [VLE Course Management](#vle_course_management)
3. [VLE Instrument Management](#vle_instrument_management)
4. [VLE Course Instructor Management](#vle_course_instructor_management)
5. [VLE Course Learner Management](#vle_course_learner_management)
6. [VLE Course Activity Management](#vle_course_activity_management)
7. [VLE Course Activity Attachment Management](#vle_course_activity_attachment_management)
8. [VLE Course Activity Instrument Management](#vle_course_activity_instrument_management)
9. [VLE Course Activity Learner Management](#vle_course_activity_learner_management)
10. [VLE Course Activity Report Management](#vle_course_activity_report_management)

</td></tr></table>

<br><br>

# 1. VLE Management <a name="vle_management"></a> 
---

  1.1 GET: [List VLE](#vle_list)<br>
  1.2 GET: [Read VLE](#vle_read)<br>
  1.3 POST: [VLE Assesment](#vle_assessment): create a new assessment session.<br>
  1.4 POST: [VLE Launcher](#vle_launcher): create a new launcher url for VLE user.
<br><br>

<!--- vle_list --->
## 1.1 List VLE <a name="vle_list"></a>

API endpoint for listing Providers.

### Request

Concept | Data
-- | --
HTTP Method | <code>**GET**</code>
Path | /api/v2/vle/
Authorization | JWT
Content Type | application/json

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
              <td>integer</td>
              <td>-</td>
          </tr>
          <tr>
              <td>next</td>
              <td>string &lt;uri&gt;<br>Nullable</td>
              <td>-</td>
          </tr>
          <tr>
              <td>previous</td>
              <td>string &lt;uri&gt;<br>Nullable</td>
              <td>-</td>
          </tr>
          <tr>
              <td>results<br><code>required</code></td>
              <td>Array of Objects (VLE)</td>
              <td>-</td>
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
      "type": "string",
      "name": "string",
      "url": "string",
      "client_id": "string"
    }
  ]
}
  ````
</details>

<div align="right">

[[top section]](#vle_management) [[top page]](#table-of-content) 
</div>
<br>


<!--- vle_read --->
## 1.2 Read VLE<a name="vle_read"></a>
Retrieves information about a VLE.

### Request
Concept | Data
-- | --
HTTP method | <code>**GET**</code>
Path | /api/v2/vle/{id}/
Authorization | JWT
Content Type | application/json

### Parameters:
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
                  <td>integer </td>
                  <td>Request path parameter. A unique integer value identifying this VLE.</td>
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
              <td><strong>type</strong><br><code>required</code></td>
              <td>string (Type)<br>non-empty.</td>
              <td>-</td>
          </tr>
          <tr>
              <td><strong>name</strong><br><code>required</code></td>
              <td>string (Name)<br>[1 .. 250] characters </td>
              <td>VLE unique name.</td>
          </tr>
          <tr>
              <td>url</td>
              <td>string (Url name)<br>Nullable </td>
              <td>VLE url.</td>
          </tr>
          <tr>
              <td>client_id</td>
              <td>string (Client_id)<br>[1 .. 250] characters<br>Nullable</td>
              <td>LTI 1.3 Client ID.</td>
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
  "type": "string",
  "name": "string",
  "url": "string",
  "client_id": "string"
}
```
</details>


<div align="right">

[[top section]](#vle_management) [[top page]](#table-of-content) 
</div>


<!--- vle_assessment --->
## 1.3 VLE Assessment <a name="vle_assessment"></a>
API endpoint that creates a new assessment session.

### Request
Concept | Data
-- | --
HTTP method | <code>**POST**</code>
Path | /api/v2/vle/{id}/assessment/
Authorization | JWT
Content Type | application/json

### Parameters:
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
                  <td>integer </td>
                  <td>Request path parameter. A unique integer value identifying this VLE.</td>
              </tr>
              <tr>
                  <td>data</td>
                  <td>object (VLENewAssessmentSessionData)</td>
                  <td>-</td>
              </tr>
              <tr>
                  <td>checked_at</td>
                  <td>string &lt;date-time&gt; (Checked at)<br>Nullable.</td>
                  <td>Last time this assessment session has been checked.</td>
              </tr>
              <tr>
                  <td>closed_at</td>
                  <td>string &lt;date-time&gt; (Closed at)<br>Nullable.</td>
                  <td>Date the assessment session has been closed.</td>
              </tr>
              <tr>
                  <td>auto_closed</td>
                  <td>boolean (Auto closed)<br>Nullable.</td>
                  <td>Whether this session has been automatically closed.</td>
              </tr>
              <tr>
                  <td><strong>activity</strong><br><code>required</code></td>
                  <td>integer (Activity) </td>
                  <td>Activity of this session.</td>
              </tr>
              <tr>
                  <td><strong>learner</strong><br><code>required</code></td>
                  <td>string (Learner) </td>
                  <td>Learner of this session.</td>
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
              <td>data</td>
              <td>object (VLENewAssessmentSessionData)</td>
              <td>-</td>
          </tr>
          <tr>
              <td>started_at</td>
              <td>string &lt;date-time&gt; (Started at)<br>Nullable.</td>
              <td>Date when this assessment session started.</td>
          </tr>
          <tr>
              <td>checked_at</td>
              <td>string &lt;date-time&gt; (Checked at)<br>Nullable.</td>
              <td>Last time this assessment session has been checked.</td>
          </tr>
          <tr>
              <td>closed_at</td>
              <td>string &lt;date-time&gt; (Closed at)<br>Nullable.</td>
              <td>Date the assessment session has been closed.</td>
          </tr>
          <tr>
              <td>auto_closed</td>
              <td>boolean (Auto closed)<br>Nullable.</td>
              <td>Whether this session has been automatically closed.</td>
          </tr>
          <tr>
              <td><strong>activity</strong><br><code>required</code></td>
              <td>integer (Activity) </td>
              <td>Activity of this session.</td>
          </tr>
          <tr>
              <td><strong>learner</strong><br><code>required</code></td>
              <td>string (Learner) </td>
              <td>Learner of this session.</td>
          </tr>
      </tbody>
    </table>
  {{</ tab >}}
{{</ tabs >}}

#### Request Sample: 
```json
{
  "data": {
    "session": 0
  },
  "checked_at": "2019-08-24T14:15:22Z",
  "closed_at": "2019-08-24T14:15:22Z",
  "auto_closed": true,
  "activity": 0,
  "learner": "string"
}
````
### Responses

#### Response sample: 201

<!--- details and summary tags, both, needed for expandable code --->
<details>
  <summary>201</summary>

```json
{
  "id": 0,
  "data": {
    "id": 0,
    "connector": "http://example.com",
    "data": "http://example.com",
    "session": 0
  },
  "started_at": "2019-08-24T14:15:22Z",
  "checked_at": "2019-08-24T14:15:22Z",
  "closed_at": "2019-08-24T14:15:22Z",
  "auto_closed": true,
  "activity": 0,
  "learner": "string"
}
```
</details>


<div align="right">

[[top section]](#vle_management) [[top page]](#table-of-content) 
</div>
<br>


<!--- vle_launcher --->
## 1.4 VLE Launcher <a name="vle_launcher"></a>
API endpoint that creates a new launcher url for VLE user.

### Request
Concept | Data
-- | --
HTTP method | <code>**POST**</code>
Path | /api/v2/vle/{id}/launcher/
Authorization | JWT
Content Type | application/json

### Parameters:
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
                  <td>integer </td>
                  <td>Request path parameter. A unique integer value identifying this VLE.</td>
              </tr>
              <tr>
                  <td><strong>token</strong><br><code>required</code></td>
                  <td>string (Token)<br>non-empty </td>
                  <td>-</td>
              </tr>
              <tr>
                  <td><strong>id</strong><br><code>required</code></td>
                  <td>integer (ID) </td>
                  <td>-</td>
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
              <td><strong>token</strong><br><code>required</code></td>
              <td>string (Token)<br>non-empty </td>
              <td>-</td>
          </tr>
          <tr>
              <td><strong>id</strong><br><code>required</code></td>
              <td>integer (ID) </td>
              <td>-</td>
          </tr>>
          <tr>
              <td>url</td>
              <td>string &lt;Url&gt;</td>
              <td>-</td>
          </tr>
      </tbody>
    </table>
  {{</ tab >}}
{{</ tabs >}}

#### Request Sample: 
```json
{
  "token": "string",
  "id": 0
}
````
### Responses

#### Response sample: 201

<!--- details and summary tags, both, needed for expandable code --->
<details>
  <summary>201</summary>

```json
{
  "token": "string",
  "id": 0,
  "url": "string"
}
```
</details>


<div align="right">

[[top section]](#vle_management) [[top page]](#table-of-content) 
</div>
<br>




<br><br><br>



# 2. VLE Course Management <a name="vle_course_management"></a>
---

Set of API endpoints that allow a course in a VLE to be viewed or edited.<br>

  2.1 GET: [List VLE Course](#vle_course_list)<br>
  2.2 POST: [Create VLE Course](#vle_course_create)<br>
  2.3 GET: [Read VLE Course](#vle_course_read)<br>
  2.4 PUT: [Update VLE Course](#vle_course_update)<br>
  2.5 PATCH: [Partial Update VLE Course](#vle_course_partial_update)<br>
  2.6 DELETE: [Delete VLE Course](#vle_course_delete)<br>

<br><br>


<!--- vle_course_list --->
## 2.1 List VLE Course<a name="vle_course_list"></a>

API endpoint for listing Courses in a VLE.

### Request

Concept | Data
-- | --
HTTP Method | <code>**GET**</code>
Path | /api/v2/vle/{parent_lookup_vle_id}/course/
Authorization | JWT
Content Type | application/json

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
                    <td><strong>parent_lookup_vle_id</strong><br><code>required</code></td>
                    <td>string </td>
                    <td>Request path parameter.</td>
            </tr>
            <tr>
                    <td>search</td>
                    <td>string </td>
                    <td>A search term</td>
            </tr>
            <tr>
                <td>code</td>
                <td>string</td>
                <td>-</td>
            </tr>
            <tr>
                <td>vle_course_id</td>
                <td>string</td>
                <td>-</td>
            </tr>
            <tr>
                <td>description</td>
                <td>string</td>
                <td>-</td>
            </tr>
            <tr>
                <td>vle</td>
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
                  <td></td>
          </tr>
          <tr>
              <td>next</td>
              <td>string &lt;uri&gt;<br>Nullable </td>
              <td>-</td>
          </tr>
          <tr>
              <td>previous</td>
              <td>string &lt;uri&gt;<br>Nullable </td>
              <td>-</td>
          </tr>
          <tr>
              <td><strong>results</strong><br><code>required</code></td>
              <td>Array of objects (VLECourse)</td>
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
      "code": "string",
      "vle_course_id": "string",
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

<div align="right">

[[top section]](#vle_course_management) [[top page]](#table-of-content) 
</div>
<br>

<!--- vle_course_create --->
## 2.2 Create VLE Course<a name="vle_course_create"></a>

API endpoint for creating a new Course in a VLE.

### Request

Concept | Data
-- | --
HTTP Method | <code>**POST**</code>
Path | /api/v2/vle/{parent_lookup_vle_id}/course/
Authorization | JWT
Content Type | application/json

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
                      <td><strong>parent_lookup_vle_id</strong><br><code>required</code></td>
                      <td>string</td>
                      <td>Request path parameter.</td>
              </tr>
              <tr>
                  <td>vle</td>
                  <td>object (VLE)</td>
                  <td>-</td>
              </tr>
              <tr>
                      <td><strong>code</strong><br><code>required</code></td>
                      <td>string (Code)<br>[1 .. 250] characters</td>
                      <td>Course code.</td>
              </tr>
              <tr>
                      <td><strong>vle_course_id</strong><br><code>required</code></td>
                      <td>string (VLE Course ID)<br>[1 .. 250] characters</td>
                      <td>Course ID on the VLE.</td>
              </tr>
              <tr>
                  <td>description</td>
                  <td>string (Description)<br>Nullable.</td>
                  <td>Course description.</td>
              </tr>
              <tr>
                  <td>start</td>
                  <td>string &lt;date-time&gt; (Start)<br>Nullable.</td>
                  <td>When course starts.</td>
              </tr>
              <tr>
                  <td>end</td>
                  <td>string &lt;date-time&gt;<br>Nullable.</td>
                  <td>When course ends.</td>
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
              <td>vle</td>
              <td>object (VLE)</td>
              <td>-</td>
            </tr>
            <tr>
              <td><strong>code</strong><br><code>required</code></td>
              <td>string (Code)<br>[1 .. 250] characters</td>
              <td>Course code.</td>
            </tr>
            <tr>
              <td><strong>vle_course_id</strong><br><code>required</code></td>
              <td>string (VLE Course ID)<br>[1 .. 250] characters</td>
              <td>Course ID on the VLE.</td>
            </tr>
            <tr>
              <td>description</td>
              <td>string (Description)<br>Nullable.</td>
              <td>Course description.</td>
            </tr>
            <tr>
              <td>start</td>
              <td>string &lt;date-time&gt; (Start)<br>Nullable.</td>
              <td>When course starts.</td>
            </tr>
            <tr>
              <td>end</td>
              <td>string &lt;date-time&gt;<br>Nullable.</td>
              <td>When course ends.</td>
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

#### Request Sample: 

```json
{
  "vle": {
    "type": "string",
    "name": "string",
    "url": "string",
    "client_id": "string"
  },
  "code": "string",
  "vle_course_id": "string",
  "description": "string",
  "start": "2019-08-24T14:15:22Z",
  "end": "2019-08-24T14:15:22Z"
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
  "vle": {
    "id": 0,
    "type": "string",
    "name": "string",
    "url": "string",
    "client_id": "string"
  },
  "code": "string",
  "vle_course_id": "string",
  "description": "string",
  "start": "2019-08-24T14:15:22Z",
  "end": "2019-08-24T14:15:22Z",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
  ````
</details>

<div align="right">

[[top section]](#vle_course_management) [[top page]](#table-of-content) 
</div>
<br>

<!--- vle_course_read --->
## 2.3 Read VLE Course<a name="vle_course_read"></a>
Retrieves information about a Course in a VLE.

### Request
Concept | Data
-- | --
HTTP method | <code>**GET**</code>
Path | /api/v2/vle/{parent_lookup_vle_id}/course/{id}/
Authorization | JWT
Content Type | application/json

### Parameters:
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
                  <td>string </td>
                  <td>Request path parameter.</td>
              </tr>
              <tr>
                  <td><strong>parent_lookup_vle_id</strong><br><code>required</code></td>
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
          <td>vle</td>
          <td>object (VLE)</td>
          <td>-</td>
        </tr>
        <tr>
          <td><strong>code</strong><br><code>required</code></td>
          <td>string (Code)<br>[1 .. 250] characters</td>
          <td>Course code.</td>
        </tr>
        <tr>
          <td><strong>vle_course_id</strong><br><code>required</code></td>
          <td>string (VLE Course ID)<br>[1 .. 250] characters</td>
          <td>Course ID on the VLE.</td>
        </tr>
        <tr>
          <td>description</td>
          <td>string (Description)<br>Nullable.</td>
          <td>Course description.</td>
        </tr>
        <tr>
          <td>start</td>
          <td>string &lt;date-time&gt; (Start)<br>Nullable.</td>
          <td>When course starts.</td>
        </tr>
        <tr>
          <td>end</td>
          <td>string &lt;date-time&gt;<br>Nullable.</td>
          <td>When course ends.</td>
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
  "vle": {
    "id": 0,
    "type": "string",
    "name": "string",
    "url": "string",
    "client_id": "string"
  },
  "code": "string",
  "vle_course_id": "string",
  "description": "string",
  "start": "2019-08-24T14:15:22Z",
  "end": "2019-08-24T14:15:22Z",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
```
</details>

<div align="right">

[[top section]](#vle_course_management) [[top page]](#table-of-content) 
</div>
<br>

<!--- vle_course_update --->
## 2.4 Update VLE Course<a name="vle_course_update"></a>
API endpoint that updates a Course in a VLE.

### Request
Concept | Data
-- | --
HTTP method | <code>**PUT**</code>
Path | /api/v2/vle/{parent_lookup_vle_id}/course/{id}/
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
              <td>Request path parameter.</td>
            </tr>
            <tr>
              <td><strong>parent_lookup_vle_id</strong><br><code>required</code></td>
              <td>string </td>
              <td>Request path parameter.</td>
            </tr>
            <tr>
              <td>vle</td>
              <td>object (VLE)</td>
              <td>-</td>
            </tr>
            <tr>
              <td><strong>code</strong><br><code>required</code></td>
              <td>string (Code)<br>[1 .. 250] characters</td>
              <td>Course code.</td>
            </tr>
            <tr>
              <td><strong>vle_course_id</strong><br><code>required</code></td>
              <td>string (VLE Course ID)<br>[1 .. 250] characters</td>
              <td>Course ID on the VLE.</td>
            </tr>
            <tr>
              <td>description</td>
              <td>string (Description)<br>Nullable.</td>
              <td>Course description.</td>
            </tr>
            <tr>
              <td>start</td>
              <td>string &lt;date-time&gt; (Start)<br>Nullable.</td>
              <td>When course starts.</td>
            </tr>
            <tr>
              <td>end</td>
              <td>string &lt;date-time&gt;<br>Nullable.</td>
              <td>When course ends.</td>
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
          <td>vle</td>
          <td>object (VLE)</td>
          <td>-</td>
        </tr>
        <tr>
          <td><strong>code</strong><br><code>required</code></td>
          <td>string (Code)<br>[1 .. 250] characters</td>
          <td>Course code.</td>
        </tr>
        <tr>
          <td><strong>vle_course_id</strong><br><code>required</code></td>
          <td>string (VLE Course ID)<br>[1 .. 250] characters</td>
          <td>Course ID on the VLE.</td>
        </tr>
        <tr>
          <td>description</td>
          <td>string (Description)<br>Nullable.</td>
          <td>Course description.</td>
        </tr>
        <tr>
          <td>start</td>
          <td>string &lt;date-time&gt; (Start)<br>Nullable.</td>
          <td>When course starts.</td>
        </tr>
        <tr>
          <td>end</td>
          <td>string &lt;date-time&gt;<br>Nullable.</td>
          <td>When course ends.</td>
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
  "vle": {
    "type": "string",
    "name": "string",
    "url": "string",
    "client_id": "string"
  },
  "code": "string",
  "vle_course_id": "string",
  "description": "string",
  "start": "2019-08-24T14:15:22Z",
  "end": "2019-08-24T14:15:22Z"
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
  "vle": {
    "id": 0,
    "type": "string",
    "name": "string",
    "url": "string",
    "client_id": "string"
  },
  "code": "string",
  "vle_course_id": "string",
  "description": "string",
  "start": "2019-08-24T14:15:22Z",
  "end": "2019-08-24T14:15:22Z",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
```
</details>

<div align="right">

[[top section]](#vle_course_management) [[top page]](#table-of-content) 
</div>
<br>

<!--- vle_course_partial_update --->
## 2.5 Partial Update VLE Course <a name="vle_course_partial_update"></a>
API endpoint that updates a Course in a VLE.

### Request
Concept | Data
-- | --
HTTP method | <code>**PATCH**</code>
Path | /api/v2/vle/{parent_lookup_vle_id}/course/{id}/
Authorization | JWT
Content Type | application/json

### Parameters:
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
              <td>string </td>
              <td>Request path parameter.</td>
            </tr>
            <tr>
              <td><strong>parent_lookup_vle_id</strong><br><code>required</code></td>
              <td>string </td>
              <td>Request path parameter.</td>
            </tr>
            <tr>
              <td>vle</td>
              <td>object (VLE)</td>
              <td>-</td>
            </tr>
            <tr>
              <td><strong>code</strong><br><code>required</code></td>
              <td>string (Code)<br>[1 .. 250] characters</td>
              <td>Course code.</td>
            </tr>
            <tr>
              <td><strong>vle_course_id</strong><br><code>required</code></td>
              <td>string (VLE Course ID)<br>[1 .. 250] characters</td>
              <td>Course ID on the VLE.</td>
            </tr>
            <tr>
              <td>description</td>
              <td>string (Description)<br>Nullable.</td>
              <td>Course description.</td>
            </tr>
            <tr>
              <td>start</td>
              <td>string &lt;date-time&gt; (Start)<br>Nullable.</td>
              <td>When course starts.</td>
            </tr>
            <tr>
              <td>end</td>
              <td>string &lt;date-time&gt;<br>Nullable.</td>
              <td>When course ends.</td>
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
          <td>vle</td>
          <td>object (VLE)</td>
          <td>-</td>
        </tr>
        <tr>
          <td><strong>code</strong><br><code>required</code></td>
          <td>string (Code)<br>[1 .. 250] characters</td>
          <td>Course code.</td>
        </tr>
        <tr>
          <td><strong>vle_course_id</strong><br><code>required</code></td>
          <td>string (VLE Course ID)<br>[1 .. 250] characters</td>
          <td>Course ID on the VLE.</td>
        </tr>
        <tr>
          <td>description</td>
          <td>string (Description)<br>Nullable.</td>
          <td>Course description.</td>
        </tr>
        <tr>
          <td>start</td>
          <td>string &lt;date-time&gt; (Start)<br>Nullable.</td>
          <td>When course starts.</td>
        </tr>
        <tr>
          <td>end</td>
          <td>string &lt;date-time&gt;<br>Nullable.</td>
          <td>When course ends.</td>
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
  "vle": {
    "type": "string",
    "name": "string",
    "url": "string",
    "client_id": "string"
  },
  "code": "string",
  "vle_course_id": "string",
  "description": "string",
  "start": "2019-08-24T14:15:22Z",
  "end": "2019-08-24T14:15:22Z"
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
  "vle": {
    "id": 0,
    "type": "string",
    "name": "string",
    "url": "string",
    "client_id": "string"
  },
  "code": "string",
  "vle_course_id": "string",
  "description": "string",
  "start": "2019-08-24T14:15:22Z",
  "end": "2019-08-24T14:15:22Z",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
```
</details>

<div align="right">

[[top section]](#vle_course_management) [[top page]](#table-of-content) 
</div>
<br>


<!--- vle_course_delete --->
## 2.6 Delete VLE Course<a name="vle_course_delete"></a>
API endpoint for deleting a Course in a VLE.

### Request
Concept | Data
-- | --
HTTP Method | <code>**DELETE**</code>
Path | /api/v2/vle/{parent_lookup_vle_id}/course/{id}/
Authorization | JWT
Content Type | application/json

### Parameters:
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
              <td>string </td>
              <td>Request path parameter.</td>
            </tr>
            <tr>
              <td><strong>parent_lookup_vle_id</strong><br><code>required</code></td>
              <td>string </td>
              <td>Request path parameter.</td>
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

<div align="right">

[[top section]](#vle_course_management) [[top page]](#table-of-content) 
</div>
<br>


<br><br><br><br>
----------
666

# 3. VLE Instrument Management <a name="vle_instrument_management"></a>
---

{{< notice note >}}
**Section TBD** <br>
{{</ notice >}}

<br><br><br>

# 4. VLE Course Instructor Management <a name="vle_course_instructor_management"></a>
---

{{< notice note >}}
**SEction TBD** <br>
{{</ notice >}}

<br><br><br>

# 5. VLE Course Learner Management <a name="vle_course_learner_management"></a>
---

{{< notice note >}}
**Section TBD** <br>
{{</ notice >}}

   
<br><br><br>

# 6. VLE Course Activity Management <a name="vle_course_activity_management"></a>
---

Set of API endpoints that allows Activity in a Course to be viewed or edited.<br>

  6.1 GET: [List VLE Course Activity](#vle_course_activity_list)<br>
  6.2 POST: [Create VLE Course Activity](#vle_course_activity_create)<br>
  6.3 GET: [Read VLE Course Activity](#vle_course_activity_read)<br>
  6.4 PUT: [Update VLE Course Activity](#vle_course_activity_update)<br>
  6.5 PATCH: [Partial Update VLE Course Activity](#vle_course_activity_partial_update)<br>
  6.6 DELETE: [Delete VLE Course Activity](#vle_course_activity_delete)

<br><br>


<!--- vle_course_activity_list --->
## 6.1 List VLE Course Activity<a name="vle_course_activity_list"></a>

API endpoint for listing Activities from a Course in a VLE.

### Request

Concept | Data
-- | --
HTTP Method | <code>**GET**</code>
Path | /api/v2/vle/{parent_lookup_vle_id}/course/{parent_lookup_course_id}/activity/
Authorization | JWT
Content Type | application/json

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
                <td><strong>parent_lookup_vle_id</strong><br><code>required</code></td>
                <td>string </td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td>search</td>
                <td>string </td>
                <td>A search term</td>
            </tr>
            <tr>
                <td>vle_id</td>
                <td>string</td>
                <td>-</td>
            </tr>
            <tr>
                <td>vle_activity_type</td>
                <td>string</td>
                <td>-</td>
            </tr>
            <tr>
                <td>vle_activity_id</td>
                <td>string</td>
                <td>-</td>
            </tr>
            <tr>
                <td>course_id</td>
                <td>string</td>
                <td>-</td>
            </tr>
            <tr>
                <td>name</td>
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
            <td></td>
          </tr>
          <tr>
            <td>next</td>
            <td>string &lt;uri&gt;<br>Nullable </td>
            <td>-</td>
          </tr>
          <tr>
            <td>previous</td>
            <td>string &lt;uri&gt;<br>Nullable </td>
            <td>-</td>
          </tr>
          <tr>
            <td><strong>results</strong><br><code>required</code></td>
            <td>Array of objects (VLECourseActivity)</td>
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
      "course": {
        "id": 0,
        "vle": {
          "id": 0,
          "type": "string",
          "name": "string",
          "url": "string",
          "client_id": "string"
        },
        "code": "string",
        "vle_course_id": "string",
        "description": "string",
        "start": "2019-08-24T14:15:22Z",
        "end": "2019-08-24T14:15:22Z",
        "created_at": "2019-08-24T14:15:22Z",
        "updated_at": "2019-08-24T14:15:22Z"
      },
      "vle_activity_type": "string",
      "vle_activity_id": "string",
      "description": "string",
      "name": "string",
      "enabled": true,
      "start": "2019-08-24T14:15:22Z",
      "end": "2019-08-24T14:15:22Z",
      "conf": "string",
      "created_at": "2019-08-24T14:15:22Z",
      "updated_at": "2019-08-24T14:15:22Z"
    }
  ]
}
  ````
</details>

<div align="right">

[[top section]](#vle_course_activity_management) [[top page]](#table-of-content) 
</div>
<br>


<!--- vle_course_activity_create --->
## 6.2 Create VLE Course Activity<a name="vle_course_activity_create"></a>

API endpoint for creating Activity for a Course in a VLE.

### Request

Concept | Data
-- | --
HTTP Method | <code>**POST**</code>
Path | /api/v2/vle/{parent_lookup_vle_id}/course/{parent_lookup_course_id}/activity/
Authorization | JWT
Content Type | application/json

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
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>              
            <tr>
                <td><strong>parent_lookup_vle_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td>course</td>
                <td>object (VLECourse)</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>vle_activity_type</strong><br><code>required</code></td>
                <td>string (VLE Activity Type)<br>[1 .. 250] characters</td>
                <td>Activity type on the VLE.</td>
            </tr>
            <tr>
                <td><strong>vle_activity_id</strong><br><code>required</code></td>
                <td>string (VLE Activity ID)<br>[1 .. 250] characters</td>
                <td>Activity ID on the VLE.</td>
            </tr>
            <tr>
              <td>description</td>
              <td>string (Description)<br>Nullable.</td>
              <td>Activity description.</td>
            </tr>
            <tr>
              <td>name</td>
              <td>string (Name)<br><= 255 characters.<br>Nullable.</td>
              <td>Activity name.</td>
            </tr>
            <tr>
              <td>enabled</td>
              <td>boolean (Enabled)</td>
              <td>Whether this activity is enabled or not.</td>
            </tr>
            <tr>
              <td>start</td>
              <td>string &lt;date-time&gt; (Start)<br>Nullable.</td>
              <td>When Activity starts.</td>
            </tr>
            <tr>
              <td>end</td>
              <td>string &lt;date-time&gt;<br>Nullable.</td>
              <td>When Activity ends.</td>
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
                <td>course</td>
                <td>object (VLECourse)</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>vle_activity_type</strong><br><code>required</code></td>
                <td>string (VLE Activity Type)<br>[1 .. 250] characters</td>
                <td>Activity type on the VLE.</td>
            </tr>
            <tr>
                <td><strong>vle_activity_id</strong><br><code>required</code></td>
                <td>string (VLE Activity ID)<br>[1 .. 250] characters</td>
                <td>Activity ID on the VLE.</td>
            </tr>
            <tr>
              <td>description</td>
              <td>string (Description)<br>Nullable.</td>
              <td>Activity description.</td>
            </tr>
            <tr>
              <td>name</td>
              <td>string (Name)<br><= 255 characters.<br>Nullable.</td>
              <td>Activity name.</td>
            </tr>
            <tr>
              <td>enabled</td>
              <td>boolean (Enabled)</td>
              <td>Whether this activity is enabled or not.</td>
            </tr>
            <tr>
              <td>start</td>
              <td>string &lt;date-time&gt; (Start)<br>Nullable.</td>
              <td>When Activity starts.</td>
            </tr>
            <tr>
              <td>end</td>
              <td>string &lt;date-time&gt;<br>Nullable.</td>
              <td>When Activity ends.</td>
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

#### Request Sample: 

```json
{
  "course": {
    "vle": {
      "type": "string",
      "name": "string",
      "url": "string",
      "client_id": "string"
    },
    "code": "string",
    "vle_course_id": "string",
    "description": "string",
    "start": "2019-08-24T14:15:22Z",
    "end": "2019-08-24T14:15:22Z"
  },
  "vle_activity_type": "string",
  "vle_activity_id": "string",
  "description": "string",
  "name": "string",
  "enabled": true,
  "start": "2019-08-24T14:15:22Z",
  "end": "2019-08-24T14:15:22Z",
  "conf": "string"
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
  "course": {
    "id": 0,
    "vle": {
      "id": 0,
      "type": "string",
      "name": "string",
      "url": "string",
      "client_id": "string"
    },
    "code": "string",
    "vle_course_id": "string",
    "description": "string",
    "start": "2019-08-24T14:15:22Z",
    "end": "2019-08-24T14:15:22Z",
    "created_at": "2019-08-24T14:15:22Z",
    "updated_at": "2019-08-24T14:15:22Z"
  },
  "vle_activity_type": "string",
  "vle_activity_id": "string",
  "description": "string",
  "name": "string",
  "enabled": true,
  "start": "2019-08-24T14:15:22Z",
  "end": "2019-08-24T14:15:22Z",
  "conf": "string",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
  ````
</details>

<div align="right">

[[top section]](#vle_course_activity_management) [[top page]](#table-of-content) 
</div>
<br>


<!--- vle_course_activity_read --->
## 6.3 Read VLE Course Activity<a name="vle_course_activity_read"></a>
API endpoint for reading Activity from a Course in a VLE.

### Request
Concept | Data
-- | --
HTTP method | <code>**GET**</code>
Path | /api/v2/vle/{parent_lookup_vle_id}/course/{parent_lookup_course_id}/activity/{id}/
Authorization | JWT
Content Type | application/json

### Parameters:
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
                  <td>string </td>
                  <td>Request path parameter.A unique integer value identifying this activity.</td>
              </tr>
              <tr>
                  <td><strong>parent_lookup_course_id</strong><br><code>required</code></td>
                  <td>string </td>
                  <td>Request path parameter.</td>
              </tr>
              <tr>
                  <td><strong>parent_lookup_vle_id</strong><br><code>required</code></td>
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
            <td>course</td>
            <td>object (VLECourse)</td>
            <td>-</td>
        </tr>
        <tr>
            <td><strong>vle_activity_type</strong><br><code>required</code></td>
            <td>string (VLE Activity Type)<br>[1 .. 250] characters</td>
            <td>Activity type on the VLE.</td>
        </tr>
        <tr>
            <td><strong>vle_activity_id</strong><br><code>required</code></td>
            <td>string (VLE Activity ID)<br>[1 .. 250] characters</td>
            <td>Activity ID on the VLE.</td>
        </tr>
        <tr>
          <td>description</td>
          <td>string (Description)<br>Nullable.</td>
          <td>Activity description.</td>
        </tr>
        <tr>
          <td>name</td>
          <td>string (Name)<br><= 255 characters.<br>Nullable.</td>
          <td>Activity name.</td>
        </tr>
        <tr>
          <td>enabled</td>
          <td>boolean (Enabled)</td>
          <td>Whether this activity is enabled or not.</td>
        </tr>
        <tr>
          <td>start</td>
          <td>string &lt;date-time&gt; (Start)<br>Nullable.</td>
          <td>When Activity starts.</td>
        </tr>
        <tr>
          <td>end</td>
          <td>string &lt;date-time&gt;<br>Nullable.</td>
          <td>When Activity ends.</td>
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
  "course": {
    "id": 0,
    "vle": {
      "id": 0,
      "type": "string",
      "name": "string",
      "url": "string",
      "client_id": "string"
    },
    "code": "string",
    "vle_course_id": "string",
    "description": "string",
    "start": "2019-08-24T14:15:22Z",
    "end": "2019-08-24T14:15:22Z",
    "created_at": "2019-08-24T14:15:22Z",
    "updated_at": "2019-08-24T14:15:22Z"
  },
  "vle_activity_type": "string",
  "vle_activity_id": "string",
  "description": "string",
  "name": "string",
  "enabled": true,
  "start": "2019-08-24T14:15:22Z",
  "end": "2019-08-24T14:15:22Z",
  "conf": "string",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
```
</details>

<div align="right">

[[top section]](#vle_course_activity_management) [[top page]](#table-of-content) 
</div>
<br>


<!--- vle_course_activity_update --->
## 6.4 Update VLE Course Activity<a name="vle_course_activity_update"></a>
API endpoint that updates an Activity from a Course in a VLE.

### Request
Concept | Data
-- | --
HTTP method | <code>**PUT**</code>
Path | /api/v2/vle/{parent_lookup_vle_id}/course/{parent_lookup_course_id}/activity/{id}/
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
                <td>string</td>
                <td>Request path parameter. A unique integer value identifying this activity.</td>
            </tr>              
            <tr>
                <td><strong>parent_lookup_course_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>              
            <tr>
                <td><strong>parent_lookup_vle_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td>course</td>
                <td>object (VLECourse)</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>vle_activity_type</strong><br><code>required</code></td>
                <td>string (VLE Activity Type)<br>[1 .. 250] characters</td>
                <td>Activity type on the VLE.</td>
            </tr>
            <tr>
                <td><strong>vle_activity_id</strong><br><code>required</code></td>
                <td>string (VLE Activity ID)<br>[1 .. 250] characters</td>
                <td>Activity ID on the VLE.</td>
            </tr>
            <tr>
              <td>description</td>
              <td>string (Description)<br>Nullable.</td>
              <td>Activity description.</td>
            </tr>
            <tr>
              <td>name</td>
              <td>string (Name)<br><= 255 characters.<br>Nullable.</td>
              <td>Activity name.</td>
            </tr>
            <tr>
              <td>enabled</td>
              <td>boolean (Enabled)</td>
              <td>Whether this activity is enabled or not.</td>
            </tr>
            <tr>
              <td>start</td>
              <td>string &lt;date-time&gt; (Start)<br>Nullable.</td>
              <td>When Activity starts.</td>
            </tr>
            <tr>
              <td>end</td>
              <td>string &lt;date-time&gt;<br>Nullable.</td>
              <td>When Activity ends.</td>
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
                <td>course</td>
                <td>object (VLECourse)</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>vle_activity_type</strong><br><code>required</code></td>
                <td>string (VLE Activity Type)<br>[1 .. 250] characters</td>
                <td>Activity type on the VLE.</td>
            </tr>
            <tr>
                <td><strong>vle_activity_id</strong><br><code>required</code></td>
                <td>string (VLE Activity ID)<br>[1 .. 250] characters</td>
                <td>Activity ID on the VLE.</td>
            </tr>
            <tr>
              <td>description</td>
              <td>string (Description)<br>Nullable.</td>
              <td>Activity description.</td>
            </tr>
            <tr>
              <td>name</td>
              <td>string (Name)<br><= 255 characters.<br>Nullable.</td>
              <td>Activity name.</td>
            </tr>
            <tr>
              <td>enabled</td>
              <td>boolean (Enabled)</td>
              <td>Whether this activity is enabled or not.</td>
            </tr>
            <tr>
              <td>start</td>
              <td>string &lt;date-time&gt; (Start)<br>Nullable.</td>
              <td>When Activity starts.</td>
            </tr>
            <tr>
              <td>end</td>
              <td>string &lt;date-time&gt;<br>Nullable.</td>
              <td>When Activity ends.</td>
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
  {{</ tab >}}
{{</ tabs >}}

#### Request sample
```json
{
  "course": {
    "vle": {
      "type": "string",
      "name": "string",
      "url": "string",
      "client_id": "string"
    },
    "code": "string",
    "vle_course_id": "string",
    "description": "string",
    "start": "2019-08-24T14:15:22Z",
    "end": "2019-08-24T14:15:22Z"
  },
  "vle_activity_type": "string",
  "vle_activity_id": "string",
  "description": "string",
  "name": "string",
  "enabled": true,
  "start": "2019-08-24T14:15:22Z",
  "end": "2019-08-24T14:15:22Z",
  "conf": "string"
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
  "course": {
    "id": 0,
    "vle": {
      "id": 0,
      "type": "string",
      "name": "string",
      "url": "string",
      "client_id": "string"
    },
    "code": "string",
    "vle_course_id": "string",
    "description": "string",
    "start": "2019-08-24T14:15:22Z",
    "end": "2019-08-24T14:15:22Z",
    "created_at": "2019-08-24T14:15:22Z",
    "updated_at": "2019-08-24T14:15:22Z"
  },
  "vle_activity_type": "string",
  "vle_activity_id": "string",
  "description": "string",
  "name": "string",
  "enabled": true,
  "start": "2019-08-24T14:15:22Z",
  "end": "2019-08-24T14:15:22Z",
  "conf": "string",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
```
</details>

<div align="right">

[[top section]](#vle_course_activity_management) [[top page]](#table-of-content) 
</div>
<br>


<!--- vle_course_activity_partial_update --->
## 6.5 Partial Update VLE Course Activity <a name="vle_course_activity_partial_update"></a>
API endpoint that updates an Activity from a Course in a VLE.

### Request
Concept | Data
-- | --
HTTP method | <code>**PATCH**</code>
Path | /api/v2/vle/{parent_lookup_vle_id}/course/{parent_lookup_course_id}/activity/{id}/
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
                <td>string</td>
                <td>Request path parameter. A unique integer value identifying this activity.</td>
            </tr>              
            <tr>
                <td><strong>parent_lookup_course_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>              
            <tr>
                <td><strong>parent_lookup_vle_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td>course</td>
                <td>object (VLECourse)</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>vle_activity_type</strong><br><code>required</code></td>
                <td>string (VLE Activity Type)<br>[1 .. 250] characters</td>
                <td>Activity type on the VLE.</td>
            </tr>
            <tr>
                <td><strong>vle_activity_id</strong><br><code>required</code></td>
                <td>string (VLE Activity ID)<br>[1 .. 250] characters</td>
                <td>Activity ID on the VLE.</td>
            </tr>
            <tr>
              <td>description</td>
              <td>string (Description)<br>Nullable.</td>
              <td>Activity description.</td>
            </tr>
            <tr>
              <td>name</td>
              <td>string (Name)<br><= 255 characters.<br>Nullable.</td>
              <td>Activity name.</td>
            </tr>
            <tr>
              <td>enabled</td>
              <td>boolean (Enabled)</td>
              <td>Whether this activity is enabled or not.</td>
            </tr>
            <tr>
              <td>start</td>
              <td>string &lt;date-time&gt; (Start)<br>Nullable.</td>
              <td>When Activity starts.</td>
            </tr>
            <tr>
              <td>end</td>
              <td>string &lt;date-time&gt;<br>Nullable.</td>
              <td>When Activity ends.</td>
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
                <td>course</td>
                <td>object (VLECourse)</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>vle_activity_type</strong><br><code>required</code></td>
                <td>string (VLE Activity Type)<br>[1 .. 250] characters</td>
                <td>Activity type on the VLE.</td>
            </tr>
            <tr>
                <td><strong>vle_activity_id</strong><br><code>required</code></td>
                <td>string (VLE Activity ID)<br>[1 .. 250] characters</td>
                <td>Activity ID on the VLE.</td>
            </tr>
            <tr>
              <td>description</td>
              <td>string (Description)<br>Nullable.</td>
              <td>Activity description.</td>
            </tr>
            <tr>
              <td>name</td>
              <td>string (Name)<br><= 255 characters.<br>Nullable.</td>
              <td>Activity name.</td>
            </tr>
            <tr>
              <td>enabled</td>
              <td>boolean (Enabled)</td>
              <td>Whether this activity is enabled or not.</td>
            </tr>
            <tr>
              <td>start</td>
              <td>string &lt;date-time&gt; (Start)<br>Nullable.</td>
              <td>When Activity starts.</td>
            </tr>
            <tr>
              <td>end</td>
              <td>string &lt;date-time&gt;<br>Nullable.</td>
              <td>When Activity ends.</td>
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
  {{</ tab >}}
{{</ tabs >}}

#### Request sample
```json
{
  "course": {
    "vle": {
      "type": "string",
      "name": "string",
      "url": "string",
      "client_id": "string"
    },
    "code": "string",
    "vle_course_id": "string",
    "description": "string",
    "start": "2019-08-24T14:15:22Z",
    "end": "2019-08-24T14:15:22Z"
  },
  "vle_activity_type": "string",
  "vle_activity_id": "string",
  "description": "string",
  "name": "string",
  "enabled": true,
  "start": "2019-08-24T14:15:22Z",
  "end": "2019-08-24T14:15:22Z",
  "conf": "string"
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
  "course": {
    "id": 0,
    "vle": {
      "id": 0,
      "type": "string",
      "name": "string",
      "url": "string",
      "client_id": "string"
    },
    "code": "string",
    "vle_course_id": "string",
    "description": "string",
    "start": "2019-08-24T14:15:22Z",
    "end": "2019-08-24T14:15:22Z",
    "created_at": "2019-08-24T14:15:22Z",
    "updated_at": "2019-08-24T14:15:22Z"
  },
  "vle_activity_type": "string",
  "vle_activity_id": "string",
  "description": "string",
  "name": "string",
  "enabled": true,
  "start": "2019-08-24T14:15:22Z",
  "end": "2019-08-24T14:15:22Z",
  "conf": "string",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
```
</details>

<div align="right">

[[top section]](#vle_course_activity_management) [[top page]](#table-of-content) 
</div>
<br>



<!--- vle_course_activity_delete --->
## 6.6 Delete VLE Course Activity<a name="vle_course_activity_delete"></a>
API endpoint for deleting an Activity from a Course in a VLE.

### Request
Concept | Data
-- | --
HTTP Method | <code>**DELETE**</code>
Path | /api/v2/vle/{parent_lookup_vle_id}/course/{parent_lookup_course_id}/activity/{id}/
Authorization | JWT
Content Type | application/json

### Parameters:
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
              <td>string </td>
              <td>Request path parameter. A unique integer value identifying this activity.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_course_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>              
            <tr>
                <td><strong>parent_lookup_vle_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
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

<div align="right">

[[top section]](#vle_course_activity_management) [[top page]](#table-of-content) 
</div>
<br>

<br><br><br>

# 7. VLE Course Activity Attachment Management <a name="vle_course_activity_attachment_management"></a>
---

Set of API endpoints that Return the list of instruments (if any) waiting to process the attachment of the activity.<br>

  7.1 GET: [List VLE Course Activity Attachment](#vle_course_activity_attachment_list)<br>
  7.2 POST: [Create VLE Course Activity Attachment](#vle_course_activity_attachment_create)<br>

<br><br>


<!--- vle_course_activity_attachment_list --->
## 7.1 List VLE Course Activity Attachment<a name="vle_course_activity_attachment_list"></a>

API endpoint for listing Activities from a Course in a VLE.

### Request

Concept | Data
-- | --
HTTP Method | <code>**GET**</code>
Path | /api/v2/vle/{parent_lookup_vle_id}/course/{parent_lookup_course_id}/activity/{id}/attachment/{learner_id}/
Authorization | JWT
Content Type | application/json

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
                <td>integer </td>
                <td>Request path parameter. A unique integer value identifying this activity.</td>
            </tr>
            <tr>
                <td><strong>learner_id</strong><br><code>required</code></td>
                <td>string </td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_course_id</strong><br><code>required</code></td>
                <td>string </td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_vle_id</strong><br><code>required</code></td>
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
            <td>learner_id</td>
            <td>string &lt;uuid&gt; (Learner ID)<br>Nullable </td>
            <td>-</td>
          </tr>
          <tr>
            <td>course_id</td>
            <td>integer (Course ID)<br>Nullable </td>
            <td>-</td>
          </tr>
          <tr>
            <td>activity_id</td>
            <td>integer (Activity ID)<br>Nullable </td>
            <td>-</td>
          </tr>
          <tr>
            <td>session_id</td>
            <td>integer (Session ID)<br>Nullable </td>
            <td>-</td>
          </tr>
          <tr>
            <td><strong>data</strong><br><code>required</code></td>
            <td>string (Data)<br>non-empty. </td>
            <td>-</td>
          </tr>
          <tr>
            <td><strong>instruments</strong><br><code>required</code></td>
            <td>Array of integers</td>
            <td>-</td>
          </tr>
          <tr>
            <td><strong>metadata</strong><br><code>required</code></td>
            <td>object (VerificationMetadata)</td>
            <td>-</td>
          </tr>
          <tr>
            <td>close_session</td>
            <td>boolean (Close session)<br>Nullable </td>
            <td>Default: true</td>
          </tr>
          <tr>
            <td>close_at</td>
            <td>string &lt;date-time&gt; (Close at)</td>
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
  "learner_id": "2df776db-09df-4cb9-a2af-db56cada6cb7",
  "course_id": 0,
  "activity_id": 0,
  "session_id": 0,
  "data": "string",
  "instruments": [
    0
  ],
  "metadata": {
    "filename": "string",
    "mimetype": "string",
    "context": {}
  },
  "close_session": true,
  "close_at": "2019-08-24T14:15:22Z"
}
  ````
</details>

<div align="right">

[[top section]](#vle_course_activity_attachment_management) [[top page]](#table-of-content) 
</div>
<br>


<!--- vle_course_activity_attachment_create --->
## 7.2 Create VLE Course Activity Attachment<a name="vle_course_activity_attachment_create"></a>

API endpoint for creating Activity for a Course in a VLE.

### Request

Concept | Data
-- | --
HTTP Method | <code>**POST**</code>
Path | /api/v2/vle/{parent_lookup_vle_id}/course/{parent_lookup_course_id}/activity/{id}/attachment/{learner_id}/
Authorization | JWT
Content Type | application/json

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
                <td>integer </td>
                <td>Request path parameter. A unique integer value identifying this activity.</td>
            </tr>
            <tr>
                <td><strong>learner_id</strong><br><code>required</code></td>
                <td>string </td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_course_id</strong><br><code>required</code></td>
                <td>string </td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_vle_id</strong><br><code>required</code></td>
                <td>string </td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td>learner_id</td>
                <td>string &lt;uuid&gt; (Learner ID)<br>Nullable </td>
                <td>-</td>
            </tr>
            <tr>
                <td>course_id</td>
                <td>integer (Course ID)<br>Nullable </td>
                <td>-</td>
            </tr>
            <tr>
                <td>activity_id</td>
                <td>integer (Activity ID)<br>Nullable </td>
                <td>-</td>
            </tr>
            <tr>
                <td>session_id</td>
                <td>integer (Session ID)<br>Nullable </td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>data</strong><br><code>required</code></td>
                <td>string (Data)<br>non-empty. </td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>instruments</strong><br><code>required</code></td>
                <td>Array of integers</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>metadata</strong><br><code>required</code></td>
                <td>object (VerificationMetadata)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>close_session</td>
                <td>boolean (Close session)<br>Nullable </td>
                <td>Default: true</td>
            </tr>
            <tr>
                <td>close_at</td>
                <td>string &lt;date-time&gt; (Close at)</td>
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
                <td>learner_id</td>
                <td>string &lt;uuid&gt; (Learner ID)<br>Nullable </td>
                <td>-</td>
            </tr>
            <tr>
                <td>course_id</td>
                <td>integer (Course ID)<br>Nullable </td>
                <td>-</td>
            </tr>
            <tr>
                <td>activity_id</td>
                <td>integer (Activity ID)<br>Nullable </td>
                <td>-</td>
            </tr>
            <tr>
                <td>session_id</td>
                <td>integer (Session ID)<br>Nullable </td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>data</strong><br><code>required</code></td>
                <td>string (Data)<br>non-empty. </td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>instruments</strong><br><code>required</code></td>
                <td>Array of integers</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>metadata</strong><br><code>required</code></td>
                <td>object (VerificationMetadata)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>close_session</td>
                <td>boolean (Close session)<br>Nullable </td>
                <td>Default: true</td>
            </tr>
            <tr>
                <td>close_at</td>
                <td>string &lt;date-time&gt; (Close at)</td>
                <td>-</td>
            </tr>
         </tbody>
        </table>
   {{</tab>}}
{{</tabs>}}

#### Request Sample: 

```json
{
  "learner_id": "2df776db-09df-4cb9-a2af-db56cada6cb7",
  "course_id": 0,
  "activity_id": 0,
  "session_id": 0,
  "data": "string",
  "instruments": [
    0
  ],
  "metadata": {
    "filename": "string",
    "mimetype": "string",
    "context": {}
  },
  "close_session": true,
  "close_at": "2019-08-24T14:15:22Z"
}
````


### Responses

#### Response sample
<!--- details and summary tags, both, needed for expandable code --->
<details>
  <summary>201</summary>

  ````json
{
  "learner_id": "2df776db-09df-4cb9-a2af-db56cada6cb7",
  "course_id": 0,
  "activity_id": 0,
  "session_id": 0,
  "data": "string",
  "instruments": [
    0
  ],
  "metadata": {
    "filename": "string",
    "mimetype": "string",
    "context": {}
  },
  "close_session": true,
  "close_at": "2019-08-24T14:15:22Z"
}
  ````
</details>

<div align="right">

[[top section]](#vle_course_activity_attachment_management) [[top page]](#table-of-content) 
</div>
<br>

<br><br><br>




# 8. VLE Course Activity Instrument Management <a name="vle_course_activity_instrument_management"></a>
---

Set of API endpoints that allows Activity instruments in a Course to be viewed or edited.<br>

  8.1 GET: [List VLE Course Activity Instrument](#vle_course_activity_instrument_list)<br>
  8.2 POST: [Create VLE Course Activity Instrument](#vle_course_activity_instrument_create)<br>
  8.3 GET: [Read VLE Course Activity Instrument](#vle_course_activity_instrument_read)<br>
  8.4 PUT: [Update VLE Course Activity Instrument](#vle_course_activity_instrument_update)<br>
  8.5 PATCH: [Partial Update VLE Course Activity Instrument](#vle_course_activity_instrument_partial_update)<br>
  8.6 DELETE: [Delete VLE Course Activity Instrument](#vle_course_activity_instrument_delete)

<br><br>


<!--- vle_course_activity_instrument_list --->
## 8.1 List VLE Course Activity Instrument<a name="vle_course_activity_instrument_list"></a>

API endpoint for listing Activity's instruments from a Course in a VLE.

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
        <td><span style="word-wrap: break-word">/api/v2/vle/{parent_lookup_vle_id}/course/{parent_lookup_course_id}/activity/{parent_lookup_activity_id}/instrument/</span></td>
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
                <td><strong>parent_lookup_course_id</strong><br><code>required</code></td>
                <td>string </td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_vle_id</strong><br><code>required</code></td>
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
            <td></td>
          </tr>
          <tr>
            <td>next</td>
            <td>string &lt;uri&gt;<br>Nullable </td>
            <td>-</td>
          </tr>
          <tr>
            <td>previous</td>
            <td>string &lt;uri&gt;<br>Nullable </td>
            <td>-</td>
          </tr>
          <tr>
            <td><strong>results</strong><br><code>required</code></td>
            <td>Array of objects (VLECourseActivityInstrument)</td>
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
      "activity": {
        "id": 0,
        "course": {
          "id": 0,
          "vle": {
            "id": 0,
            "type": "string",
            "name": "string",
            "url": "string",
            "client_id": "string"
          },
          "code": "string",
          "vle_course_id": "string",
          "description": "string",
          "start": "2019-08-24T14:15:22Z",
          "end": "2019-08-24T14:15:22Z",
          "created_at": "2019-08-24T14:15:22Z",
          "updated_at": "2019-08-24T14:15:22Z"
        },
        "vle_activity_type": "string",
        "vle_activity_id": "string",
        "description": "string",
        "name": "string",
        "enabled": true,
        "start": "2019-08-24T14:15:22Z",
        "end": "2019-08-24T14:15:22Z",
        "conf": "string",
        "created_at": "2019-08-24T14:15:22Z",
        "updated_at": "2019-08-24T14:15:22Z"
      },
      "options": {},
      "active": true,
      "created_at": "2019-08-24T14:15:22Z",
      "updated_at": "2019-08-24T14:15:22Z",
      "instrument": 0,
      "alternative_to": 0
    }
  ]
}
  ````
</details>

<div align="right">

[[top section]](#vle_course_activity_instrument_management) [[top page]](#table-of-content) 
</div>
<br>


<!--- vle_course_activity_instrument_create --->
## 8.2 Create VLE Course Activity Instrument<a name="vle_course_activity_instrument_create"></a>

API endpoint for adding instrument to Activity for a Course in a VLE.

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
        <td><span style="word-wrap: break-word">/api/v2/vle/{parent_lookup_vle_id}/course/{parent_lookup_course_id}/activity/{parent_lookup_activity_id}/instrument/</span></td>
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
                <td><strong>parent_lookup_course_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>              
            <tr>
                <td><strong>parent_lookup_vle_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td>activity</td>
                <td>object (VLECourseActivity)</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>options</strong><br><code>required</code></td>
                <td>object (Options)<br>Nullable.</td>
                <td>Activity type on the VLE.</td>
            </tr>
            <tr>
                <td><strong>active</strong><br><code>required</code></td>
                <td>boolean (Active)</td>
                <td>Is instrument active?</td>
            </tr>
            <tr>
                <td><strong>instrument</strong><br><code>required</code></td>
                <td>integer (Instrument)</td>
                <td>Activity.</td>
            </tr>
            <tr>
              <td>alternative_to</td>
              <td>integer (Alternative to)<br>Nullable.</td>
              <td>Primary instrument to be used.</td>
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
                <td>activity</td>
                <td>object (VLECourseActivity)</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>options</strong><br><code>required</code></td>
                <td>object (Options)<br>Nullable.</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>active</strong><br><code>required</code></td>
                <td>boolean (Active)</td>
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
            <tr>
                <td><strong>instrument</strong><br><code>required</code></td>
                <td>integer (Instrument)</td>
                <td>Activity.</td>
            </tr>
            <tr>
              <td>alternative_to</td>
              <td>integer (Alternative to)<br>Nullable.</td>
              <td>Primary instrument to be used.</td>
            </tr>
         </tbody>
        </table>
   {{</tab>}}
{{</tabs>}}

#### Request Sample: 

```json
{
  "activity": {
    "course": {
      "vle": {
        "type": "string",
        "name": "string",
        "url": "string",
        "client_id": "string"
      },
      "code": "string",
      "vle_course_id": "string",
      "description": "string",
      "start": "2019-08-24T14:15:22Z",
      "end": "2019-08-24T14:15:22Z"
    },
    "vle_activity_type": "string",
    "vle_activity_id": "string",
    "description": "string",
    "name": "string",
    "enabled": true,
    "start": "2019-08-24T14:15:22Z",
    "end": "2019-08-24T14:15:22Z",
    "conf": "string"
  },
  "options": {},
  "active": true,
  "instrument": 0,
  "alternative_to": 0
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
  "activity": {
    "id": 0,
    "course": {
      "id": 0,
      "vle": {
        "id": 0,
        "type": "string",
        "name": "string",
        "url": "string",
        "client_id": "string"
      },
      "code": "string",
      "vle_course_id": "string",
      "description": "string",
      "start": "2019-08-24T14:15:22Z",
      "end": "2019-08-24T14:15:22Z",
      "created_at": "2019-08-24T14:15:22Z",
      "updated_at": "2019-08-24T14:15:22Z"
    },
    "vle_activity_type": "string",
    "vle_activity_id": "string",
    "description": "string",
    "name": "string",
    "enabled": true,
    "start": "2019-08-24T14:15:22Z",
    "end": "2019-08-24T14:15:22Z",
    "conf": "string",
    "created_at": "2019-08-24T14:15:22Z",
    "updated_at": "2019-08-24T14:15:22Z"
  },
  "options": {},
  "active": true,
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z",
  "instrument": 0,
  "alternative_to": 0
}
  ````
</details>

<div align="right">

[[top section]](#vle_course_activity_instrument_management) [[top page]](#table-of-content) 
</div>
<br>


<!--- vle_course_activity_instrument_read --->
## 8.3 Read VLE Course Activity Instrument<a name="vle_course_activity_instrument_read"></a>
API endpoint for reading Activity's instrument from a Course in a VLE.

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
        <td><span style="word-wrap: break-word">/api/v2/vle/{parent_lookup_vle_id}/course/{parent_lookup_course_id}/activity/{parent_lookup_activity_id}/instrument/{id}/</span></td>
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


### Parameters:
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
              <td>string </td>
              <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_activity_id</strong><br><code>required</code></td>
                <td>string </td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_course_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>              
            <tr>
                <td><strong>parent_lookup_vle_id</strong><br><code>required</code></td>
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
            <td>activity</td>
            <td>object (VLECourseActivity)</td>
            <td>-</td>
        </tr>
        <tr>
            <td><strong>options</strong><br><code>required</code></td>
            <td>object (Options)<br>Nullable.</td>
            <td>-</td>
        </tr>
        <tr>
            <td><strong>active</strong><br><code>required</code></td>
            <td>boolean (Active)</td>
            <td>Is instrument active?</td>
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
            <td><strong>instrument</strong><br><code>required</code></td>
            <td>integer (Instrument)</td>
            <td>Activity.</td>
        </tr>
        <tr>
          <td>alternative_to</td>
          <td>integer (Alternative to)<br>Nullable.</td>
          <td>Primary instrument to be used.</td>
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
  "activity": {
    "id": 0,
    "course": {
      "id": 0,
      "vle": {
        "id": 0,
        "type": "string",
        "name": "string",
        "url": "string",
        "client_id": "string"
      },
      "code": "string",
      "vle_course_id": "string",
      "description": "string",
      "start": "2019-08-24T14:15:22Z",
      "end": "2019-08-24T14:15:22Z",
      "created_at": "2019-08-24T14:15:22Z",
      "updated_at": "2019-08-24T14:15:22Z"
    },
    "vle_activity_type": "string",
    "vle_activity_id": "string",
    "description": "string",
    "name": "string",
    "enabled": true,
    "start": "2019-08-24T14:15:22Z",
    "end": "2019-08-24T14:15:22Z",
    "conf": "string",
    "created_at": "2019-08-24T14:15:22Z",
    "updated_at": "2019-08-24T14:15:22Z"
  },
  "options": {},
  "active": true,
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z",
  "instrument": 0,
  "alternative_to": 0
}
```
</details>

<div align="right">

[[top section]](#vle_course_activity_instrument_management) [[top page]](#table-of-content) 
</div>
<br>


<!--- vle_course_activity_instrument_update --->
## 8.4 Update VLE Course Activity Instrument<a name="vle_course_activity_instrument_update"></a>
API endpoint that updates an Activity's Instrument from a Course in a VLE.

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
        <td><span style="word-wrap: break-word">/api/v2/vle/{parent_lookup_vle_id}/course/{parent_lookup_course_id}/activity/{parent_lookup_activity_id}/instrument/{id}/</span></td>
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
              <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_activity_id</strong><br><code>required</code></td>
                <td>string </td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_course_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>              
            <tr>
                <td><strong>parent_lookup_vle_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td>activity</td>
                <td>object (VLECourseActivity)</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>options</strong><br><code>required</code></td>
                <td>object (Options)<br>Nullable.</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>active</strong><br><code>required</code></td>
                <td>boolean (Active)</td>
                <td>Is instrument active?</td>
            </tr>
            <tr>
                <td><strong>instrument</strong><br><code>required</code></td>
                <td>integer (Instrument)</td>
                <td>Activity.</td>
            </tr>
            <tr>
              <td>alternative_to</td>
              <td>integer (Alternative to)<br>Nullable.</td>
              <td>Primary instrument to be used.</td>
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
            <td>activity</td>
            <td>object (VLECourseActivity)</td>
            <td>-</td>
        </tr>
        <tr>
            <td><strong>options</strong><br><code>required</code></td>
            <td>object (Options)<br>Nullable.</td>
            <td>-</td>
        </tr>
        <tr>
            <td><strong>active</strong><br><code>required</code></td>
            <td>boolean (Active)</td>
            <td>Is instrument active?</td>
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
            <td><strong>instrument</strong><br><code>required</code></td>
            <td>integer (Instrument)</td>
            <td>Activity.</td>
        </tr>
        <tr>
          <td>alternative_to</td>
          <td>integer (Alternative to)<br>Nullable.</td>
          <td>Primary instrument to be used.</td>
        </tr>
      </tbody>
    </table>
  {{</ tab >}}
{{</ tabs >}}

#### Request sample
```json
{
  "activity": {
    "course": {
      "vle": {
        "type": "string",
        "name": "string",
        "url": "string",
        "client_id": "string"
      },
      "code": "string",
      "vle_course_id": "string",
      "description": "string",
      "start": "2019-08-24T14:15:22Z",
      "end": "2019-08-24T14:15:22Z"
    },
    "vle_activity_type": "string",
    "vle_activity_id": "string",
    "description": "string",
    "name": "string",
    "enabled": true,
    "start": "2019-08-24T14:15:22Z",
    "end": "2019-08-24T14:15:22Z",
    "conf": "string"
  },
  "options": {},
  "active": true,
  "instrument": 0,
  "alternative_to": 0
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
  "activity": {
    "id": 0,
    "course": {
      "id": 0,
      "vle": {
        "id": 0,
        "type": "string",
        "name": "string",
        "url": "string",
        "client_id": "string"
      },
      "code": "string",
      "vle_course_id": "string",
      "description": "string",
      "start": "2019-08-24T14:15:22Z",
      "end": "2019-08-24T14:15:22Z",
      "created_at": "2019-08-24T14:15:22Z",
      "updated_at": "2019-08-24T14:15:22Z"
    },
    "vle_activity_type": "string",
    "vle_activity_id": "string",
    "description": "string",
    "name": "string",
    "enabled": true,
    "start": "2019-08-24T14:15:22Z",
    "end": "2019-08-24T14:15:22Z",
    "conf": "string",
    "created_at": "2019-08-24T14:15:22Z",
    "updated_at": "2019-08-24T14:15:22Z"
  },
  "options": {},
  "active": true,
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z",
  "instrument": 0,
  "alternative_to": 0
}
```
</details>

<div align="right">

[[top section]](#vle_course_activity_instrument_management) [[top page]](#table-of-content) 
</div>
<br>


<!--- vle_course_activity_instrument_partial_update --->
## 8.5 Partial Update VLE Course Activity Instrument <a name="vle_course_activity_instrument_partial_update"></a>
API endpoint that updates an Activity's Instrument from a Course in a VLE.

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
        <td><span style="word-wrap: break-word">/api/v2/vle/{parent_lookup_vle_id}/course/{parent_lookup_course_id}/activity/{parent_lookup_activity_id}/instrument/{id}/</span></td>
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
              <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_activity_id</strong><br><code>required</code></td>
                <td>string </td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_course_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>              
            <tr>
                <td><strong>parent_lookup_vle_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>
            <tr>
                <td>activity</td>
                <td>object (VLECourseActivity)</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>options</strong><br><code>required</code></td>
                <td>object (Options)<br>Nullable.</td>
                <td>-</td>
            </tr>
            <tr>
                <td><strong>active</strong><br><code>required</code></td>
                <td>boolean (Active)</td>
                <td>Is instrument active?</td>
            </tr>
            <tr>
                <td><strong>instrument</strong><br><code>required</code></td>
                <td>integer (Instrument)</td>
                <td>Activity.</td>
            </tr>
            <tr>
              <td>alternative_to</td>
              <td>integer (Alternative to)<br>Nullable.</td>
              <td>Primary instrument to be used.</td>
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
            <td>activity</td>
            <td>object (VLECourseActivity)</td>
            <td>-</td>
        </tr>
        <tr>
            <td><strong>options</strong><br><code>required</code></td>
            <td>object (Options)<br>Nullable.</td>
            <td>-</td>
        </tr>
        <tr>
            <td><strong>active</strong><br><code>required</code></td>
            <td>boolean (Active)</td>
            <td>Is instrument active?</td>
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
            <td><strong>instrument</strong><br><code>required</code></td>
            <td>integer (Instrument)</td>
            <td>Activity.</td>
        </tr>
        <tr>
          <td>alternative_to</td>
          <td>integer (Alternative to)<br>Nullable.</td>
          <td>Primary instrument to be used.</td>
        </tr>
      </tbody>
    </table>
  {{</ tab >}}
{{</ tabs >}}

#### Request sample
```json
{
  "activity": {
    "course": {
      "vle": {
        "type": "string",
        "name": "string",
        "url": "string",
        "client_id": "string"
      },
      "code": "string",
      "vle_course_id": "string",
      "description": "string",
      "start": "2019-08-24T14:15:22Z",
      "end": "2019-08-24T14:15:22Z"
    },
    "vle_activity_type": "string",
    "vle_activity_id": "string",
    "description": "string",
    "name": "string",
    "enabled": true,
    "start": "2019-08-24T14:15:22Z",
    "end": "2019-08-24T14:15:22Z",
    "conf": "string"
  },
  "options": {},
  "active": true,
  "instrument": 0,
  "alternative_to": 0
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
  "activity": {
    "id": 0,
    "course": {
      "id": 0,
      "vle": {
        "id": 0,
        "type": "string",
        "name": "string",
        "url": "string",
        "client_id": "string"
      },
      "code": "string",
      "vle_course_id": "string",
      "description": "string",
      "start": "2019-08-24T14:15:22Z",
      "end": "2019-08-24T14:15:22Z",
      "created_at": "2019-08-24T14:15:22Z",
      "updated_at": "2019-08-24T14:15:22Z"
    },
    "vle_activity_type": "string",
    "vle_activity_id": "string",
    "description": "string",
    "name": "string",
    "enabled": true,
    "start": "2019-08-24T14:15:22Z",
    "end": "2019-08-24T14:15:22Z",
    "conf": "string",
    "created_at": "2019-08-24T14:15:22Z",
    "updated_at": "2019-08-24T14:15:22Z"
  },
  "options": {},
  "active": true,
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z",
  "instrument": 0,
  "alternative_to": 0
}
```
</details>

<div align="right">

[[top section]](#vle_course_activity_instrument_management) [[top page]](#table-of-content) 
</div>
<br>



<!--- vle_course_activity_instrument_delete --->
## 8.6 Delete VLE Course Activity Instrument<a name="vle_course_activity_instrument_delete"></a>
API endpoint for deleting an Instrument from Activity.

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
        <td><span style="word-wrap: break-word">/api/v2/vle/{parent_lookup_vle_id}/course/{parent_lookup_course_id}/activity/{parent_lookup_activity_id}/instrument/{id}/</span></td>
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

### Parameters:
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
              <td>string </td>
              <td>Request path parameter.</td>
            </tr>
            <tr>
                <td><strong>parent_lookup_activity_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>              
            <tr>
                <td><strong>parent_lookup_course_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
            </tr>              
            <tr>
                <td><strong>parent_lookup_vle_id</strong><br><code>required</code></td>
                <td>string</td>
                <td>Request path parameter.</td>
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

<div align="right">

[[top section]](#vle_course_activity_instrument_management) [[top page]](#table-of-content) 
</div>
<br>

<br><br><br>

# 9. VLE Course Activity Learner Management <a name="vle_course_activity_learner_management"></a>
---

{{< notice note >}}
**Section TBD** <br>
{{</ notice >}}

<br><br><br>

# 10. VLE Course Activity Report Management <a name="vle_course_activity_report_management"></a>
---

  10.1 [List VLE Course Activity Report](#vle_course_activity_report_list)<br>
  10.2 [Read VLE Course Activity Report](#vle_course_activity_report_read)<br><br>


<!--- vle_course_activity_report_list --->
## 10.1 List VLE Course Activity Report <a name="vle_course_activity_report_list"></a>

API endpoint for listing Activity Reports from a Course in a VLE.

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
        <td><span style="word-wrap: break-word">/api/v2/vle/{parent_lookup_activity__vle_id}/course/{parent_lookup_activity__course_id}/activity/{parent_lookup_activity_id}/report/</span></td>
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
          <td><strong>parent_lookup_activity__vle_id</strong><br><code>required</code></td>
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
              <td>integer</td>
              <td>-</td>
          </tr>
          <tr>
              <td>next</td>
              <td>string &lt;uri&gt;<br>Nullable</td>
              <td>-</td>
          </tr>
          <tr>
              <td>previous</td>
              <td>string &lt;uri&gt;<br>Nullable</td>
              <td>-</td>
          </tr>
          <tr>
              <td>results<br><code>required</code></td>
              <td>Array of Objects (VLECourseActivityReport)</td>
              <td>-</td>
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

<div align="right">

[[top section]](#vle_course_activity_report_management) [[top page]](#table-of-content) 
</div>
<br>


<!--- vle_course_activity_report_read --->
## 10.2 Read VLE Course Activity Report<a name="vle_course_activity_report_read"></a>
Retrieves Activity Report from a Course in a VLE.

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
        <td><span style="word-wrap: break-word">/api/v2/vle/{parent_lookup_activity__vle_id}/course/{parent_lookup_activity__course_id}/activity/{parent_lookup_activity_id}/report/{id}/</span></td>
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
              <td>string </td>
              <td>Request path parameter.A unique integer value identifying this report activity.</td>
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
              <td><strong>parent_lookup_activity__vle_id</strong><br><code>required</code></td>
              <td>string </td>
              <td>Request path parameter.</td>
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
              <td><strong>learner</strong><br><code>required</code></td>
              <td>object (VLECourseActivityReportLearner)</td>
              <td>-</td>
          </tr>
          <tr>
              <td><strong>detail</strong><br><code>required</code></td>
              <td>Array of Objects (VLECourseActivityReportDetail)</td>
              <td>-</td>
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
```
</details>


<div align="right">

[[top section]](#vle_course_activity_report_management) [[top page]](#table-of-content) 
</div>

**********

<br><br><br><br>
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

```html
<head>
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
