---
title: "Project Guidelines"
excerpt: "Project guidelines"
last_modified_at: 2023-01-09 14:04:00 +0100
toc: true
---

## Commit conventions

We should use conventional commits
Conventions can be found [here](https://www.freecodecamp.org/news/how-to-write-better-git-commit-messages/)

```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

### Types of commits

- feat – a new feature is introduced with the changes
- fix – a bug fix has occurred
- chore – changes that do not relate to a fix or feature and don't modify src or test files (for example updating dependencies)
- refactor – refactored code that neither fixes a bug nor adds a feature
- docs – updates to documentation such as a the README or other markdown files
- style – changes that do not affect the meaning of the code, likely related to code formatting such as white-space, missing semi-colons, and so on.
- test – including new or correcting previous tests
- perf – performance improvements
- ci – continuous integration related
- build – changes that affect the build system or external dependencies
- revert – reverts a previous commit

We should enforce these commit message format

### Tools

https://commitizen.github.io/cz-cli/

## What should we monitor

### Our endpoints

We should monitor time it took to answer a query
https://blog.appoptics.com/monitoring-rails-get-hidden-metrics-rails-app/

## Linting

### Ruby

### Javascript

## Static code analyser

I am using rubocop since it is the gem I am most confortable with as static code analyzer
