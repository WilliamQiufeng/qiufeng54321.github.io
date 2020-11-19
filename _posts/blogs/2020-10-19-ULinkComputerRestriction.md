---
layout: post
title: "ULink Computer Restriction"
date: 2019-3-10
excerpt: "some studies"
tags: [ulink]
comments: true
---

# ULink Computer Restriction

This is some studies about the restriction put among students' computer uses.  

## Behavior

By installing Application `FileWave`, a user named `ULink Admin` / `ulinkadmin` appears (This is hidden but can be seen by a set of procedures); two profiles named `FileWave MDM Configuration`  and `Restrictions & Preferences ...` will be installed on the computer.

### Restrictions

In `System Preferences`, `Profiles` and `Sharing` panel became disabled. `App Store` becomes completely unavailable and some apps are restricted (Can be opened by clicking `Allow Once`).
## Installation

Just open `FileWaveClient_13.3.1-mdm.ulinkedu.com-15-Jul-2020` and follow instructions

## Uninstallation

### Some common actions

`Unlock`: Sometimes a lock icon appears and is needed to be unlocked by clicking on the icon and inputting the password of the current user.

### Procedure

+ Open `Finder`. Search for `FileWave` and delete stuff
+ Enable root user:
  + Step 1
    + Method 1 (May be blocked too):
      + Open `System Preferences`
      + Go to `Users & Groups`
      + `Unlock`
      + Click `Login Options`
      + Click `Join` next to `Network Account Server`
    + Method 2:
      + Open `Terminal` (`Command + Space` and type `Terminal`)
      + Do `open -a "Directory Utility"`
    + `Unlock`
  + Optional Step (This might cause some minor problems, not sure yet so don't do it if you don't want to):
    + Go to `Directory Editor`
    + Search for `ulink`
    + You may see the name `Ulink Admin` or `ulinkadmin`
    + Delete it
  + Step 2:
    + Go to `Menu bar -> Edit -> Enable Root User`
    + Type a password and `Enter`
  + Step 3:
    + **Warning**: Do this if you are sure you can close all the apps!
    + Log out from current user
    + Log in with username `root` and the password with previously typed one
+ Delete profiles
  + Method 1:
    + Go to `System Preferences`
    + Press `Profiles`
    + Delete them
  + Method 2:
    + Open `Terminal`
    + Do `profiles list`
    + Copy the id (from `apple` to `...ff51e`)
    + Do `profiles remove -identity="{Paste here}"`
+ Log out and login to your own account.

