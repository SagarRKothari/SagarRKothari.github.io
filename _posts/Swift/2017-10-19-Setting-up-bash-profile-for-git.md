---
layout: post
title:  "Setting up .bash_profile for Git Terminal Mac OSX"
date:   2017-10-19 10:00:00
categories: Scripts
tags: bash profile git mac osx
comments: true
logo: terminal
---

### Step 1. Download

Download following files.

* [git-completion]({{ "/assets/2017-10-19/git-completion.bash"| absolute_url }})
* [git-prompt]({{ "assets/2017-10-19/git-prompt.sh" | absolute_url }})

### Step 2. Move

Move this files under your user's root directory. 

In my case it is `/Users/sagar`

### Step 3. Edit your `.bash_profile`

This file is usually located under user's root directory. In my case it is `/Users/sagar`.
Open `.bash_profile` with editor of your preference. I prefer `vi` editor. 
Insert following lines.

```sh
# Enable tab completion
source ~/git-completion.bash

# colors!
green="\[\033[0;32m\]"
blue="\[\033[0;34m\]"
purple="\[\033[0;35m\]"
reset="\[\033[0m\]"

# Change command prompt
source ~/git-prompt.sh
export GIT_PS1_SHOWDIRTYSTATE=1
# '\u' adds the name of the current user to the prompt
# '\$(__git_ps1)' adds git-related stuff
# '\W' adds the name of the current directory
export PS1="$purple\u$green\$(__git_ps1)$blue \W $ $reset"
```