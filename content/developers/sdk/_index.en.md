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
Get Course information:
<!-- # TODO: missing GET call in python-client documentation --> 
```python
self._client.vle.course.get(...)
 ```
Get Course information by VLE Course ID ([source code documentation](https://www.tesla-ce.eu/python-client/0.0.1/client/#tesla_ce_client.vle.course.client.VleCourseClient.find_by_vle_id))::
```python
self._client.vle.course.find_by_vle_id(...)
 ```
Updating an existing Course: *TBD*
<!-- # TODO: missing updating existing course method in python-client -->
<!-- # TODO: missing UPDATE call in python-client documentation -->
```python
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
<!-- 666: is that correct? --> 
{{% /tab %}}
{{% tab "PHP SDK" %}}
<!-- # TODO: Missing all source code documentation links -->
Adding Instructor to a Course:
<!-- 666 find right source code sample -->
```php
echo "Section under construction";
$this->client->getCourse()->addInstructor(...);
 ```
Adding Learner to a Course
<!-- 666 find right source code sample -->
```php
echo "Section under construction";
$this->client->getCourse()->addLearner(...);
 ```
{{% /tab %}}
{{% tab "Python SDK" %}}
Adding Instructors to a Course ([source code documentation](https://www.tesla-ce.eu/python-client/0.0.1/client/#tesla_ce_client.vle.course.client.VleCourseClient.create)): 
<!-- 666 find documentation link -->
<!-- 666 find right source code sample -->
```python
print("Section under construction")
self._client.vle.course.create(...)
```
Adding Learner to a Course:
<!-- 666 find documentation link -->
<!-- 666 find right source code sample -->
```python
print("Section under construction")
self._client.vle.course.get(...)
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
The API level differentiate between Instructor and Learner users:
<!-- 666: API endpoint? --> 
{{% /tab %}}
{{% tab "PHP SDK" %}}
<!-- # 666: Documentation links? -->
<!-- # 666: source code? -->
```php
echo "Section under construction";
$this->client->getCourse()->addInstructor(...);
 ```

{{% /tab %}}
{{% tab "Python SDK" %}}
<!-- # 666: Documentation links? -->
<!-- # 666: source code? -->
```python
print("Section under construction")
self._client.vle.course.create(...)
```
{{% /tab %}}
{{% /tabs %}}
<br>

## 4. Create/Get/Update an Activity

All 3 user cases using the same endpoint but with its corresponding verb (PUT, GET, PATCH).


{{%tabs %}}
{{% tab "HTTP" %}}
The API level differentiate between Instructor and Learner users:
<!-- 666: API endpoint? --> 
{{% /tab %}}
{{% tab "PHP SDK" %}}
<!-- # 666: Documentation links? -->
<!-- # 666: source code? -->
```php
echo "Section under construction";
$this->client->getCourse()->addInstructor(...);
 ```

{{% /tab %}}
{{% tab "Python SDK" %}}
<!-- # 666: Documentation links? -->
<!-- # 666: source code? -->
```python
print("Section under construction")
self._client.vle.course.create(...)
```
{{% /tab %}}
{{% /tabs %}}
<br>

## 5. Learner Information


{{%tabs %}}
{{% tab "HTTP" %}}
The API level differentiate between Instructor and Learner users:
<!-- 666: API endpoint? --> 
{{% /tab %}}
{{% tab "PHP SDK" %}}
<!-- # 666: Documentation links? -->
<!-- # 666: source code? -->
```php
echo "Section under construction";
$this->client->getCourse()->addInstructor(...);
 ```

{{% /tab %}}
{{% tab "Python SDK" %}}
<!-- # 666: Documentation links? -->
<!-- # 666: source code? -->
```python
print("Section under construction")
self._client.vle.course.create(...)
```
{{% /tab %}}
{{% /tabs %}}
<br>

## 6. Create an Assessment

There are two types of send data processes: the enrolment data and the verification data.

The enrolment data is done once (unless the Institution decides it needs to be done more than once, such, for instance, once a year),
 and it's done in the TeSLA CE dashboard.

The verification data process is done while the learner is making the assessment, and since the 
assessment can be done over several days, every day will have a dedicated assessment for 
letting the system know that all data sent during same assessment is related.

This user case takes care of all the following scenarios:
* Enrolment not done: system forwards the learner to dashboard for making the enrolment.
* Informed Consent is not accepted/signed: the system forward the learner to the informed consent in the dashboard.
* Otherwise (everything correct): the system returns a javascript (the URL connection) for inserting 
in the LMS for starting capturing data dinamically.
  
{{%tabs %}}
{{% tab "HTTP" %}}
The API level differentiate between Instructor and Learner users:
<!-- 666: API endpoint? --> 
{{% /tab %}}
{{% tab "PHP SDK" %}}
<!-- # 666: Documentation links? -->
<!-- # 666: source code? -->
```php
echo "Section under construction";
$this->client->getCourse()->addInstructor(...);
 ```

{{% /tab %}}
{{% tab "Python SDK" %}}
<!-- # 666: Documentation links? -->
<!-- # 666: source code? -->
```python
print("Section under construction")
self._client.vle.course.create(...)
```
{{% /tab %}}
{{% /tabs %}}
<br>

## 7. Add document to an assessment

SendActivityDocument

{{%tabs %}}
{{% tab "HTTP" %}}
The API level differentiate between Instructor and Learner users:
<!-- 666: API endpoint? --> 
{{% /tab %}}
{{% tab "PHP SDK" %}}
<!-- # 666: Documentation links? -->
<!-- # 666: source code? -->
```php
echo "Section under construction";
$this->client->getCourse()->addInstructor(...);
 ```

{{% /tab %}}
{{% tab "Python SDK" %}}
<!-- # 666: Documentation links? -->
<!-- # 666: source code? -->
```python
print("Section under construction")
self._client.vle.course.create(...)
```
{{% /tab %}}
{{% /tabs %}}
<br>

## 8. Can Send 

canSend
Notify the system if a verification can be sent: does the course exist in TeSLA sytem? Does the activity exist? Is the instrument activated in the TeSLA Activity?

{{%tabs %}}
{{% tab "HTTP" %}}
The API level differentiate between Instructor and Learner users:
<!-- 666: API endpoint? --> 
{{% /tab %}}
{{% tab "PHP SDK" %}}
<!-- # 666: Documentation links? -->
<!-- # 666: source code? -->
```php
echo "Section under construction";
$this->client->getCourse()->addInstructor(...);
 ```

{{% /tab %}}
{{% tab "Python SDK" %}}
<!-- # 666: Documentation links? -->
<!-- # 666: source code? -->
```python
print("Section under construction")
self._client.vle.course.create(...)
```
{{% /tab %}}
{{% /tabs %}}
<br>




******

*******

## ***************

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
