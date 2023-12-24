---
title: Useful git config settings
description: 
slug: 2023/05/git-config-starter
date: 2023-05-15 00:00:00+0000
image: img_git-config-featured-4001369487.png
math: 
license: 
hidden: false
comments: true
categories:
  -
tags:
  - git
---

This is a summary of useful git config commands.  Git settings exist in a hierachy, for Windows the default locations are:

- System wide - %programfiles%\Git\etc\gitconfig
- Global - %userprofile%\.gitconfig
- Local to the repository - .git/config

## Common global properties

These ones are recommended to be set after Git has been installed:

- ```git config --global user.name "your name"```
- ```git config --global user.email you@example.com```

### Overriding properties

Settings lower in the hierachy override, so for example, if you need to use a different user name and email for a particular repository:

- ```git config user.name "your name"```
- ```git config user.email you@example.com```

Run this in the git repository you wish to modify.  Local is implied if another scope such as ```--global``` is not specified.

## Listing settings

- List global settings: ```git config --global --list```
- List **only** local settings:  ```git config --local --list```
- Show where settings apply from: ```git config --list --show-origin```

## Useful settings

- ```git config --global init.defaultbranch main``` will set the default branch to any new repository to 'main'
- ```git config --global user.signingkey <your key>``` allows you to set your GPG key for signing commits
- ```git config --global credential.msauthflow system``` will set the git credential manager to use your system default browser (otherwise it can use IE)

## Removing settings

This is done using ```--unset``` or ```--unset-all``` if you want to remove all settings with a particular property, e.g.:

- ```git config --global --unset user.signingkey```

An example of removing a local config setting with a specific value (user name: "Mr X"):

- ```git config --unset user.name "Mr X"```

## Git Credential Manager

If you're using Git for Windows, you automatically have [git credential manager](https://github.com/git-ecosystem/git-credential-manager) installed so you don't have to continuously authenticate.  

This adds a new global setting ```credential.helper=manager```
