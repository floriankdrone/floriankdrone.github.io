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
  open_ff(Open FF website)
  accept_mail_invitation(Accept Invitation in email)
  accept_invitation(Accept invitation on website)
  subgraph account_creation
  signup(Create account)
  end
  open_ff --> account_creation
  accept_mail_invitation --> account_creation
  subgraph league_creation
  create_league(Create league)
  create_league --> invite_others(Invite other people)
  accept_invitation --> is_league_full
  invite_others --> is_league_full{Is the league full?}
  is_league_full -- no --> invite_others
  end
  account_creation --> league_creation
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

### Account Creation
### League Creation
### League Invitations
### Transfers
### League Start
### Fixtures
### League End

The goal of this type of app is for users to create account
