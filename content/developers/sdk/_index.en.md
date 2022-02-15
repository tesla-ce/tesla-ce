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

This section will show you main SDKs user cases for calling TeSLA CE API.

Available SDKs:
* https://github.com/tesla-ce/php-client: VLE integration
* https://github.com/tesla-ce/python-provider-sdk: Providers integration
* https://github.com/tesla-ce/python-client: General API methods for generic and admin calls such as system installation, client set up, and so on.



# Table Of Contents
{{< toc >}}

# VLE Integration User Cases
## 1. Course Management
Create/Get/Update a Course.

All 3 user cases using the same endpoint but with its corresponding verb (PUT, GET, PATCH).

{{%tabs %}}
{{% tab "HTTP" %}}
This first tab shows an example of HTML code, but we should use **HTTP** header and calls.

API method:
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
{{% /tab %}}

{{% tab "PHP SDK" %}}
This second tab shows an example of PHP code, but we should use **SKD** header and calls.

```php
print("Hello World!")
```
{{% /tab %}}

{{% tab "Python SDK" %}}
This second tab shows an example of PYTHON code, but we should use **SKD** header and calls.

```python
print("Hello World!")
```
{{% /tab %}}
 
{{% /tabs %}}

## 2. Add User to a Course
User can be an Instructor or a Learner.


{{< tabs >}}
  {{< tab "HTTP" >}}
   This is first tab
  {{</ tab >}}

  {{< tab "SDK" >}}
  this is second tab
  {{</ tab >}}

 
{{</ tabs >}}

## 3. Get a Launcher
What you need for forwarding fro your LMS to TeSLA CE Dashboard, without need of the use of credentials.
Example: an INstructor using Moodle that wants to check TeSLA reports about specific activity in TeSLA Dashboard.
TeSLA CE Dashboard can be used for monitoring status of instruments, informed consent, activities.

Note: TeSLA Dasboard can be access directly by an Intitution role (legal, admin, send), but, 
by default, a user (Instructor o Learner) is not allowed to access directly to TeSLA dashboard, she needs access through the LMS front-end.
However, you can change this behaviour by activating the option "login allowed" of the user profile
 in the Instituion Admin Dashboard. In that case, you will need to assign a new password using the "Change Password" button.

Note: A course should be created first in the LMS front-end (for example Moodle). When the user uses 
the launcher, the system will check and decide if it needs to create the course in the TeSLA system.



{{< tabs >}}
  {{< tab "HTTP" >}}
   This is first tab
  {{</ tab >}}

  {{< tab "SDK" >}}
  this is second tab
  {{</ tab >}}

 
{{</ tabs >}}

## 4. Create/Get/Update an Activity

All 3 user cases using the same endpoint but with its corresponding verb (PUT, GET, PATCH).


{{< tabs >}}
  {{< tab "HTTP" >}}
   This is first tab
  {{</ tab >}}

  {{< tab "SDK" >}}
  this is second tab
  {{</ tab >}}

 
{{</ tabs >}}

## 5. Learner Information


{{< tabs >}}
  {{< tab "HTTP" >}}
   This is first tab
  {{</ tab >}}

  {{< tab "SDK" >}}
  this is second tab
  {{</ tab >}}

 
{{</ tabs >}}

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
  
{{< tabs >}}
  {{< tab "HTTP" >}}
   This is first tab
  {{</ tab >}}

  {{< tab "SDK" >}}
  this is second tab
  {{</ tab >}}

 
{{</ tabs >}}

## 7. Add document to an assessment

SendActivityDocument

{{< tabs >}}
  {{< tab "HTTP" >}}
   This is first tab
  {{</ tab >}}

  {{< tab "SDK" >}}
  this is second tab
  {{</ tab >}}

 
{{</ tabs >}}

## 8. Can Send 

canSend
Notify the system if a verification can be sent: does the course exist in TeSLA sytem? Does the activity exist? Is the instrument activated in the TeSLA Activity?

{{< tabs >}}
  {{< tab "HTTP" >}}
   This is first tab
  {{</ tab >}}

  {{< tab "SDK" >}}
  this is second tab
  {{</ tab >}}

 
{{</ tabs >}}

Nulla non sollicitudin. Morbi sit amet laoreet ipsum, vel pretium mi. Morbi varius, tellus in accumsan blandit, elit ligula eleifend velit, luctus mattis ante nulla condimentum nulla. Etiam vestibulum risus vel arcu elementum eleifend. Cras at dolor eget urna varius faucibus tempus in elit.



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
