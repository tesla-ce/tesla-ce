---
title: "VLE Integration"
weight: 2
draft: false
# search related keywords
keywords: ["vle","environment"]
---
{{< notice info >}}
  **This page is under construction** <br>
  We're working on it!
{{</ notice >}}

<!--- COMMENT START
# What is VLE?
VLE from Virtual Learning Environment.

Moodle, Kanbas, Blackboard.... Currently there is only plugin for Moodle.

How to create course in Tesla -> When you create a course in VLE, it has to be created in Tesla.

Where users and instructors interact.

Everything that happens in VLE has to be sent to Tesla system.


Between Tesla and your VLE there is the SDK. Currently there are SDKs for Python and for <code>kenbeth???</code>.
The SDK acts as a library for helping on call from VLE to Tesla and <code>viceversa?</code>
SDK translate the requirement from VLE to an API endpoint.

Endpoints:
The Moodle plugin can create a Course, an activity, instructors and learners in Tesla.

<br>

# Configuration
---
What we need to integrate a VLE: which data you need

Tesla: if you want to activate and use Tesla by default.
Role
Secret
API URL
Token expiration
Debug mode: allows more error and information messages at interface leve.
Learner create: Moodle can send in automated way Learner information to Tesla, or not.
Instructor create: 
Sticky position.

--- add configuration dashboard screenshot
![image example](img-1.jpg "image")

Create script to configure data or allow VLE to make it.

Steps:
1. Set up VLE: get Moodle configuration (authentication: send role and secret to API, and the returns a set of data with configuration and tokens in order to allow you to communicate with the API )
You will need the token for every query to API, since this is part of the authentication process.
2. Depending on configuration VLE will be able to create course/learners or not. In case VLE is not allowed to created course/learners, those would need to be created from Instituion Dashboard???

<br>

# API Endpoints
---

## Admin user and Instructors:
- Create and update a Course.
- Create, update, configure, report and Activity

Learner user: The Learner user has no direct action with this module, beyond activating/deactivating and moving the position of the floating menu (sticky)

## ONline/OFFline data

<br><br><br><br>

COMMENT END --->