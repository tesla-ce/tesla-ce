---
title: "SDK"
weight: 6
draft: false
# search related keywords
keywords: ["sdk"]
---
{{< notice info >}}
  **This page is under construction** <br>
  We're working on it!
{{</ notice >}}

The Open Source TeSLA CE SDKs for supporting TeSLA CE REST API. 

Available SDKs:
* [PHP Client](https://github.com/tesla-ce/php-client): VLE integration
* [Python Provider SDK](https://github.com/tesla-ce/python-provider-sdk): Providers integration
* [Pyhton Client](https://github.com/tesla-ce/python-client): General API methods for generic and admin calls such as system installation, client set up, and so on.



# Table Of Contents
{{< toc >}}


{{< notice warning >}}
Before using any of the TeSLA CE SDKs, please, note that a client must exist.
{{</ notice >}}

{{% tabs %}}
{{% tab "PHP"%}}
Client creation (php):
````php
$this->client = new Client($role, $secret, $base_url, !$debug, $tesla_cache);
````
{{% /tab%}}
{{% tab "Python"%}}
Client creation (Python):
Python client:
```python
self._client = Client.create_instance(config['VAULT_URL'], config['VAULT_ROLE_ID'], config['VAULT_SECRET_ID'], config['VAULT_SSL_VERIFY'])
```
{{% /tab%}}
{{% /tabs %}}

# VLE Integration User Cases
## 1. Course Management
SDK for Course Management including 3 user cases: Create/Get/Update a Course.

{{%tabs %}}
{{% tab "HTTP" %}}
All the three User Cases (Create, Get, and Update) using the same API endpoint but with its corresponding verb (PUT, GET, and PATCH).

Check the [API VLE Course Management documentation](/developers/api/vle/#vle_course_management) for methods details.
{{% /tab %}}
{{% tab "PHP SDK" %}}
<!-- # TODO: Missing all source code documentation links -->
Adding a Course:
```php
$this->client->getCourse()->create(...);
 ```
Get Course information:
```php
$this->client->getCourse()->get(...);
 ```
Get Course information by VLE Course ID:
```php
$this->client->getCourse()->getByVleCourseId(...);
 ```
Updating an existing Course:
```php
$this->client->getCourse()->update(...);
```
{{% /tab %}}
{{% tab "Python SDK" %}}
Adding a Course ([source code documentation](https://www.tesla-ce.eu/python-client/0.0.1/client/#tesla_ce_client.vle.course.client.VleCourseClient.create)): 
```python
self._client.vle.course.create(...)
```
Get Course information ([source code documentation](https://www.tesla-ce.eu/python-client/0.0.1/client/#tesla_ce_client.vle.course.client.VleCourseClient.list)):
```python
self._client.vle.course.list(...)
 ```
Get Course information by VLE Course ID ([source code documentation](https://www.tesla-ce.eu/python-client/0.0.1/client/#tesla_ce_client.vle.course.client.VleCourseClient.find_by_vle_id))::
```python
self._client.vle.course.find_by_vle_id(...)
 ```
Updating an existing Course: *TBD*
<!-- # TODO: missing updating existing course method in python-client -->
<!-- # TODO: missing UPDATE call in python-client documentation -->
```python
# Not implemented
self._client.vle.course.update(...)
```
{{% /tab %}}
{{% /tabs %}}
<br>

## 2. Add User to a Course
SDK for adding User to an existing Course.

Note that the User can be an Instructor or a Learner.

{{%tabs %}}
{{% tab "HTTP" %}}
The API level differentiate between Instructor and Learner users:
- Adding an Instructor to a Course: Check the [API VLE Course Instructor documentation](/developers/api/vle/#vle_course_instructor_create)
- Adding a Learner to a Course: Check the [API VLE Course Learner documentation](/developers/api/vle/#vle_course_learner_create)
{{% /tab %}}
{{% tab "PHP SDK" %}}
<!-- # TODO: Missing all source code documentation links -->
Adding Instructor to a Course:
```php
$this->client->getCourse()->addInstructor(...);
 ```
Adding Learner to a Course
```php
$this->client->getCourse()->addLearner(...);
 ```
{{% /tab %}}
{{% tab "Python SDK" %}}
<!-- # TODO: missing adding instructor to existing course method in python-client -->
Adding Instructors to a Course:
```python
# Not implemented
self._client.vle.course.add_instructor(...)
```
<!-- # TODO: missing adding learner to existing course method in python-client -->
Adding Learner to a Course:
```python
# Not implemented
self._client.vle.course.add_learner(...)
 ```

{{% /tab %}}
{{% /tabs %}}
<br>

## 3. Get a Launcher
What you need for forwarding from your LMS to TeSLA CE Dashboard, without need of the use of credentials.
TeSLA CE Dashboard can be used for monitoring status of instruments, informed consent, activities.
Example: an Instructor using Moodle that wants to check TeSLA reports about specific activity in TeSLA Dashboard.

Note: TeSLA Dashboard can be access directly by an Institution role (legal, admin, send), but, 
by default, a user (either Instructor or Learner) is not allowed to access directly to TeSLA dashboard, 
she needs access through the LMS front-end.
Please, note that you can change this behaviour by activating the option "login allowed" of the user profile
 in the Institution Admin Dashboard. In that case, you will need to assign a new password using the "Change Password" button.

Note: A course should be created first in the LMS front-end (for example Moodle). When the user uses 
the launcher, the system will check and decide if it needs to create the course in the TeSLA system.



{{%tabs %}}
{{% tab "HTTP" %}}

Check the [API VLE Launcher documentation](/developers/api/vle/#vle_launcher) for methods details.

{{% /tab %}}
{{% tab "PHP SDK" %}}
```php
$this->client->getLauncher()->create(...);
 ```
{{% /tab %}}
{{% tab "Python SDK" %}}
Get launcher information ([source code documentation](https://www.tesla-ce.eu/python-client/0.0.1/client/#tesla_ce_client.vle.client.VleClient.get_launcher))::

```python
self._client.get_launcher(...)
```
{{% /tab %}}
{{% /tabs %}}
<br>

## 4. Create/Get/Update an Activity

SDK for Activity Management including 3 user cases: Create/Get/Update an Activity.


{{%tabs %}}
{{% tab "HTTP" %}}
All the three User Cases (Create, Get, and Update) using the same API endpoint but with its corresponding verb (PUT, GET, and PATCH).

Check the [API VLE Activity Management documentation](/developers/api/vle/#vle_course_activity_management) for methods details.
{{% /tab %}}
{{% tab "PHP SDK" %}}
Adding an Activity:
```php
$this->client->getActivity()->create(...);
 ```
Get Activity information:
```php
$this->client->getActivity()->get(...);
 ```
Get Activity information by Activity ID and Activity Type:
```php
$this->client->getActivity()->getByVleActivityIdAndType(...);
 ```
Updating an existing Activity:
```php
$this->client->getActivity()->update(...);
```

{{% /tab %}}
{{% tab "Python SDK" %}}
Adding an Activity ([source code documentation](https://www.tesla-ce.eu/python-client/0.0.1/client/#tesla_ce_client.vle.course.activity.client.VleCourseActivityClient.create)):
```python
self._client.vle.course.activity.create(...)
```
Get Activity information ([source code documentation](https://www.tesla-ce.eu/python-client/0.0.1/client/#tesla_ce_client.vle.course.activity.client.VleCourseActivityClient.get)):
```python
self._client.vle.course.activity.get(...)
 ```
Get Activity information by Activity ID ([source code documentation](https://www.tesla-ce.eu/python-client/0.0.1/client/#tesla_ce_client.vle.course.activity.client.VleCourseActivityClient.find_by_vle_id)):
```python
self._client.vle.course.activity.find_by_vle_id(...)
 ```
Updating an existing Activity ([source code documentation](https://www.tesla-ce.eu/python-client/0.0.1/client/#tesla_ce_client.vle.course.activity.client.VleCourseActivityClient.update)):
```python
self._client.vle.course.activity.update(...)
```
{{% /tab %}}
{{% /tabs %}}
<br>

## 5. Learner Information


{{%tabs %}}
{{% tab "HTTP" %}}

Check the [API VLE Course Learner Management documentation](/developers/api/vle/#vle_course_learner_management) for methods details.

{{% /tab %}}
{{% tab "PHP SDK" %}}
Adding a Learner:
```php
$this->client->getLearner()->create(...);
 ```
Get Learner information:
```php
// Not implemented
$this->client->getLearner()->get(...);
 ```
Get Learner information by UID:
```php
$this->client->getLearner()->getByUid(...);
 ```
Updating an existing Learner:
```php
// Not implemented
$this->client->getLearner()->update(...);
```

{{% /tab %}}
{{% tab "Python SDK" %}}
Adding a Learner:
```python
# Not implemented
self._client.vle.course.learner.create(...)
```
Get Learner information ([source code documentation](https://www.tesla-ce.eu/python-client/0.0.1/client/#tesla_ce_client.vle.course.activity.client.VleCourseActivityClient.get)):
```python
self._client.vle.course.learner.get(...)
 ```
Get Learner information by UID ([source code documentation](https://www.tesla-ce.eu/python-client/0.0.1/client/#tesla_ce_client.vle.course.learner.client.VleCourseLearnerClient.find_by_uid)):
```python
self._client.vle.course.learner.find_by_uid(...)
 ```
Get Learner information by mail ([source code documentation](https://www.tesla-ce.eu/python-client/0.0.1/client/#tesla_ce_client.vle.course.learner.client.VleCourseLearnerClient.find_by_mail)):
```python
self._client.vle.course.learner.find_by_mail(...)
 ```

Updating an existing learner:
```python
# Not implemented
self._client.vle.course.learner.update(...)
```
{{% /tab %}}
{{% /tabs %}}
<br>

<!--- ## 6. Create an Assessment --->
## 6. Assessment Data

In order to apply for a TeSLA CE Assessment, the system needs to send different type of data from the learner to the system.

We can differentiate two main types of send data processes: the enrolment data and the verification data.

The enrolment data is done once (unless the Institution decides it needs to be done more than once, such, for instance, 
once a year), and it's done in the TeSLA CE dashboard. It implies the capturing of sample data in order to later verify that 
the learner applying for an assessment is, in fact, the right and allowed learner to do it.

The verification data process, instead, needs to be done every time that the learner applies for an assessment.
Inside this verification data process we can differentiate between verification done *during* the assessment (while 
the learner is performing the assessment), versus the verification done *after* the assessment (once the learner has delivered 
task of the assessment).

The verification done *during* the assessment implies the capturing of several data (depending on the activated instruments 
for that specific activity) in order to verify that person typing, or sending, or recording the assessment is, actually, 
the allowed learner. An example of this assessment data could be face pictures for face recognition, or keystroke recording for 
keystroke dynamic recognition.

On the other hand, for the verification done *after* the assessment, the system analyzes the data sent by the learner (the 
deliverable item of the assessment, such a document) and compares it with other delivered items in order to detect if the content is 
copied by an other source or learner. As an example, the plagiarism detection tool uses this process in order to compare a 
delivered document with all the other delivered documents.

### Create an Assessment <!-- create_an_assessment -->
Since an assessment can be performed over several days, every different day will need a dedicated assessment 
for letting the system know that all verification data sent during the assessment is related to the same assessment 
and to the same learner. In order to achieve that target, the system returns a dynamic URL to be inserted in the LMS.

Moreover, when using this method, the system will take care of the following 3 possible scenarios:

* Enrolment process not done: system forwards the Learner to the TeSLA CE Dashboard for making the enrolment.
* Informed Consent is not accepted/signed: the system forward the Learner to the informed consent page in the TeSLA CE Dashboard.
* Otherwise (everything correct): the system returns a javascript (the URL connection) that should be inserted  
in the LMS for starting capturing data dynamically.
  
{{%tabs %}}
{{% tab "HTTP" %}}
Check the [API VLE Assessment documentation](/developers/api/vle/#vle_assessment) for methods details.

{{% /tab %}}
{{% tab "PHP SDK" %}}
Creating an assessment:
```php
$this->client->getAssessment()->create(...);
 ```
Close an assessment:
```php
$this->client->getAssessment()->close(...);
 ```

{{% /tab %}}
{{% tab "Python SDK" %}}

Create an assessment
```python
# Not implemented
self._client.vle.course.activity.assessment.create(...)
```

Close an assessment
```python
# Not implemented
self._client.vle.course.activity.assessment.close(...)
```

{{% /tab %}}
{{% /tabs %}}
<br>

### Verification Data sending during the Assessment 
As mentioned in previous section, all data sent during an assessment needs to be related to an assessment session, i.e. 
needs to use the dynamic URL created in the "Create an Assessment" User Case.
<br>

### Verification Data sending after the Assessment
<!-- ## 7. Assessment -->
For the verification data sending after the assessment, the data is not related to a session, but to a learner and activity. 
That's the reason why the system needs to verify if the verification data can be sent, i.e. validate if the Course 
exist in TeSLA system, if the Activity exist, and if the instrument is activated for that particular TeSLA Activity.

So, the system needs to create the attachment stored in the LMS (the deliverable sent by the Learner) and also needs to 
verify if the data can be sent.

TODO: add document to an assessment
<!-- 666 Roger? -->

{{%tabs %}}
{{% tab "HTTP" %}}
Check the [API VLE Course Activity Attachment Management](/developers/api/vle/#vle_course_activity_attachment_management) for methods details.

{{% /tab %}}
{{% tab "PHP SDK" %}}
Creating an attachment:
```php
$this->client->getVerification()->sendActivityDocument(...);
 ```

Can send:
```php
$this->client->getVerification()->canSend(...);
 ```

{{% /tab %}}
{{% tab "Python SDK" %}}
```python
# Not implemented
```
{{% /tab %}}
{{% /tabs %}}
<br>




