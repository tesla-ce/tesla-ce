---
title: "Authentication"
weight: 3
draft: false
# search related keywords
keywords: ["authentication","users", "roles"]
---

{{< notice info >}}
  **This page is under construction** <br>
  We're working on it!
{{</ notice >}}


- Only special users can log in with credentials. Most of the users are logged in using external systems, such as LTI. 
- Modules use Vault AppRole authentication system, obtaining configuration values and details required by each module.
- It is possible to create one-time credentials, which are referred as launcher tokens. 
- All requests to API must be authenticated using a JWT token.

<br><br>
Note that:
- Vault AppRole authentication system uses a non expiring credentials. It is used at VLE level.
- Launcher tokens uses a single use credentials. It is used at learner/instructor level.
