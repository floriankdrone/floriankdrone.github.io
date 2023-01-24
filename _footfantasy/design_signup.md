---
title: "Signup"
excerpt: "Signup"
last_modified_at: 2023-01-24 23:22:00 +0100
toc: true
---
<script src="/assets/js/mermaid.min.js"></script>

## Models used

- Authentication
- Account

## Flow

- User open signup page
- User fills form and submit
- Form sends post request to account controller
- Accounts controller validates type
- Calls account model create function
- account model will create authentication record [email, password]
- Validate email page
- email validation
- click on email validation link
- validate email
