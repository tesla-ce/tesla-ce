---
title: "Roles"
weight: 2
draft: false
# search related keywords
keywords: ["authentication","users", "roles"]
---
{{< notice info >}}
  **This page is under construction** <br>
  We're working on it!
{{</ notice >}}


Following table shows current system roles in the TeSLA system:

Role | Area | Description | Assigned by
--- | ----- | ---- | ----------
GLOBAL_ADMIN | Global | Manages and monitors the entire system. <br> Manages institutions. <br> Manages providers. <br> Manages instruments. <br> Required to access url:  api/v2/admin/** | GLOBAL_ADMIN: It can only be assigned by another user with this role. |
ADMIN | Institution | Manages institution settings. <br>Manages institution roles. <br>Required to access url:  api/v2/institution/<institucio>/** | It can be assigned by another ADMIN user, or by a GLOBAL_ADMIN.
SEND | Institution | Manages students with special needs properties. | ADMIN role from same institution.
DATA_MANAGEMENT | Institution | Manages update/delete data linked to GPRD ARCO permissions | ADMIN role from same institution.
IC_MANAGEMENT | Institution| Manages the informed consent of an institution | ADMIN role from same institution.
INSTRUCTOR | Institution | Manages the activities from own instituion | See information and results of students linked to their subjects| This role is not assigned, it is generated from a user's assignments
LEARNER | Institution | See his/her own information as student. | Make records on biometric instruments. | See results of the activities in which she/he has participated. | This role is not assigned, it is generated from a user's assignments
ACADEMIC_MANAGEMENT | Institution | See the results and statistics of a set of subjects. | ADMIN role from same institution.








