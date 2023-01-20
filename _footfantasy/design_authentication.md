---
title: "Authentication"
excerpt: "Authentication"
last_modified_at: 2023-01-17 23:22:00 +0100
toc: true
---
<script src="/assets/js/mermaid.min.js"></script>

<div class="mermaid">
classDiagram
  class Authentication~ActiveRecord~{
    +Email email
    +String password
    +generate_session() string
  }
</div>

This model should have these capabilities:
- validate the email/password
- encrypt password
- store email and password
- generate authentication via cookie

## Email

We will use the [valid_email2](https://github.com/micke/valid_email2) gem for email validation (regex + domain).

## Password

### Password rules

- Passwords will contain at least 6 characters in length
- Passwords will contain at least 1 upper and 1 lower case letter
- Passwords will contain at least 1 number
- Passwords will contain at least given special characters 

Regex: `/^.*(?=.{6,})(?=.*[a-zA-Z])(?=.*\d)(?=.*[!&$%&? "]).*$/`

> We decided __not__ to add an additional confirmation password.
First thought, its one more field in the form and it can create frustration to log in. 
> Here is a [case study](https://www.zuko.io/blog/should-you-use-confirm-password-on-your-forms-and-websites-case-study) that proves it.

### Encryption

Password should be encrypted.
Luckily ActiveRecords has a tool for that: [https://edgeguides.rubyonrails.org/active_record_encryption.html]
> We can also look at [this](https://api.rubyonrails.org/v6.0.3.2/classes/ActiveSupport/MessageEncryptor.html)

## Generate Session

We should generate a session.
> According to [this article](https://blog.logrocket.com/jwt-authentication-best-practices/#whyyoushouldnt) __it should not be JWT__
A session cookie should be given back to the client.
A description of how session work in rails can be found [here](https://guides.rubyonrails.org/action_controller_overview.html#session) and [here](https://guides.rubyonrails.org/security.html#what-are-sessions-questionmark)