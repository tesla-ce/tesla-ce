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

# Table of Content
1. [Provider Management](#provider_management)
2. [Provider Enrolment Management](#provider_enrolment_management)
3. [Provider Notification Management](#provider_notification_management)
4. [Provider Request Management](#provider_request_management)


*****
*****


# 1. Provider Management <a name="provider_management"></a> 
Set of API endpoints that allow Instrument Providers to be viewed or edited.

- [List Providers](#provider_list)
- [Read Provider](#provider_read)


<!--- provider_list --->
## List Providers: GET <a name="provider_list"></a>

API endpoint for listing Instrument Providers.

### Request

Concept | Data
-- | --
HTTP Method | **GET**
Path | /api/v2/provider/
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


<!--- provider_read --->
## Read Provider<a name="provider_read"></a>
Retrieves information about an Instrument Provider.

### Request
Concept | Data
-- | --
HTTP method | **GET**
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





---

# 2. Provider Enrolment Management <a name="provider_enrolment_management"></a> 
Set of API endpoints that allow Provider access enrolment samples.

- GET: [List Provider Enrolment](#provider_enrolment_list)
- POST: [Create Provider Enrolment](#provider_enrolment_create)
- GET: [Read Provider Enrolment](#provider_enrolment_read)
- PUT: [Update Provider Enrolment](#provider_enrolment_update)
- PATCH: [Partial Update Provider Enrolment](#provider_enrolment_partial_update)
- DELETE: [Delete Provider Enrolment](#provider_enrolment_delete)


<!--- provider_enrolment_list --->
## List Provider Enrolment: GET <a name="provider_enrolment_list"></a>

API endpoint for listing Provider Enrolment.

### Request

Concept | Data
-- | --
HTTP Method | **GET**
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



<!--- provider_enrolment_create --->
## Create Provider Enrolment<a name="provider_enrolment_create"></a>

API endpoint for creating a new Institution.

### Request

Concept | Data
-- | --
HTTP Method | **POST**
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
                      <td>-</td>
              </tr>
              <tr>
                      <td><strong>learner_id</strong><br><code>required</code></td>
                      <td>string &lt;uuid&gt; (Learner id)</td>
                      <td>Request path parameter.</td>
              </tr>
              <tr>
                      <td><strong>task_id</strong><br><code>required</code></td>
                      <td>string &lt;uuid&gt; (Task id)</td>
                      <td>Request path parameter.</td>
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

#### Request Sample: POST

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


<!--- provider_enrolment_read --->
## Read Provider Enrolment<a name="provider_enrolment_read"></a>
Retrieves information about Provider access enrolment samples.

### Request
Concept | Data
-- | --
HTTP method | **GET**
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


<!--- provider_enrolment_update --->
## Update Provider Enrolment<a name="provider_enrolment_update"></a>
API endpoint that updates Provider access enrolment samples.

### Request
Concept | Data
-- | --
HTTP method | **PUT**
Path | /api/v2/provider/{parent_lookup_provider_id}/enrolment/{learner__learner_id}/
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

<!--- provider_enrolment_partial_update --->
## Partial Update Provider Enrolment <a name="provider_enrolment_partial_update"></a>
API endpoint that updates Provider access enrolment samples' information.

### Request
Concept | Data
-- | --
HTTP method | **PATCH**
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

<!--- provider_enrolment_delete --->
## Delete Provider Enrolment<a name="provider_enrolment_delete"></a>
API endpoint for deleting Provider access enrolment samples.

### Request
Concept | Data
-- | --
HTTP Method | **DELETE**
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













---
---
---
---
---

# TEMP WIP

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


