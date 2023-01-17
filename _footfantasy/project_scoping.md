---
title: "Project Scoping"
excerpt: "Project scoping"
last_modified_at: 2023-01-09 11:16:00 +0100
toc: true
---
<script src="/assets/js/mermaid.min.js"></script>
# Description
We want to create a football fantasy app.
A football fantasy game consists of choosing players every weeks and going against other players. The winner of the match is decided according to the grades of the player chosen.

# Flow Chart

<div class="mermaid">
flowchart TD
  open_ff[\Open FF website/]
  accept_mail_invitation[\Accept Invitation in email/]
  accept_invitation[\Accept invitation on website/]
  is_authenticated{Is Authenticated?}
  has_account{Has Account?}
  login(Login)
  open_ff --> is_authenticated
  accept_mail_invitation -.-> is_authenticated
  subgraph authentication
  is_authenticated -- no --> has_account
  is_authenticated -. no .-> has_account  
  has_account -- yes --> login
  has_account -- no --> signup
  has_account -. yes .-> login
  has_account -. no .-> signup
  end
  is_authenticated -- yes --> home_page[/Home page/]
  is_authenticated -. yes .-> league_page[/League page/]
  subgraph league_creation
  create_league(Create league)
  create_league --> league_page
  league_page --> invite_others(Invite other people)
  accept_invitation --> is_league_full
  invite_others --> is_league_full{Is the league full?}
  is_league_full -- no --> invite_others
  end
  signup --> home_page
  login --> home_page
  home_page --> league_creation
  subgraph transfers
    transfer_round(Biding on players)
    transfer_round --> teams_are_completed{Are teams completed?}
    teams_are_completed -- no --> transfer_round
  end
  is_league_full -- yes --> transfers
  subgraph match
  player_selection(Choose your players)
  play_match(Play Match)
  player_selection --> play_match(Play Match)
  play_match --> any_game_left{Are there games left ?}
  any_game_left -- yes --> player_selection
  end
  teams_are_completed -- yes --> match
  any_game_left -- no --> league_finished(League is finished)
</div>

### Account Creation Flow

Simple signup page.
We should ask for:
- email
- password
- repeat_password
- username
- dob

Should enforce some password rules.
Should generate default usernames
Should generate authentication token once signed up
Should create authentication and account entry in database.

The flow would look like this:
<div class="mermaid">
sequenceDiagram
  participant SP as Signup Page
  participant AuthC as AuthenticationsController
  participant Auth as Authentication
  participant A as Account
  SP->>AuthC: POST /authentication/create
  AuthC->>+Auth: New auth
  AuthC->>Auth: validate params
  AuthC->>Auth: save!
  Auth->>A: Create account with form params using `accepts_nested_attributes_for`
  AuthC->>Auth: generate authentication token
  Auth->>-AuthC: Authentication Token
  AuthC->>SP: Return JSON with authentication token
</div>

The class diagram would look like this:
<div class="mermaid">
classDiagram
  class Account~ActiveRecord~{
    +String username
    +Image avatar
    +Date dob
  }
  class Authentication~ActiveRecord~{
    +Email email
    +String password
    -encode() string
    -decode() string
    -generate_token() string
  }
  Account "1" -- "1" Authentication
</div>

### Login Flow

Simple login page with email and password.

Should generate authentication token
It should be the page to be redirected to if not authenticated

<div class="mermaid">
sequenceDiagram
  participant LP as Login Page
  participant Auth as Authentication
  LP->>Auth: POST /authentication/create 
  Auth->>LP: Authentication Token
</div>

### League Creation

Create a league

### League Invitations
### Transfers
### League Start
### Fixtures
### League End

The goal of this type of app is for users to create account
