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
    -encode() string
    -decode() string
    -generate_token() string
  }
</div>