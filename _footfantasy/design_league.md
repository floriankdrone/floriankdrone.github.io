---
title: "League"
excerpt: "League"
last_modified_at: 2023-01-30 23:22:00 +0100
toc: true
---

<script src="/assets/js/mermaid.min.js"></script>

## Description

The league reprensents a group of user's playing against each other with the same schedule.

<div class="mermaid">
classDiagram
  class LeagueStatuses {
    <<enumeration>>
    CREATED
    TRANSFER
    ONGOING
    FINISHED
  }
  class ParticipationStatuses {
    <<enumeration>>
    INVITED
    ACCEPTED
    DECLINED
  }
  class ParticipationRoles{
    <<enumeration>>
    OWNER
    MEMBER
  }
  class League~ActiveRecord~{
    +String name
    +Number size
    +LeagueStatuses status
  }
  class LeagueParticipation~ActiveRecord~{
    +ParticipationStatuses status
    +ParticipationRoles role
    +String email
    +Number league_id
    +Number account_id
  }
League --* LeagueParticipation
</div>
