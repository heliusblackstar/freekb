# Setting an alternate name and email address to use for your commits in a Git repository

## Summary
You can specify an alternate name and email address to use when you are working with a specific Git repository.  You may wish to use a pseudonym for your commits for a specific Git repository or hide your usual email address.  Once you make these changes, it will be effective for new commits (not any existing ones).

## Steps
1. When inside a git repository, you can run `git config --list` to see the name and email that will be shown in any new commits.  

        user.email=you@example.com
        user.name=Your Name
        core.repositoryformatversion=0
        core.filemode=false
        core.bare=false
        core.logallrefupdates=true
        core.ignorecase=true
        remote.origin.url=git@github.com:heliusblackstar/freekb.git
        remote.origin.fetch=+refs/heads/*:refs/remotes/origin/*
        branch.master.remote=origin
        branch.master.merge=refs/heads/master

1. You can open `.git/config` and add these lines to override the name and email for a repository:

        [user]
        name = John Smith
        email = none@example.com

1. After this, you can verify your new name and email is set by looking at `git config --list`.  The output is a set of variables that is interpreted from top to bottom (a "user.name" and "user.email" this is later in the list overrides earlier ones).

        user.email=you@example.com
        user.name=Your Name
        core.repositoryformatversion=0
        core.filemode=false
        core.bare=false
        core.logallrefupdates=true
        core.ignorecase=true
        remote.origin.url=git@github.com:heliusblackstar/freekb.git
        remote.origin.fetch=+refs/heads/*:refs/remotes/origin/*
        branch.master.remote=origin
        branch.master.merge=refs/heads/master
        user.name=John Smith
        user.email=none@example.com


*** 
_Mandatory_page_footer: This article and the rest of the [FreeKB](../README.md) is dedicated to the public domain via the [Creative Commons CC0](../LICENSE.md)._


