---
layout: post
title:  "List of most commonly used git commands"
date:   2018-01-02 10:00:00
categories: Tools
tags: git github commands terminal command promt
comments: true
logo: exchange
---
List of most commonly used commands of git (if you're a fan of using git using terminal)

`git init`

Create an empty Git repository or reinitialize an existing one

`git clone`

Clone a repository into a new directory

`git add fileA fileB`

Add changeset of files - `fileA` and `fileB`.

`git add .`

Add all changesets.

`git commit -m "Message of commit"`

Commit your changes with message `Message of commit`.

`git reset --hard`

Reset everything & checkout the most recent revision.

`git push origin master`

Push your changes to master branch of origin = remote repository.

`git push origin feature/siri`

Push your changes to `feature/siri` branch of `origin` = remote repository.

`git pull origin master`

Pull changes from remote `origin`'s master branch to your local branch.

`git pull origin some/branch`

Pull changes from remote `origin`'s `some/branch` branch to your local branch.

`git checkout some/branch`

Switch to `some/branch` from current branch on local.

`git checkout some-revision`

Checkout the specific revision.

`git log -1`

Show most recent commit log.

`git log -2`

Show most 2 recent commit log.

`git status`

Show current changesets in list format showing files.

`git show`

Show changesets in detailed view.

`git fetch --all`

Fetch everything from every remotes.

`git tag Version1Tag`

Apply a tag to current status.

`git push origin --mirror`

Push everything from local. Create a replica of local to remote.

`git push -u origin some/branch`

Push local branched named `some/branch` to remote origin.

`git push origin --tags`

Push all local tags to remote origin.

`git push origin refs/tags/tag_a`

Push a specific tag to remote origin.
