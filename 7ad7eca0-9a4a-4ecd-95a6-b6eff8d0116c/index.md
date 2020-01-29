# Private branch feature

## Summary
You can use a git branch to store articles you wish to keep private, or that do not follow the Design Framework or Style Rules of the original instance of FreeKB.  This article gives recommendations on how to do this.

## Note
This article does make the assumption that you used Git to obtain the original instance of FreeKB (authoritatively stored at https://github.com/heliusblackstar/freekb).

## Why?
Perhaps you or your organization want to use the design of FreeKB, but you want to keep your articles private and not contribute them back to the original instance.  Your articles may contain sensitive information, or just may not at all be helpful to anyone outside your organization.

Using Git, you can create your own private branch where public articles are mixed in with your private articles, and you do not contribute your private articles out to the public.

You may or may not wish to occasionally pull new articles from the original instance of FreeKB into your separate instance.  Since articles are stored in folders using UUIDs, there's a good chance you'll still be able to pull articles from the original instance into your instance from time to time without too much headache.  Of course, if you've rewritten the README.md or [the Style Rules on the new article how-to page](9d798584-cb62-45ba-9b80-bde71b946329\index.md) to fit your own worldview, you'll have to account for that on your side.

## Suggested method
### Git cloning, then using a private branch with "private" prefixed before private article UUIDs
**This method is recommended if you intend to still contribute to FreeKB, but want to keep some of your articles in a private branch.  This method also keeps your future options open.**

After git cloning the main instance to your machine, articles in the original instance of FreeKB will be stored in folders with a UUID as the name, as here:

        $ ls
        41e45de3-25bf-4b06-87d6-2f74b6bbd848
        6450d106-8045-449b-9bf8-9ad23db8d714
        8917ef97-878d-47d5-9d64-fb7e69a44dbb
        ff8eefe9-3d87-4cb6-94e4-7ef1fa9d24d0
        24afd842-efe3-49c2-884f-e54e4415bc1c

However, you could do a "git checkout -b private" to checkout a new branch, and then simply never push that branch back to the original instance.  You could still push that branch to other remotes, such as your own private server.
To help distinguish articles that should NEVER be made public, it is suggested that "private-" be used as a prefix for your folder names.  Example:

        $ ls
        private-18502467-9937-4621-a676-c06ffcaed651
        private-eb70adef-1bea-42c9-81c1-268fa69a46b8
        private-421abab4-b8c9-41a3-a88e-8ad3daff176e
        a56b4299-46aa-43fc-8311-2214e311b8de
        983f7be6-21a8-4c13-bccb-e5e5d196521a

Since the branch won't ever be pushed to a public place, the public would never see any article titles with this private prefix.  Additionally, the prefix violates the Style Rules, so it wouldn't be approved for merging into master in the original instance of FreeKB anyway).  This "private-" prefix in your branch name and folder names will help everyone who uses any instance of FreeKB identify articles that should not be made public.

This private prefix would also show in hyperlinks, allowing you to identify any articles or links which link to a private article.

You could then use "git checkout" to switch between your "master" (which would be the original instance of FreeKB) and your "private" branch and merge master into private as you see fit, if you'd like to ever incorporate new articles from the original FreeKB into your private branch.

In your private branch, you could technically do whatever you want.  In your own private branch, you wouldn't even need to follow the Style Rules or Design Framework.  


***
_Mandatory_page_footer: This article and the rest of the FreeKB is dedicated to the public domain via the [Creative Commons CC0](../LICENSE.md)._

