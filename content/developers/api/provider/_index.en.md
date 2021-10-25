---
title: "Provider"
weight: 4
draft: false
# search related keywords
keywords: ["API","provider"]
---

{{< notice info >}}
  **This page is under construction** <br>
  We're working on it!
{{</ notice >}}

<table><tr><td>

# Table of Content
1. [Provider Management](#provider_management)
2. [Provider Enrolment Management](#provider_enrolment_management)
3. [Provider Enrolment Sample Management](#provider_enrolment_sample_management)
4. [Provider Enrolment Sample Validation Management](#provider_enrolment_sample_validation_management)
5. [Provider Notification Management](#provider_notification_management)
6. [Provider Request Management](#provider_request_management)

</td></tr></table>

<br><br>

# 1. Provider Management <a name="provider_management"></a> 
---
Set of API endpoints that allow Providers to be viewed or edited.

  1.1 GET: [List Providers](#provider_list)<br>
  1.2 GET: [Read Provider](#provider_read)
<br><br>

<!--- provider_list --->
## 1.1 List Providers <a name="provider_list"></a>

API endpoint for listing Providers.

### Request

Concept | Data
-- | --
HTTP Method | <code>**GET**</code>
Path | /api/v2/provider/
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
          <tr class="last undefined">
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
              <td>Array of Objects (Provider)</td>
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
      "id": "string",
      "instrument": {
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
      },
      "name": "string",
      "queue": "string",
      "description": "string",
      "url": "string",
      "version": "string",
      "acronym": "string",
      "allow_validation": true,
      "inverted_polarity": true,
      "image": "string",
      "has_service": true,
      "service_port": -2147483648,
      "options_schema": {},
      "options": {},
      "credentials": "string",
      "enabled": false,
      "validation_active": false
    }
  ]
}
  ````
</details>

<div style="text-align:right">

[[top section]](#provider_management) [[top page]](#table-of-content) 
</div>
<br>

<!--- provider_read --->
## 1.2 Read Provider<a name="provider_read"></a>
Retrieves information about a Provider.

### Request
Concept | Data
-- | --
HTTP method | <code>**GET**</code>
Path | /api/v2/provider/{id}/
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
                  <td>Request path parameter. A unique integer value identifying this provider.</td>
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
              <td>string (ID)</td>
              <td>-</td>
          </tr>
          <tr>
              <td>instrument</td>
              <td>object (Instrument)</td>
              <td>-</td>
          </tr>
          <tr>
              <td><strong>name</strong><br><code>required</code></td>
              <td>string (Name)<br>[1 .. 250] characters </td>
              <td>Provider name.</td>
          </tr>
          <tr>
              <td><strong>queue</strong><br><code>required</code></td>
              <td>string (Queue)<br>[1 .. 50] characters </td>
              <td>Queue where provider listens for requests.</td>
          </tr>
          <tr>
              <td>description</td>
              <td>string (Description)<br>Nullable. </td>
              <td>Provider description.</td>
          </tr>
          <tr>
              <td>url</td>
              <td>string (Url name)<br>[1 .. 250 characters]<br>Nullable </td>
              <td>Provider url.</td>
          </tr>
          <tr>
              <td><strong>version</strong><br><code>required</code></td>
              <td>string (Version)<br>[1 .. 15] characters </td>
              <td>Provider version.</td>
          </tr>
          <tr>
              <td><strong>acronym</strong><br><code>required</code></td>
              <td>string (Acronym)<br>[1 .. 30] characters </td>
              <td>Provider acronym.</td>
          </tr>
          <tr>
              <td>allow_validation</td>
              <td>boolean (Allow validation)</td>
              <td>Whether this provider provides validation feature for data.</td>
          </tr>
          <tr>
              <td>inverted_polarity</td>
              <td>boolean (Inverted polarity)</td>
              <td>If enabled, good values are lower values.</td>
          </tr>
          <tr>
              <td><strong>image</strong><br><code>required</code></td>
              <td>string (Image)<br>[1 .. 250] characters</td>
              <td>Provider Docker image.</td>
          </tr>
          <tr>
              <td>has_service</td>
              <td>boolean (Has service)</td>
              <td>Whether this provider starts a service and must be balanced.</td>
          </tr>
          <tr>
              <td>service_port</td>
              <td>integer (service Port)<br>[ -2147483648 .. 2147483647 ] <br>Nullable</td>
              <td>Port where service is listening.</td>
          </tr>
          <tr>
              <td>options_schema</td>
              <td>object (Options schema)<br>Nullable </td>
              <td>-</td>
          </tr>
          <tr>
              <td>options</td>
              <td>object (Options)<br>Nullable </td>
              <td>-</td>
          </tr>
          <tr>
              <td>credentials</td>
              <td>string (Credentials)</td>
              <td>-</td>
          </tr>
          <tr>
              <td>enabled</td>
              <td>boolean (Enabled)<br>Nullable </td>
              <td>Default: false</td>
          </tr>
          <tr>
              <td>validation_active</td>
              <td>boolean (Validation active)<br>Nullable </td>
              <td>Default: false</td>
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
  "instrument": {
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
  },
  "name": "string",
  "queue": "string",
  "description": "string",
  "url": "string",
  "version": "string",
  "acronym": "string",
  "allow_validation": true,
  "inverted_polarity": true,
  "image": "string",
  "has_service": true,
  "service_port": -2147483648,
  "options_schema": {},
  "options": {},
  "credentials": "string",
  "enabled": false,
  "validation_active": false
}
```
</details>


<div style="text-align:right">

[[top section]](#provider_management) [[top page]](#table-of-content) 
</div>
<br><br><br>


# 2. Provider Enrolment Management <a name="provider_enrolment_management"></a> 
---
Set of API endpoints that allow Provider access enrolment samples.

  2.1 GET: [List Provider Enrolment](#provider_enrolment_list)<br>
  2.2 POST: [Create Provider Enrolment](#provider_enrolment_create)<br>
  2.3 GET: [Read Provider Enrolment](#provider_enrolment_read)<br>
  2.4 PUT: [Update Provider Enrolment](#provider_enrolment_update)<br>
  2.5 PATCH: [Partial Update Provider Enrolment](#provider_enrolment_partial_update)<br>
  2.6 DELETE: [Delete Provider Enrolment](#provider_enrolment_delete)<br>
  2.7 GET: [Provider Enrolment Available Samples](#provider_enrolment_available_samples)<br>
  2.8 POST: [Unlock Provider Enrolment](#provider_enrolment_unlock)<br>
  2.9 GET: [Provider Enrolment Used Samples](#provider_enrolment_used_samples)

<br><br>


<!--- provider_enrolment_list --->
## 2.1 List Provider Enrolment<a name="provider_enrolment_list"></a>

API endpoint for listing Provider Enrolment.

### Request

Concept | Data
-- | --
HTTP Method | <code>**GET**</code>
Path | /api/v2/provider/{parent_lookup_provider_id}/enrolment/
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
                      <td><strong>parent_lookup_provider_id</strong><br><code>required</code></td>
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
                  <td>integer</td>
                  <td>-</td>
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
              <td>Array of objects (ProviderEnrolment)</td>
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
      "learner_id": "2df776db-09df-4cb9-a2af-db56cada6cb7",
      "model": "http://example.com",
      "is_locked": true,
      "task_id": "736fde4d-9029-4915-8189-01353d6982cb",
      "model_upload_url": "string",
      "percentage": 0,
      "can_analyse": false,
      "model_total_samples": 0,
      "used_samples": []
    }
  ]
}
  ````
</details>

<div style="text-align:right">

[[top section]](#provider_enrolment_management) [[top page]](#table-of-content) 
</div>
<br>

<!--- provider_enrolment_create --->
## 2.2 Create Provider Enrolment<a name="provider_enrolment_create"></a>

API endpoint for creating a new Provider Enrolment.

### Request

Concept | Data
-- | --
HTTP Method | <code>**POST**</code>
Path | /api/v2/provider/{parent_lookup_provider_id}/enrolment/
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
                      <td><strong>parent_lookup_provider_id</strong><br><code>required</code></td>
                      <td>string</td>
                      <td>Request path parameter.</td>
              </tr>
              <tr>
                      <td><strong>learner_id</strong><br><code>required</code></td>
                      <td>string &lt;uuid&gt; (Learner id)</td>
                      <td>-</td>
              </tr>
              <tr>
                      <td><strong>task_id</strong><br><code>required</code></td>
                      <td>string &lt;uuid&gt; (Task id)</td>
                      <td>-</td>
              </tr>
              <tr>
                  <td>percentage</td>
                  <td>number (Percentage)</td>
                  <td>Default: 0</td>
              </tr>
              <tr>
                  <td>can_analyse</td>
                  <td>boolean (Can analyse)</td>
                  <td>Default: false</td>
              </tr>
              <tr>
                  <td>used_samples</td>
                  <td>Array of integers<br>Nullable.</td>
                  <td>Default: []</td>
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
              <td><strong>learner_id</strong><br><code>required</code></td>
              <td>string &lt;uuid&gt; (Learner id)</td>
              <td>-</td>
            </tr>
            <tr>
                <td>model</td>
                <td>string &lt;uri&gt; (Model)</td>
                <td>Default: 0</td>
            </tr>
            <tr>
                <td>is_locked</td>
                <td>boolean (Is locked)</td>
                <td>-</td>
            </tr>
            <tr>
              <td><strong>task_id</strong><br><code>required</code></td>
              <td>string &lt;uuid&gt; (Task id)</td>
              <td>-</td>
            </tr>
            <tr>
                <td>model_upload_url</td>
                <td>string (Model upload url)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>percentage</td>
                <td>number (Percentage)</td>
                <td>Default: 0</td>
            </tr>
            <tr>
                <td>can_analyse</td>
                <td>boolean (Can analyse)</td>
                <td>Default: false</td>
            </tr>
            <tr>
                <td>model_total_samples</td>
                <td>integer (Model total samples)</td>
                <td>-</td>
            </tr>
            <tr>
                <td>used_samples</td>
                <td>Array of integers<br>Nullable.</td>
                <td>Default: []</td>
            </tr>
         </tbody>
        </table>
   {{</tab>}}
{{</tabs>}}

#### Request Sample: 

```json
{
  "learner_id": "2df776db-09df-4cb9-a2af-db56cada6cb7",
  "task_id": "736fde4d-9029-4915-8189-01353d6982cb",
  "percentage": 0,
  "can_analyse": false,
  "used_samples": []
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
  "learner_id": "2df776db-09df-4cb9-a2af-db56cada6cb7",
  "model": "http://example.com",
  "is_locked": true,
  "task_id": "736fde4d-9029-4915-8189-01353d6982cb",
  "model_upload_url": "string",
  "percentage": 0,
  "can_analyse": false,
  "model_total_samples": 0,
  "used_samples": []
}
  ````
</details>

<div style="text-align:right">

[[top section]](#provider_enrolment_management) [[top page]](#table-of-content) 
</div>
<br>

<!--- provider_enrolment_read --->
## 2.3 Read Provider Enrolment<a name="provider_enrolment_read"></a>
Retrieves information about Provider access enrolment samples.

### Request
Concept | Data
-- | --
HTTP method | <code>**GET**</code>
Path | /api/v2/provider/{parent_lookup_provider_id}/enrolment/{learner__learner_id}/
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
                  <td><strong>learner__learner_id</strong><br><code>required</code></td>
                  <td>string </td>
                  <td>Request path parameter.</td>
              </tr>
              <tr>
                  <td><strong>parent_lookup_provider_id</strong><br><code>required</code></td>
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
          <td><strong>learner_id</strong><br><code>required</code></td>
          <td>string &lt;uuid&gt; (Learner id)</td>
          <td>-</td>
        </tr>
        <tr>
            <td>model</td>
            <td>string &lt;uri&gt; (Model)</td>
            <td>Default: 0</td>
        </tr>
        <tr>
            <td>is_locked</td>
            <td>boolean (Is locked)</td>
            <td>-</td>
        </tr>
        <tr>
          <td><strong>task_id</strong><br><code>required</code></td>
          <td>string &lt;uuid&gt; (Task id)</td>
          <td>-</td>
        </tr>
        <tr>
            <td>model_upload_url</td>
            <td>string (Model upload url)</td>
            <td>-</td>
        </tr>
        <tr>
            <td>percentage</td>
            <td>number (Percentage)</td>
            <td>Default: 0</td>
        </tr>
        <tr>
            <td>can_analyse</td>
            <td>boolean (Can analyse)</td>
            <td>Default: false</td>
        </tr>
        <tr>
            <td>model_total_samples</td>
            <td>integer (Model total samples)</td>
            <td>-</td>
        </tr>
        <tr>
            <td>used_samples</td>
            <td>Array of integers<br>Nullable.</td>
            <td>Default: []</td>
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
  "learner_id": "2df776db-09df-4cb9-a2af-db56cada6cb7",
  "model": "http://example.com",
  "is_locked": true,
  "task_id": "736fde4d-9029-4915-8189-01353d6982cb",
  "model_upload_url": "string",
  "percentage": 0,
  "can_analyse": false,
  "model_total_samples": 0,
  "used_samples": []
}
```
</details>

<div style="text-align:right">

[[top section]](#provider_enrolment_management) [[top page]](#table-of-content) 
</div>
<br>

<!--- provider_enrolment_update --->
## 2.4 Update Provider Enrolment<a name="provider_enrolment_update"></a>
API endpoint that updates Provider access enrolment samples.

### Request
Concept | Data
-- | --
HTTP method | <code>**PUT**</code>
Path | /api/v2/provider/{parent_lookup_provider_id}/enrolment/{learner__learner_id}/
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
                  <td><strong>learner__learner_id</strong><br><code>required</code></td>
                  <td>string </td>
                  <td>Request path parameter.</td>
              </tr>
              <tr>
                  <td><strong>parent_lookup_provider_id</strong><br><code>required</code></td>
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
          <td><strong>learner_id</strong><br><code>required</code></td>
          <td>string &lt;uuid&gt; (Learner id)</td>
          <td>-</td>
        </tr>
        <tr>
          <td><strong>task_id</strong><br><code>required</code></td>
          <td>string &lt;uuid&gt; (Task id)</td>
          <td>-</td>
        </tr>
        <tr>
            <td>percentage</td>
            <td>number (Percentage)</td>
            <td>Default: 0</td>
        </tr>
        <tr>
            <td>can_analyse</td>
            <td>boolean (Can analyse)</td>
            <td>Default: false</td>
        </tr>
        <tr>
            <td>used_samples</td>
            <td>Array of integers<br>Nullable.</td>
            <td>Default: []</td>
        </tr>
      </tbody>
    </table>
  {{</ tab >}}
{{</ tabs >}}

#### Request sample
```json
{
  "learner_id": "2df776db-09df-4cb9-a2af-db56cada6cb7",
  "task_id": "736fde4d-9029-4915-8189-01353d6982cb",
  "percentage": 0,
  "can_analyse": false,
  "used_samples": []
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
  "learner_id": "2df776db-09df-4cb9-a2af-db56cada6cb7",
  "model": "http://example.com",
  "is_locked": true,
  "task_id": "736fde4d-9029-4915-8189-01353d6982cb",
  "model_upload_url": "string",
  "percentage": 0,
  "can_analyse": false,
  "model_total_samples": 0,
  "used_samples": []
}
```
</details>

<div style="text-align:right">

[[top section]](#provider_enrolment_management) [[top page]](#table-of-content) 
</div>
<br>

<!--- provider_enrolment_partial_update --->
## 2.5 Partial Update Provider Enrolment <a name="provider_enrolment_partial_update"></a>
API endpoint that updates Provider access enrolment samples' information.

### Request
Concept | Data
-- | --
HTTP method | <code>**PATCH**</code>
Path | /api/v2/provider/{parent_lookup_provider_id}/enrolment/{learner__learner_id}/
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
              <td><strong>learner__learner_id</strong><br><code>required</code></td>
              <td>string </td>
              <td>Request path parameter.</td>
            </tr>
            <tr>
              <td><strong>parent_lookup_provider_id</strong><br><code>required</code></td>
              <td>string </td>
              <td>Request path parameter.</td>
            </tr>
            <tr>
              <td><strong>learner_id</strong><br><code>required</code></td>
              <td>string &lt;uuid&gt; (Learner id)</td>
              <td>-</td>
            </tr>
            <tr>
              <td><strong>task_id</strong><br><code>required</code></td>
              <td>string &lt;uuid&gt; (Task id)</td>
              <td>-</td>
            </tr>
            <tr>
                <td>percentage</td>
                <td>number (Percentage)</td>
                <td>Default: 0</td>
            </tr>
            <tr>
                <td>can_analyse</td>
                <td>boolean (Can analyse)</td>
                <td>Default: false</td>
            </tr>
            <tr>
                <td>used_samples</td>
                <td>Array of integers<br>Nullable.</td>
                <td>Default: []</td>
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
          <td><strong>learner_id</strong><br><code>required</code></td>
          <td>string &lt;uuid&gt; (Learner id)</td>
          <td>-</td>
        </tr>
        <tr>
            <td>model</td>
            <td>string &lt;uri&gt; (Model)</td>
            <td>-</td>
        </tr>
        <tr>
            <td>is_locked</td>
            <td>boolean (Is locked)</td>
            <td>-/td>
        </tr>
        <tr>
          <td><strong>task_id</strong><br><code>required</code></td>
          <td>string &lt;uuid&gt; (Task id)</td>
          <td>-</td>
        </tr>
        <tr>
            <td>model_upload_url</td>
            <td>string (Model upload url)</td>
            <td>-</td>
        </tr>
        <tr>
            <td>percentage</td>
            <td>number (Percentage)</td>
            <td>Default: 0</td>
        </tr>
        <tr>
            <td>can_analyse</td>
            <td>boolean (Can analyse)</td>
            <td>Default: false</td>
        </tr>
        <tr>
            <td>model_total_samples</td>
            <td>integer (Model total samples)</td>
            <td>-</td>
        </tr>
        <tr>
            <td>used_samples</td>
            <td>Array of integers<br>Nullable.</td>
            <td>Default: []</td>
        </tr>
      </tbody>
    </table>
  {{</ tab >}}
{{</ tabs >}}

#### Request sample
```json
{
  "learner_id": "2df776db-09df-4cb9-a2af-db56cada6cb7",
  "task_id": "736fde4d-9029-4915-8189-01353d6982cb",
  "percentage": 0,
  "can_analyse": false,
  "used_samples": []
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
  "learner_id": "2df776db-09df-4cb9-a2af-db56cada6cb7",
  "model": "http://example.com",
  "is_locked": true,
  "task_id": "736fde4d-9029-4915-8189-01353d6982cb",
  "model_upload_url": "string",
  "percentage": 0,
  "can_analyse": false,
  "model_total_samples": 0,
  "used_samples": []
}
```
</details>

<div style="text-align:right">

[[top section]](#provider_enrolment_management) [[top page]](#table-of-content) 
</div>
<br>


<!--- provider_enrolment_delete --->
## 2.6 Delete Provider Enrolment<a name="provider_enrolment_delete"></a>
API endpoint for deleting Provider access enrolment samples.

### Request
Concept | Data
-- | --
HTTP Method | <code>**DELETE**</code>
Path | /api/v2/provider/{parent_lookup_provider_id}/enrolment/{learner__learner_id}/
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
              <td><strong>learner__learner_id</strong><br><code>required</code></td>
              <td>string </td>
              <td>Request path parameter.</td>
            </tr>
            <tr>
              <td><strong>parent_lookup_provider_id</strong><br><code>required</code></td>
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

<div style="text-align:right">

[[top section]](#provider_enrolment_management) [[top page]](#table-of-content) 
</div>
<br>

<!--- provider_enrolment_available_samples --->
## 2.7 Provider Enrolment Available Samples<a name="provider_enrolment_available_samples"></a>
Get available samples for this enrolment model.

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
        <td><span style="word-wrap: break-word">/api/v2/provider/{parent_lookup_provider_id}/enrolment/{learner__learner_id}/available_samples/</span></td>
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
              <td><strong>learner__learner_id</strong><br><code>required</code></td>
              <td>string </td>
              <td>Request path parameter.</td>
            </tr>
            <tr>
              <td><strong>parent_lookup_provider_id</strong><br><code>required</code></td>
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
              <td>learner_id</td>
              <td>string &lt;uuid&gt; (Learner id)</td>
              <td>-</td>
            </tr>
            <tr>
                <td>data</td>
                <td>string &lt;uri&gt; (Data)</td>
                <td>-</td>
            </tr>
         </tbody>
        </table>
  {{</ tab >}} 
{{</tabs>}}

### Responses

#### Response sample: 200
<details>
  <summary>200</summary>

```json
{
  "id": 0,
  "learner_id": "2df776db-09df-4cb9-a2af-db56cada6cb7",
  "data": "http://example.com"
}
```
</details>

<div style="text-align:right">

[[top section]](#provider_enrolment_management) [[top page]](#table-of-content) 
</div>
<br>

<!--- provider_enrolment_unlock --->
## 2.8 Unlock Provider Enrolment<a name="provider_enrolment_unlock"></a>
API endpoint for unlocking a locked model.

### Request
Concept | Data
-- | --
HTTP Method | <code>**POST**</code>
Path | /api/v2/provider/{parent_lookup_provider_id}/enrolment/{learner__learner_id}/unlock/
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
              <td><strong>learner__learner_id</strong><br><code>required</code></td>
              <td>string </td>
              <td>Request path parameter.</td>
            </tr>
            <tr>
              <td><strong>parent_lookup_provider_id</strong><br><code>required</code></td>
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
              <td>learner_id</td>
              <td>string &lt;uuid&gt; (Learner id)</td>
              <td>-</td>
            </tr>
            <tr>
                <td>data</td>
                <td>string &lt;uri&gt; (Data)</td>
                <td>-</td>
            </tr>
         </tbody>
        </table>
  {{</ tab >}} 
{{</tabs>}}

### Responses

#### Response sample: 201
<details>
  <summary>201</summary>

```json
{
  "id": 0,
  "learner_id": "2df776db-09df-4cb9-a2af-db56cada6cb7",
  "data": "http://example.com"
}
```
</details>


<div style="text-align:right">

[[top section]](#provider_enrolment_management) [[top page]](#table-of-content) 
</div>
<br>

<!--- provider_enrolment_used_samples --->
## 2.9 Provider Enrolment Used Samples<a name="provider_enrolment_used_samples"></a>
Get used samples for this enrolment model.

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
        <td><span style="word-wrap: break-word">/api/v2/provider/{parent_lookup_provider_id}/enrolment/{learner__learner_id}/used_samples/</span></td>
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
              <td><strong>learner__learner_id</strong><br><code>required</code></td>
              <td>string </td>
              <td>Request path parameter.</td>
            </tr>
            <tr>
              <td><strong>parent_lookup_provider_id</strong><br><code>required</code></td>
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
              <td>learner_id</td>
              <td>string &lt;uuid&gt; (Learner id)</td>
              <td>-</td>
            </tr>
            <tr>
                <td>data</td>
                <td>string &lt;uri&gt; (Data)</td>
                <td>-</td>
            </tr>
         </tbody>
        </table>
  {{</ tab >}} 
{{</tabs>}}

### Responses

#### Response sample: 200
<details>
  <summary>200</summary>

```json
{
  "id": 0,
  "learner_id": "2df776db-09df-4cb9-a2af-db56cada6cb7",
  "data": "http://example.com"
}
```
</details>


<div style="text-align:right">

[[top section]](#provider_enrolment_management) [[top page]](#table-of-content) 
</div>



<br><br><br>

# 3. Provider Enrolment Sample Management <a name="provider_enrolment_sample_management"></a>
---
Set of API endpoints that allow Provider access enrolment samples to be viewed.

  3.1 GET: [List Providers Enrolment Sample](#provider_enrolment_sample_list)<br>
  3.2 GET: [Read Provider Enrolment Sample](#provider_enrolment_sample_read)
<br><br>

<!--- provider_enrolment_sample_list --->
## 3.1 List Providers Enrolment Sample<a name="provider_enrolment_sample_list"></a>

API endpoint for listing Provider Samples.

### Request

<!-- Using HTML table instead of markdown table because long path needs to be wrapped up -->

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
        <td><span style="word-wrap: break-word">/api/v2/provider/{parent_lookup_instruments__provider__id}/enrolment/{parent_lookup_learner__learner_id}/sample/</span></td>
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
          <td><strong>parent_lookup_instruments__provider__id</strong><br><code>required</code></td>
          <td>string </td>
          <td>Request path parameter.</td>
        </tr>
        <tr>
          <td><strong>parent_lookup_learner__learner_id</strong><br><code>required</code></td>
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
              <td>Array of Objects (Provider)</td>
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
      "learner_id": "2df776db-09df-4cb9-a2af-db56cada6cb7",
      "data": "http://example.com"
    }
  ]
}
  ````
</details>

<div style="text-align:right">

[[top section]](#provider_enrolment_sample_management) [[top page]](#table-of-content) 
</div>
<br>

<!--- provider_enrolment_sample_read --->
## 3.2 Read Provider Enrolment Sample<a name="provider_enrolment_sample_read"></a>
Retrieves information about Provider access enrolment samples.

### Request
<!-- Using HTML table instead of markdown table because long path needs to be wrapped up -->

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
        <td><span style="word-wrap: break-word">/api/v2/provider/{parent_lookup_instruments__provider__id}/enrolment/{parent_lookup_learner__learner_id}/sample/{id}/</span></td>
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
              <td>integer </td>
              <td>Request path parameter. A unique integer value identifying this enrolment sample.</td>
            </tr>
            <tr>
              <td><strong>parent_lookup_instruments__provider__id</strong><br><code>required</code></td>
              <td>string </td>
              <td>Request path parameter.</td>
            </tr>
            <tr>
              <td><strong>parent_lookup_learner__learner_id</strong><br><code>required</code></td>
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
              <td>string (ID)</td>
              <td>-</td>
          </tr>
          <tr>
              <td>learner_id</td>
              <td>string &lt;uuid&gt; (Learner id)</td>
              <td>-</td>
          </tr>
         <tr>
              <td>data</td>
              <td>string &lt;uuid&gt; (Data)</td>
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
  "learner_id": "2df776db-09df-4cb9-a2af-db56cada6cb7",
  "data": "http://example.com"
}
```
</details>

<div style="text-align:right">

[[top section]](#provider_enrolment_sample_management) [[top page]](#table-of-content) 
</div>


<br><br><br>

# 4. Provider Enrolment Sample Validation Management <a name="provider_enrolment_sample_validation_management"></a>
---
Set of API endpoints that allows Provider manage enrolment sample validation.
<br>
  4.1 GET: [List Provider Enrolment Sample Validation](#provider_enrolment_sample_validation_list)<br>
  4.2 POST: [Create Provider Enrolment Sample Validation](#provider_enrolment_sample_validation_create)<br>
  4.3 GET: [Read Provider Enrolment Sample Validation](#provider_enrolment_sample_validation_read)<br>
  4.4 PUT: [Update Provider Enrolment Sample Validation](#provider_enrolment_sample_validation_update)<br>
  4.5 PATCH: [Partial Update Provider Enrolment Sample Validation Information](#provider_enrolment_sample_validation_partial_update)<br>
  4.6 DELETE: [Delete Provider Enrolment Sample Validation](#provider_enrolment_sample_validation_delete)<br>
  4.7 POST: [Status Provider Enrolment Sample Validation](#provider_enrolment_sample_validation_status)<br>

<br><br>

<!--- provider_enrolment_sample_validation_list --->
## 4.1 List Provider Enrolment Sample Validation<a name="provider_enrolment_sample_validation_list"></a>
API endpoint for listing all Provider manage enrolment sample validation.

### Request
<!-- Using HTML table instead of markdown table because long path needs to be wrapped up -->

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
        <td><span style="word-wrap: break-word">/api/v2/provider/{parent_lookup_provider_id}/enrolment/{parent_lookup_sample__learner__learner_id}/sample/{parent_lookup_sample_id}/validation/</span></td>
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
                  <td><strong>parent_lookup_provider_id</strong><br><code>required</code></td>
                  <td>string </td>
                  <td>Request path parameter.</td>
                </tr>
                <tr>
                  <td><strong>parent_lookup_sample__learner__learner_id</strong><br><code>required</code></td>
                  <td>string </td>
                  <td>Request path parameter.</td>
                </tr>
                <tr>
                  <td><strong>parent_lookup_sample_id</strong><br><code>required</code></td>
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
                  <td>Array of Objects (Provider)</td>
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
      "status": 0,
      "info": "http://example.com",
      "validation_info": {},
      "provider": 0,
      "sample": {
        "id": 0,
        "learner_id": "2df776db-09df-4cb9-a2af-db56cada6cb7",
        "data": "http://example.com"
      },
      "error_message": "string",
      "contribution": 0,
      "message_code_id": "string"
    }
  ]
}
  ````
</details>

<div style="text-align:right">

[[top section]](#provider_enrolment_sample_validation_management) [[top page]](#table-of-content) 
</div>
<br>


<!--- provider_enrolment_sample_validation_create --->
## 4.2 Create Provider Enrolment Sample Validation<a name="provider_enrolment_sample_validation_create"></a>
API endpoint for creating new Provider Enrolment Sample Validation.

### Request
<!-- Using HTML table instead of markdown table because long path needs to be wrapped up -->

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
        <td><span style="word-wrap: break-word">/api/v2/provider/{parent_lookup_provider_id}/enrolment/{parent_lookup_sample__learner__learner_id}/sample/{parent_lookup_sample_id}/validation/</span></td>
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
                  <td><strong>parent_lookup_provider_id</strong><br><code>required</code></td>
                  <td>string </td>
                  <td>Request path parameter.</td>
                </tr>
                <tr>
                  <td><strong>parent_lookup_sample__learner__learner_id</strong><br><code>required</code></td>
                  <td>string </td>
                  <td>Request path parameter.</td>
                </tr>
                <tr>
                  <td><strong>parent_lookup_sample_id</strong><br><code>required</code></td>
                  <td>string </td>
                  <td>Request path parameter.</td>
                </tr>
              <tr>
                      <td>status</td>
                      <td>integer (Status) <br>Enum: 0, 1, 2, 3, 4</td>
                      <td>Validation status for this sample.</td>
              </tr>
              <tr>
                      <td>validation_info</td>
                      <td>object (Validation info) <br>Nullable</td>
                      <td>-</td>
              </tr>
              <tr>
                      <td>sample</td>
                      <td>object (ProviderEnrolmentSample)</td>
                      <td>-</td>
              </tr>
              <tr>
                      <td>error_message</td>
                      <td>string (Error message) <br>non-empty<br>Nullable</td>
                      <td>Error message when status is error.</td>
              </tr>
              <tr>
                  <td>contribution</td>
                  <td>number (Contribution)<br>Nullable.</td>
                  <td>-</td>
              </tr>
              <tr>
                  <td>requires_enrolment</td>
                  <td>boolean (Requires enrolment)</td>
                  <td>Whether this instrument requires enrolment.</td>
              </tr>
              <tr>
                  <td>message_code_id</td>
                  <td>string (Message code id) <br>non-empty<br>Nullable.</td>
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
                      <td>status</td>
                      <td>integer (Status) <br>Enum: 0, 1, 2, 3, 4</td>
                      <td>Validation status for this sample.</td>
              </tr>
              <tr>
                      <td>info</td>
                      <td>string &lt;uri&gt; (Info)<br>Nullable.</td>
                      <td>-</td>
              </tr>
              <tr>
                      <td>validation_info</td>
                      <td>object (Validation info) <br>Nullable</td>
                      <td>-</td>
              </tr>
              <tr>
                      <td>provider</td>
                      <td>integer (Provider)</td>
                      <td>-</td>
              </tr>
              <tr>
                      <td>sample</td>
                      <td>object (ProviderEnrolmentSample)</td>
                      <td>-</td>
              </tr>
              <tr>
                      <td>error_message</td>
                      <td>string (Error message) <br>non-empty<br>Nullable</td>
                      <td>Error message when status is error.</td>
              </tr>
              <tr>
                  <td>contribution</td>
                  <td>number (Contribution)<br>Nullable.</td>
                  <td>-</td>
              </tr>
              <tr>
                  <td>message_code_id</td>
                  <td>string (Message code id) <br>non-empty<br>Nullable.</td>
                  <td>-</td>
              </tr>
         </tbody>
        </table>
   {{</tab>}}
{{</tabs>}}

#### Request Sample: 

```json
{
  "status": 0,
  "validation_info": {},
  "sample": {},
  "error_message": "string",
  "contribution": 0,
  "message_code_id": "string"
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
  "status": 0,
  "info": "http://example.com",
  "validation_info": {},
  "provider": 0,
  "sample": {
    "id": 0,
    "learner_id": "2df776db-09df-4cb9-a2af-db56cada6cb7",
    "data": "http://example.com"
  },
  "error_message": "string",
  "contribution": 0,
  "message_code_id": "string"
}
  ````
</details>

<div style="text-align:right">

[[top section]](#provider_enrolment_sample_validation_management) [[top page]](#table-of-content) 
</div>
<br>

<!--- provider_enrolment_sample_validation_read --->
## 4.3 Read Provider Enrolment Sample Validation<a name="provider_enrolment_sample_validation_read"></a>
API endpoint that allows Provider Enrolment Sample Validation information.

### Request
<!-- Using HTML table instead of markdown table because long path needs to be wrapped up -->

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
        <td><span style="word-wrap: break-word">/api/v2/provider/{parent_lookup_provider_id}/enrolment/{parent_lookup_sample__learner__learner_id}/sample/{parent_lookup_sample_id}/validation/{id}/</span></td>
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
                  <td>Request path parameter. A unique integer value identifying this enrolment sample validation.</td>
                </tr>
                <tr>
                  <td><strong>parent_lookup_provider_id</strong><br><code>required</code></td>
                  <td>string </td>
                  <td>Request path parameter.</td>
                </tr>
                <tr>
                  <td><strong>parent_lookup_sample__learner__learner_id</strong><br><code>required</code></td>
                  <td>string </td>
                  <td>Request path parameter.</td>
                </tr>
                <tr>
                  <td><strong>parent_lookup_sample_id</strong><br><code>required</code></td>
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
                      <td>status</td>
                      <td>integer (Status) <br>Enum: 0, 1, 2, 3, 4</td>
                      <td>Validation status for this sample.</td>
              </tr>
              <tr>
                      <td>info</td>
                      <td>string &lt;uri&gt; (Info)<br>Nullable.</td>
                      <td>-</td>
              </tr>
              <tr>
                      <td>validation_info</td>
                      <td>object (Validation info) <br>Nullable</td>
                      <td>-</td>
              </tr>
              <tr>
                      <td>provider</td>
                      <td>integer (Provider)</td>
                      <td>-</td>
              </tr>
              <tr>
                      <td>sample</td>
                      <td>object (ProviderEnrolmentSample)</td>
                      <td>-</td>
              </tr>
              <tr>
                      <td>error_message</td>
                      <td>string (Error message) <br>non-empty<br>Nullable</td>
                      <td>Error message when status is error.</td>
              </tr>
              <tr>
                  <td>contribution</td>
                  <td>number (Contribution)<br>Nullable.</td>
                  <td>-</td>
              </tr>
              <tr>
                  <td>message_code_id</td>
                  <td>string (Message code id) <br>non-empty<br>Nullable.</td>
                  <td>-</td>
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
  "status": 0,
  "info": "http://example.com",
  "validation_info": {},
  "provider": 0,
  "sample": {
    "id": 0,
    "learner_id": "2df776db-09df-4cb9-a2af-db56cada6cb7",
    "data": "http://example.com"
  },
  "error_message": "string",
  "contribution": 0,
  "message_code_id": "string"
}
```
</details>


<div style="text-align:right">

[[top section]](#provider_enrolment_sample_validation_management) [[top page]](#table-of-content) 
</div>
<br>

<!--- provider_enrolment_sample_validation_update --->
## 4.4 Update Provider Enrolment Sample Validation<a name="provider_enrolment_sample_validation_update"></a>
API endpoint that allows Provider manage enrolment sample validation updates.

### Request
<!-- Using HTML table instead of markdown table because long path needs to be wrapped up -->

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
        <td><span style="word-wrap: break-word">/api/v2/provider/{parent_lookup_provider_id}/enrolment/{parent_lookup_sample__learner__learner_id}/sample/{parent_lookup_sample_id}/validation/{id}/</span></td>
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
                  <td>Request path parameter. A unique integer value identifying this enrolment sample validation.</td>
                </tr>
                <tr>
                  <td><strong>parent_lookup_provider_id</strong><br><code>required</code></td>
                  <td>string </td>
                  <td>Request path parameter.</td>
                </tr>
                <tr>
                  <td><strong>parent_lookup_sample__learner__learner_id</strong><br><code>required</code></td>
                  <td>string </td>
                  <td>Request path parameter.</td>
                </tr>
                <tr>
                  <td><strong>parent_lookup_sample_id</strong><br><code>required</code></td>
                  <td>string </td>
                  <td>Request path parameter.</td>
                </tr>
              <tr>
                      <td>status</td>
                      <td>integer (Status) <br>Enum: 0, 1, 2, 3, 4</td>
                      <td>Validation status for this sample.</td>
              </tr>
              <tr>
                      <td>validation_info</td>
                      <td>object (Validation info) <br>Nullable</td>
                      <td>-</td>
              </tr>
              <tr>
                      <td>sample</td>
                      <td>object (ProviderEnrolmentSample)</td>
                      <td>-</td>
              </tr>
              <tr>
                      <td>error_message</td>
                      <td>string (Error message) <br>non-empty<br>Nullable</td>
                      <td>Error message when status is error.</td>
              </tr>
              <tr>
                  <td>contribution</td>
                  <td>number (Contribution)<br>Nullable.</td>
                  <td>-</td>
              </tr>
              <tr>
                  <td>message_code_id</td>
                  <td>string (Message code id) <br>non-empty<br>Nullable.</td>
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
                      <td>status</td>
                      <td>integer (Status) <br>Enum: 0, 1, 2, 3, 4</td>
                      <td>Validation status for this sample.</td>
              </tr>
              <tr>
                      <td>info</td>
                      <td>string &lt;uri&gt; (Info)<br>Nullable.</td>
                      <td>-</td>
              </tr>
              <tr>
                      <td>validation_info</td>
                      <td>object (Validation info) <br>Nullable</td>
                      <td>-</td>
              </tr>
              <tr>
                      <td>provider</td>
                      <td>integer (Provider)</td>
                      <td>-</td>
              </tr>
              <tr>
                      <td>sample</td>
                      <td>object (ProviderEnrolmentSample)</td>
                      <td>-</td>
              </tr>
              <tr>
                      <td>error_message</td>
                      <td>string (Error message) <br>non-empty<br>Nullable</td>
                      <td>Error message when status is error.</td>
              </tr>
              <tr>
                  <td>contribution</td>
                  <td>number (Contribution)<br>Nullable.</td>
                  <td>-</td>
              </tr>
              <tr>
                  <td>message_code_id</td>
                  <td>string (Message code id) <br>non-empty<br>Nullable.</td>
                  <td>-</td>
              </tr>
      </tbody>
    </table>
  {{</ tab >}}
{{</ tabs >}}

#### Request sample
```json
{
  "status": 0,
  "validation_info": {},
  "sample": {},
  "error_message": "string",
  "contribution": 0,
  "message_code_id": "string"
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
  "status": 0,
  "info": "http://example.com",
  "validation_info": {},
  "provider": 0,
  "sample": {
    "id": 0,
    "learner_id": "2df776db-09df-4cb9-a2af-db56cada6cb7",
    "data": "http://example.com"
  },
  "error_message": "string",
  "contribution": 0,
  "message_code_id": "string"
}
```
</details>


<div style="text-align:right">

[[top section]](#provider_enrolment_sample_validation_management) [[top page]](#table-of-content) 
</div>
<br>

<!--- provider_enrolment_sample_validation_partial_update --->
## 4.5 Partial Update Provider Enrolment Sample Validation Information<a name="provider_enrolment_sample_validation_partial_update"></a>
API endpoint that updates Provider manage enrolment sample validation.

### Request
<!-- Using HTML table instead of markdown table because long path needs to be wrapped up -->

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
        <td><span style="word-wrap: break-word">/api/v2/provider/{parent_lookup_provider_id}/enrolment/{parent_lookup_sample__learner__learner_id}/sample/{parent_lookup_sample_id}/validation/{id}/</span></td>
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
                  <td>Request path parameter. A unique integer value identifying this enrolment sample validation.</td>
                </tr>
                <tr>
                  <td><strong>parent_lookup_provider_id</strong><br><code>required</code></td>
                  <td>string </td>
                  <td>Request path parameter.</td>
                </tr>
                <tr>
                  <td><strong>parent_lookup_sample__learner__learner_id</strong><br><code>required</code></td>
                  <td>string </td>
                  <td>Request path parameter.</td>
                </tr>
                <tr>
                  <td><strong>parent_lookup_sample_id</strong><br><code>required</code></td>
                  <td>string </td>
                  <td>Request path parameter.</td>
                </tr>
              <tr>
                      <td>status</td>
                      <td>integer (Status) <br>Enum: 0, 1, 2, 3, 4</td>
                      <td>Validation status for this sample.</td>
              </tr>
              <tr>
                      <td>validation_info</td>
                      <td>object (Validation info) <br>Nullable</td>
                      <td>-</td>
              </tr>
              <tr>
                      <td>sample</td>
                      <td>object (ProviderEnrolmentSample)</td>
                      <td>-</td>
              </tr>
              <tr>
                      <td>error_message</td>
                      <td>string (Error message) <br>non-empty<br>Nullable</td>
                      <td>Error message when status is error.</td>
              </tr>
              <tr>
                  <td>contribution</td>
                  <td>number (Contribution)<br>Nullable.</td>
                  <td>-</td>
              </tr>
              <tr>
                  <td>message_code_id</td>
                  <td>string (Message code id) <br>non-empty<br>Nullable.</td>
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
                      <td>status</td>
                      <td>integer (Status) <br>Enum: 0, 1, 2, 3, 4</td>
                      <td>Validation status for this sample.</td>
              </tr>
              <tr>
                      <td>info</td>
                      <td>string &lt;uri&gt; (Info)<br>Nullable.</td>
                      <td>-</td>
              </tr>
              <tr>
                      <td>validation_info</td>
                      <td>object (Validation info) <br>Nullable</td>
                      <td>-</td>
              </tr>
              <tr>
                      <td>provider</td>
                      <td>integer (Provider)</td>
                      <td>-</td>
              </tr>
              <tr>
                      <td>sample</td>
                      <td>object (ProviderEnrolmentSample)</td>
                      <td>-</td>
              </tr>
              <tr>
                      <td>error_message</td>
                      <td>string (Error message) <br>non-empty<br>Nullable</td>
                      <td>Error message when status is error.</td>
              </tr>
              <tr>
                  <td>contribution</td>
                  <td>number (Contribution)<br>Nullable.</td>
                  <td>-</td>
              </tr>
              <tr>
                  <td>message_code_id</td>
                  <td>string (Message code id) <br>non-empty<br>Nullable.</td>
                  <td>-</td>
              </tr>
      </tbody>
    </table>
  {{</ tab >}}
{{</ tabs >}}

#### Request sample
```json
{
  "status": 0,
  "validation_info": {},
  "sample": {},
  "error_message": "string",
  "contribution": 0,
  "message_code_id": "string"
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
  "status": 0,
  "info": "http://example.com",
  "validation_info": {},
  "provider": 0,
  "sample": {
    "id": 0,
    "learner_id": "2df776db-09df-4cb9-a2af-db56cada6cb7",
    "data": "http://example.com"
  },
  "error_message": "string",
  "contribution": 0,
  "message_code_id": "string"
}
```
</details>


<div style="text-align:right">

[[top section]](#provider_enrolment_sample_validation_management) [[top page]](#table-of-content) 
</div>
<br>

<!--- provider_enrolment_sample_validation_delete --->
## 4.6 Delete Provider Enrolment Sample Validation<a name="provider_enrolment_sample_validation_delete"></a> 
API endpoint for deleting Provider Enrolment Sample Validation.

### Request
<!-- Using HTML table instead of markdown table because long path needs to be wrapped up -->

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
        <td><span style="word-wrap: break-word">/api/v2/provider/{parent_lookup_provider_id}/enrolment/{parent_lookup_sample__learner__learner_id}/sample/{parent_lookup_sample_id}/validation/{id}/</span></td>
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
                  <td>Request path parameter. A unique integer value identifying this enrolment sample validation.</td>
                </tr>
                <tr>
                  <td><strong>parent_lookup_provider_id</strong><br><code>required</code></td>
                  <td>string </td>
                  <td>Request path parameter.</td>
                </tr>
                <tr>
                  <td><strong>parent_lookup_sample__learner__learner_id</strong><br><code>required</code></td>
                  <td>string </td>
                  <td>Request path parameter.</td>
                </tr>
                <tr>
                  <td><strong>parent_lookup_sample_id</strong><br><code>required</code></td>
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


<div style="text-align:right">

[[top section]](#provider_enrolment_sample_validation_management) [[top page]](#table-of-content) 
</div>
<br>

<!--- provider_enrolment_sample_validation_status --->
## 4.7 Status Provider Enrolment Sample Validation<a name="provider_enrolment_sample_validation_status"></a> 
Change enrolment sample validation status.

### Request
<!-- Using HTML table instead of markdown table because long path needs to be wrapped up -->

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
        <td><span style="word-wrap: break-word">/api/v2/provider/{parent_lookup_provider_id}/enrolment/{parent_lookup_sample__learner__learner_id}/sample/{parent_lookup_sample_id}/validation/{id}/status/</span></td>
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
                  <td>Request path parameter. A unique integer value identifying this enrolment sample validation.</td>
                </tr>
                <tr>
                  <td><strong>parent_lookup_provider_id</strong><br><code>required</code></td>
                  <td>string </td>
                  <td>Request path parameter.</td>
                </tr>
                <tr>
                  <td><strong>parent_lookup_sample__learner__learner_id</strong><br><code>required</code></td>
                  <td>string </td>
                  <td>Request path parameter.</td>
                </tr>
                <tr>
                  <td><strong>parent_lookup_sample_id</strong><br><code>required</code></td>
                  <td>string </td>
                  <td>Request path parameter.</td>
                </tr>
              <tr>
                      <td>status</td>
                      <td>integer (Status) <br>Enum: 0, 1, 2, 3, 4</td>
                      <td>Validation status for this sample.</td>
              </tr>
              <tr>
                      <td>validation_info</td>
                      <td>object (Validation info) <br>Nullable</td>
                      <td>-</td>
              </tr>
              <tr>
                      <td>sample</td>
                      <td>object (ProviderEnrolmentSample)</td>
                      <td>-</td>
              </tr>
              <tr>
                      <td>error_message</td>
                      <td>string (Error message) <br>non-empty<br>Nullable</td>
                      <td>Error message when status is error.</td>
              </tr>
              <tr>
                  <td>contribution</td>
                  <td>number (Contribution)<br>Nullable.</td>
                  <td>-</td>
              </tr>
              <tr>
                  <td>message_code_id</td>
                  <td>string (Message code id) <br>non-empty<br>Nullable.</td>
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
                      <td>status</td>
                      <td>integer (Status) <br>Enum: 0, 1, 2, 3, 4</td>
                      <td>Validation status for this sample.</td>
              </tr>
              <tr>
                      <td>info</td>
                      <td>string &lt;uri&gt; (Info)<br>Nullable.</td>
                      <td>-</td>
              </tr>
              <tr>
                      <td>validation_info</td>
                      <td>object (Validation info) <br>Nullable</td>
                      <td>-</td>
              </tr>
              <tr>
                      <td>provider</td>
                      <td>integer (Provider)</td>
                      <td>-</td>
              </tr>
              <tr>
                      <td>sample</td>
                      <td>object (ProviderEnrolmentSample)</td>
                      <td>-</td>
              </tr>
              <tr>
                      <td>error_message</td>
                      <td>string (Error message) <br>non-empty<br>Nullable</td>
                      <td>Error message when status is error.</td>
              </tr>
              <tr>
                  <td>contribution</td>
                  <td>number (Contribution)<br>Nullable.</td>
                  <td>-</td>
              </tr>
              <tr>
                  <td>message_code_id</td>
                  <td>string (Message code id) <br>non-empty<br>Nullable.</td>
                  <td>-</td>
              </tr>
        </tbody>
    </table>
  {{</ tab >}}
{{</tabs>}}

#### Request sample
```json
{
  "status": 0,
  "validation_info": {},
  "sample": {},
  "error_message": "string",
  "contribution": 0,
  "message_code_id": "string"
}
```
### Responses

#### Response sample: 201
<details>
  <summary>201</summary>

```json
{
  "id": 0,
  "status": 0,
  "info": "http://example.com",
  "validation_info": {},
  "provider": 0,
  "sample": {
    "id": 0,
    "learner_id": "2df776db-09df-4cb9-a2af-db56cada6cb7",
    "data": "http://example.com"
  },
  "error_message": "string",
  "contribution": 0,
  "message_code_id": "string"
}
```
</details>

<div style="text-align:right">

[[top section]](#provider_enrolment_sample_validation_management) [[top page]](#table-of-content) 
</div>


<br><br><br>



# 5. Provider Notification Management <a name="provider_notification_management"></a>
---
Set of API endpoints that allow Provider Notification to be viewed or edited.

  5.1 GET: [List Provider Notification](#provider_notification_list)<br>
  5.2 POST: [Create Provider Notification](#provider_notification_create)<br>
  5.3 GET: [Read Provider Notification](#provider_notification_read)<br>
  5.4 PUT: [Update Provider Notification](#provider_notification_update)<br>
  5.5 PATCH: [Partial Update Provider Notification](#provider_notification_partial_update)<br>
  5.6 DELETE: [Delete Provider Notification](#provider_notification_delete)<br>

<br><br>



<!--- provider_notification_list --->
## 5.1 List Provider Notification <a name="provider_notification_list"></a>
API endpoint for listing Provider Notification.

### Request

Concept | Data
-- | --
HTTP Method | <code>**GET**</code>
Path | /api/v2/provider/{parent_lookup_provider_id}/notification/
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
                      <td><strong>parent_lookup_provider_id</strong><br><code>required</code></td>
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
                  <td>integer (ID) </td>
                  <td>-</td>
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
              <td>Array of objects (ProviderNotification)</td>
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
      "info": {},
      "provider": 0,
      "key": "string",
      "when": "2019-08-24T14:15:22Z",
      "created_at": "2019-08-24T14:15:22Z",
      "updated_at": "2019-08-24T14:15:22Z"
    }
  ]
}
  ````
</details>



<div style="text-align:right">

[[top section]](#provider_notification_management) [[top page]](#table-of-content) 
</div>

<br>

<!--- provider_notification_create --->
## 5.2 Create Provider Notification<a name="provider_notification_create"></a>
API endpoint for creating a new Provider Notification.

### Request

Concept | Data
-- | --
HTTP Method | <code>**POST**</code>
Path | /api/v2/provider/{parent_lookup_provider_id}/notification/
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
                      <td><strong>parent_lookup_provider_id</strong><br><code>required</code></td>
                      <td>string</td>
                      <td>Request path parameter.</td>
              </tr>
              <tr>
                  <td>info</td>
                  <td>object (Info)<br>Nullable</td>
                  <td>-</td>
              </tr>
              <tr>
                  <td><strong>key</strong><br><code>required</code></td>
                  <td>string (Key)<br>[1 .. 250] characters</td>
                  <td>Notification unique key for the provider.</td>
              </tr>
              <tr>
                  <td><strong>when</strong><br><code>required</code></td>
                  <td>string &lt;date-time&gt; (When)</td>
                  <td>When the notification should be sent to provider.</td>
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
              <td>info</td>
              <td>object (Info)<br>Nullable</td>
              <td>-</td>
            </tr>
            <tr>
              <td>provider</td>
              <td>integer (Provider)</td>
              <td>-</td>
            </tr>
            <tr>
              <td><strong>key</strong><br><code>required</code></td>
              <td>string (Key)<br>[1 .. 250] characters</td>
              <td>Notification unique key for the provider.</td>
            </tr>
            <tr>
              <td><strong>when</strong><br><code>required</code></td>
              <td>string &lt;date-time&gt; (When)</td>
              <td>When the notification should be sent to provider.</td>
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
  "info": {},
  "key": "string",
  "when": "2019-08-24T14:15:22Z"
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
  "info": {},
  "provider": 0,
  "key": "string",
  "when": "2019-08-24T14:15:22Z",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
  ````
</details>

<div style="text-align:right">

[[top section]](#provider_notification_management) [[top page]](#table-of-content) 
</div>

<br>

<!--- provider_notification_read --->
## 5.3 Read Provider Notification<a name="provider_notification_read"></a>
Retrieves information about Provider Notification.

### Request
Concept | Data
-- | --
HTTP method | <code>**GET**</code>
Path | /api/v2/provider/{parent_lookup_provider_id}/notification/{id}/
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
                  <td><strong>parent_lookup_provider_id</strong><br><code>required</code></td>
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
              <td>info</td>
              <td>object (Info)<br>Nullable</td>
              <td>-</td>
            </tr>
            <tr>
              <td>provider</td>
              <td>integer (Provider)</td>
              <td>-</td>
            </tr>
            <tr>
              <td><strong>key</strong><br><code>required</code></td>
              <td>string (Key)<br>[1 .. 250] characters</td>
              <td>Notification unique key for the provider.</td>
            </tr>
            <tr>
              <td><strong>when</strong><br><code>required</code></td>
              <td>string &lt;date-time&gt; (When)</td>
              <td>When the notification should be sent to provider.</td>
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
  "info": {},
  "provider": 0,
  "key": "string",
  "when": "2019-08-24T14:15:22Z",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
```
</details>

<div style="text-align:right">

[[top section]](#provider_notification_management) [[top page]](#table-of-content) 
</div>
<br>

<!--- provider_notification_update --->
## 5.4 Update Provider Notification<a name="provider_notification_update"></a>
API endpoint that updates Provider Notification.

### Request
Concept | Data
-- | --
HTTP method | <code>**PUT**</code>
Path | /api/v2/provider/{parent_lookup_provider_id}/notification/{id}/
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
                  <td><strong>parent_lookup_provider_id</strong><br><code>required</code></td>
                  <td>string </td>
                  <td>Request path parameter.</td>
              </tr>
            <tr>
              <td>info</td>
              <td>object (Info)<br>Nullable</td>
              <td>-</td>
            </tr>
            <tr>
              <td><strong>key</strong><br><code>required</code></td>
              <td>string (Key)<br>[1 .. 250] characters</td>
              <td>Notification unique key for the provider.</td>
            </tr>
            <tr>
              <td><strong>when</strong><br><code>required</code></td>
              <td>string &lt;date-time&gt; (When)</td>
              <td>When the notification should be sent to provider.</td>
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
              <td>info</td>
              <td>object (Info)<br>Nullable</td>
              <td>-</td>
            </tr>
            <tr>
              <td>provider</td>
              <td>integer (Provider)</td>
              <td>-</td>
            </tr>
            <tr>
              <td><strong>key</strong><br><code>required</code></td>
              <td>string (Key)<br>[1 .. 250] characters</td>
              <td>Notification unique key for the provider.</td>
            </tr>
            <tr>
              <td><strong>when</strong><br><code>required</code></td>
              <td>string &lt;date-time&gt; (When)</td>
              <td>When the notification should be sent to provider.</td>
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
  "info": {},
  "key": "string",
  "when": "2019-08-24T14:15:22Z"
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
  "info": {},
  "provider": 0,
  "key": "string",
  "when": "2019-08-24T14:15:22Z",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
```
</details>

<div style="text-align:right">

[[top section]](#provider_notification_management) [[top page]](#table-of-content) 
</div>
<br>

<!--- provider_notification_partial_update --->
## 5.5 Partial Update Provider Notification <a name="provider_notification_partial_update"></a>
API endpoint that updates Provider Notification partial information.

### Request
Concept | Data
-- | --
HTTP method | <code>**PATCH**</code>
Path | /api/v2/provider/{parent_lookup_provider_id}/notification/{id}/
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
                  <td><strong>parent_lookup_provider_id</strong><br><code>required</code></td>
                  <td>string </td>
                  <td>Request path parameter.</td>
              </tr>
            <tr>
              <td>info</td>
              <td>object (Info)<br>Nullable</td>
              <td>-</td>
            </tr>
            <tr>
              <td><strong>key</strong><br><code>required</code></td>
              <td>string (Key)<br>[1 .. 250] characters</td>
              <td>Notification unique key for the provider.</td>
            </tr>
            <tr>
              <td><strong>when</strong><br><code>required</code></td>
              <td>string &lt;date-time&gt; (When)</td>
              <td>When the notification should be sent to provider.</td>
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
              <td>info</td>
              <td>object (Info)<br>Nullable</td>
              <td>-</td>
            </tr>
            <tr>
              <td>provider</td>
              <td>integer (Provider)</td>
              <td>-</td>
            </tr>
            <tr>
              <td><strong>key</strong><br><code>required</code></td>
              <td>string (Key)<br>[1 .. 250] characters</td>
              <td>Notification unique key for the provider.</td>
            </tr>
            <tr>
              <td><strong>when</strong><br><code>required</code></td>
              <td>string &lt;date-time&gt; (When)</td>
              <td>When the notification should be sent to provider.</td>
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
  "info": {},
  "key": "string",
  "when": "2019-08-24T14:15:22Z"
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
  "info": {},
  "provider": 0,
  "key": "string",
  "when": "2019-08-24T14:15:22Z",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
```
</details>

<div style="text-align:right">

[[top section]](#provider_notification_management) [[top page]](#table-of-content) 
</div>
<br>

<!--- provider_notification_delete --->
## 5.6 Delete Provider Notification<a name="provider_notification_delete"></a>
API endpoint for deleting Provider Notification.

### Request
Concept | Data
-- | --
HTTP Method | <code>**DELETE**</code>
Path | /api/v2/provider/{parent_lookup_provider_id}/notification/{id}/
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
              <td><strong>parent_lookup_provider_id</strong><br><code>required</code></td>
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

<div style="text-align:right">

[[top section]](#provider_notification_management) [[top page]](#table-of-content) 
</div>
<br>



# 6. Provider Request Management <a name="provider_request_management"></a>
---
Set of API endpoints that allows activity to be viewed or edited.

  6.1 GET: [List Provider Request](#provider_request_list)<br>
  6.2 GET: [Read Provider Request](#provider_request_read)<br>
  6.3 PUT: [Update Provider Request](#provider_request_update)<br>
  6.4 PATCH: [Partial Update Provider Request](#provider_request_partial_update)<br>
  6.5 POST: [Status Provider Request](#provider_request_status)<br>

<br><br>



<!--- provider_request_list --->
## 6.1 List Provider Request <a name="provider_request_list"></a>
API endpoint for listing Provider Requests.

### Request

Concept | Data
-- | --
HTTP Method | <code>**GET**</code>
Path | /api/v2/provider/{parent_lookup_provider_id}/request/
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
                      <td><strong>parent_lookup_provider_id</strong><br><code>required</code></td>
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
                  <td>integer (ID) </td>
                  <td>-</td>
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
              <td>Array of objects (ProviderVerificationRequestResult)</td>
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
      "request": {
        "id": 0,
        "data": "http://example.com"
      },
      "learner_id": "2df776db-09df-4cb9-a2af-db56cada6cb7",
      "result": 0,
      "status": 0,
      "error_message": "string",
      "code": 0,
      "audit": "http://example.com",
      "audit_data": {}
    }
  ]
}
  ````
</details>



<div style="text-align:right">

[[top section]](#provider_request_management) [[top page]](#table-of-content) 
</div>

<br>


<!--- provider_request_read --->
## 6.2 Read Provider Request<a name="provider_request_read"></a>
Retrieves information about Provider Request.

### Request
Concept | Data
-- | --
HTTP method | <code>**GET**</code>
Path | /api/v2/provider/{parent_lookup_provider_id}/request/{request_id}/
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
                  <td><strong>request_id</strong><br><code>required</code></td>
                  <td>string </td>
                  <td>Request path parameter. Request related to this result.</td>
              </tr>
              <tr>
                  <td><strong>parent_lookup_provider_id</strong><br><code>required</code></td>
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
              <td>request</td>
              <td>object (ProviderVerificationRequest)</td>
              <td>-</td>
            </tr>
            <tr>
              <td>learner_id</td>
              <td>string &lt;uuid&gt; (Learner id)</td>
              <td>-</td>
            </tr>
            <tr>
              <td>result</td>
              <td>number (Result) <br>Nullable.</td>
              <td>Normalized result value.</td>
            </tr>
            <tr>
              <td>status</td>
              <td>integer (Status)<br>Enum: 0, 1, 2, 3, 4, 5, 6, 7</td>
              <td>Status for this result.</td>
            </tr>
            <tr>
              <td>error_message</td>
              <td>string (Error message)<br>non-empty<br>Nullable</td>
              <td>Error message when status is error.</td>
            </tr>
            <tr>
              <td>code</td>
              <td>integer (Code)<br>Enum: 0, 1, 2, 3</td>
              <td>Result code provided after performing the verification process.</td>
            </tr>
            <tr>
              <td>audit</td>
              <td>string &lt;uri&gt; (Audit)</td>
              <td>-</td>
            </tr>
            <tr>
              <td>audit_data</td>
              <td>object (Audit data) <br>Nullable</td>
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
  "request": {
    "id": 0,
    "data": "http://example.com"
  },
  "learner_id": "2df776db-09df-4cb9-a2af-db56cada6cb7",
  "result": 0,
  "status": 0,
  "error_message": "string",
  "code": 0,
  "audit": "http://example.com",
  "audit_data": {}
}
```
</details>

<div style="text-align:right">

[[top section]](#provider_request_management) [[top page]](#table-of-content) 
</div>
<br>

<!--- provider_request_update --->
## 6.3 Update Provider Request<a name="provider_request_update"></a>
API endpoint that updates Provider Request.

### Request
Concept | Data
-- | --
HTTP method | <code>**PUT**</code>
Path | /api/v2/provider/{parent_lookup_provider_id}/request/{request_id}/
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
                  <td><strong>request_id</strong><br><code>required</code></td>
                  <td>string </td>
                  <td>Request path parameter. Request related to this result.</td>
              </tr>
              <tr>
                  <td><strong>parent_lookup_provider_id</strong><br><code>required</code></td>
                  <td>string </td>
                  <td>Request path parameter.</td>
              </tr>
            <tr>
              <td>request</td>
              <td>object (ProviderVerificationRequest)</td>
              <td>-</td>
            </tr>
            <tr>
              <td>result</td>
              <td>number (Result) <br>Nullable.</td>
              <td>Normalized result value.</td>
            </tr>
            <tr>
              <td>status</td>
              <td>integer (Status)<br>Enum: 0, 1, 2, 3, 4, 5, 6, 7</td>
              <td>Status for this result.</td>
            </tr>
            <tr>
              <td>error_message</td>
              <td>string (Error message)<br>non-empty<br>Nullable</td>
              <td>Error message when status is error.</td>
            </tr>
            <tr>
              <td>code</td>
              <td>integer (Code)<br>Enum: 0, 1, 2, 3</td>
              <td>Result code provided after performing the verification process.</td>
            </tr>
            <tr>
              <td>audit_data</td>
              <td>object (Audit data) <br>Nullable</td>
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
              <td>request</td>
              <td>object (ProviderVerificationRequest)</td>
              <td>-</td>
            </tr>
            <tr>
              <td>learner_id</td>
              <td>string &lt;uuid&gt; (Learner id)</td>
              <td>-</td>
            </tr>
            <tr>
              <td>result</td>
              <td>number (Result) <br>Nullable.</td>
              <td>Normalized result value.</td>
            </tr>
            <tr>
              <td>status</td>
              <td>integer (Status)<br>Enum: 0, 1, 2, 3, 4, 5, 6, 7</td>
              <td>Status for this result.</td>
            </tr>
            <tr>
              <td>error_message</td>
              <td>string (Error message)<br>non-empty<br>Nullable</td>
              <td>Error message when status is error.</td>
            </tr>
            <tr>
              <td>code</td>
              <td>integer (Code)<br>Enum: 0, 1, 2, 3</td>
              <td>Result code provided after performing the verification process.</td>
            </tr>
            <tr>
              <td>audit</td>
              <td>string &lt;uri&gt; (Audit)</td>
              <td>-</td>
            </tr>
            <tr>
              <td>audit_data</td>
              <td>object (Audit data) <br>Nullable</td>
              <td>-</td>
            </tr>
        </tbody>
    </table>
  {{</ tab >}}
{{</ tabs >}}

#### Request sample
```json
{
  "request": {},
  "result": 0,
  "status": 0,
  "error_message": "string",
  "code": 0,
  "audit_data": {}
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
  "request": {
    "id": 0,
    "data": "http://example.com"
  },
  "learner_id": "2df776db-09df-4cb9-a2af-db56cada6cb7",
  "result": 0,
  "status": 0,
  "error_message": "string",
  "code": 0,
  "audit": "http://example.com",
  "audit_data": {}
}
```
</details>

<div style="text-align:right">

[[top section]](#provider_request_management) [[top page]](#table-of-content) 
</div>
<br>

<!--- provider_request_partial_update --->
## 6.4 Partial Update Provider Request <a name="provider_request_partial_update"></a>
API endpoint that updates Provider Request partial information.

### Request
Concept | Data
-- | --
HTTP method | <code>**PATCH**</code>
Path | /api/v2/provider/{parent_lookup_provider_id}/request/{request_id}/
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
                  <td><strong>request_id</strong><br><code>required</code></td>
                  <td>string </td>
                  <td>Request path parameter. Request related to this result.</td>
              </tr>
              <tr>
                  <td><strong>parent_lookup_provider_id</strong><br><code>required</code></td>
                  <td>string </td>
                  <td>Request path parameter.</td>
              </tr>
            <tr>
              <td>request</td>
              <td>object (ProviderVerificationRequest)</td>
              <td>-</td>
            </tr>
            <tr>
              <td>result</td>
              <td>number (Result) <br>Nullable.</td>
              <td>Normalized result value.</td>
            </tr>
            <tr>
              <td>status</td>
              <td>integer (Status)<br>Enum: 0, 1, 2, 3, 4, 5, 6, 7</td>
              <td>Status for this result.</td>
            </tr>
            <tr>
              <td>error_message</td>
              <td>string (Error message)<br>non-empty<br>Nullable</td>
              <td>Error message when status is error.</td>
            </tr>
            <tr>
              <td>code</td>
              <td>integer (Code)<br>Enum: 0, 1, 2, 3</td>
              <td>Result code provided after performing the verification process.</td>
            </tr>
            <tr>
              <td>audit_data</td>
              <td>object (Audit data) <br>Nullable</td>
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
              <td>request</td>
              <td>object (ProviderVerificationRequest)</td>
              <td>-</td>
            </tr>
            <tr>
              <td>learner_id</td>
              <td>string &lt;uuid&gt; (Learner id)</td>
              <td>-</td>
            </tr>
            <tr>
              <td>result</td>
              <td>number (Result) <br>Nullable.</td>
              <td>Normalized result value.</td>
            </tr>
            <tr>
              <td>status</td>
              <td>integer (Status)<br>Enum: 0, 1, 2, 3, 4, 5, 6, 7</td>
              <td>Status for this result.</td>
            </tr>
            <tr>
              <td>error_message</td>
              <td>string (Error message)<br>non-empty<br>Nullable</td>
              <td>Error message when status is error.</td>
            </tr>
            <tr>
              <td>code</td>
              <td>integer (Code)<br>Enum: 0, 1, 2, 3</td>
              <td>Result code provided after performing the verification process.</td>
            </tr>
            <tr>
              <td>audit</td>
              <td>string &lt;uri&gt; (Audit)</td>
              <td>-</td>
            </tr>
            <tr>
              <td>audit_data</td>
              <td>object (Audit data) <br>Nullable</td>
              <td>-</td>
            </tr>
        </tbody>
    </table>
  {{</ tab >}}
{{</ tabs >}}

#### Request sample
```json
{
  "request": {},
  "result": 0,
  "status": 0,
  "error_message": "string",
  "code": 0,
  "audit_data": {}
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
  "request": {
    "id": 0,
    "data": "http://example.com"
  },
  "learner_id": "2df776db-09df-4cb9-a2af-db56cada6cb7",
  "result": 0,
  "status": 0,
  "error_message": "string",
  "code": 0,
  "audit": "http://example.com",
  "audit_data": {}
}
```
</details>

<div style="text-align:right">

[[top section]](#provider_request_management) [[top page]](#table-of-content) 
</div>
<br>

<!--- provider_request_status --->
## 6.5 Status Provider Request<a name="provider_request_status"></a>
Change Provider Request status.

### Request
Concept | Data
-- | --
HTTP Method | <code>**POST**</code>
Path | /api/v2/provider/{parent_lookup_provider_id}/request/{request_id}/status/
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
                  <td><strong>request_id</strong><br><code>required</code></td>
                  <td>string </td>
                  <td>Request path parameter. Request related to this result.</td>
              </tr>
              <tr>
                  <td><strong>parent_lookup_provider_id</strong><br><code>required</code></td>
                  <td>string </td>
                  <td>Request path parameter.</td>
              </tr>
            <tr>
              <td>request</td>
              <td>object (ProviderVerificationRequest)</td>
              <td>-</td>
            </tr>
            <tr>
              <td>result</td>
              <td>number (Result) <br>Nullable.</td>
              <td>Normalized result value.</td>
            </tr>
            <tr>
              <td>status</td>
              <td>integer (Status)<br>Enum: 0, 1, 2, 3, 4, 5, 6, 7</td>
              <td>Status for this result.</td>
            </tr>
            <tr>
              <td>error_message</td>
              <td>string (Error message)<br>non-empty<br>Nullable</td>
              <td>Error message when status is error.</td>
            </tr>
            <tr>
              <td>code</td>
              <td>integer (Code)<br>Enum: 0, 1, 2, 3</td>
              <td>Result code provided after performing the verification process.</td>
            </tr>
            <tr>
              <td>audit_data</td>
              <td>object (Audit data) <br>Nullable</td>
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
              <td>request</td>
              <td>object (ProviderVerificationRequest)</td>
              <td>-</td>
            </tr>
            <tr>
              <td>learner_id</td>
              <td>string &lt;uuid&gt; (Learner id)</td>
              <td>-</td>
            </tr>
            <tr>
              <td>result</td>
              <td>number (Result) <br>Nullable.</td>
              <td>Normalized result value.</td>
            </tr>
            <tr>
              <td>status</td>
              <td>integer (Status)<br>Enum: 0, 1, 2, 3, 4, 5, 6, 7</td>
              <td>Status for this result.</td>
            </tr>
            <tr>
              <td>error_message</td>
              <td>string (Error message)<br>non-empty<br>Nullable</td>
              <td>Error message when status is error.</td>
            </tr>
            <tr>
              <td>code</td>
              <td>integer (Code)<br>Enum: 0, 1, 2, 3</td>
              <td>Result code provided after performing the verification process.</td>
            </tr>
            <tr>
              <td>audit</td>
              <td>string &lt;uri&gt; (Audit)</td>
              <td>-</td>
            </tr>
            <tr>
              <td>audit_data</td>
              <td>object (Audit data) <br>Nullable</td>
              <td>-</td>
            </tr>
         </tbody>
        </table>
  {{</ tab >}}
{{</tabs>}}

#### Request sample:
````json
{
  "request": {},
  "result": 0,
  "status": 0,
  "error_message": "string",
  "code": 0,
  "audit_data": {}
}
````
### Responses

#### Response sample: 201
<details>
  <summary>201</summary>

```json
{
  "id": 0,
  "request": {
    "id": 0,
    "data": "http://example.com"
  },
  "learner_id": "2df776db-09df-4cb9-a2af-db56cada6cb7",
  "result": 0,
  "status": 0,
  "error_message": "string",
  "code": 0,
  "audit": "http://example.com",
  "audit_data": {}
}
```
</details>

<div style="text-align:right">

[[top section]](#provider_request_management) [[top page]](#table-of-content) 
</div>
<br>

