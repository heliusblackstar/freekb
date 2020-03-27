# Building an Overview page

## Summary
In addition to the methods for browsing and searching described in the README, you can build an overview page for FreeKB.  Per template, the first 5 lines of all articles contain the title and summary of the article--we can use this to build a page containing an overview of the entire knowledgebase.

All below methods should be executed from the top-level folder of FreeKB.

## Steps
### Bash/WSL:

- Dumps list of titles, summaries, and filenames:  `find ./ | grep "index.md" | xargs head -n 5 > Overview.md`
- Dumps list of titles, summaries, and creates links to each filename:  `find ./ | grep "index.md" | xargs head -n 5 | sed 's/==> /==> [link to below article](/' | sed 's/ <==/) <==/' > Overview.md`

Note that:
- You'll need to rebuild the Overview page manually when your copy of FreeKB is updated (if you want to have the Overview mention page show articles, or changes to titles/summaries).
- The order that articles are listed in the Overview isn't alphabetical by article title.  It's alphabetical by article UUID, so it will seem like the article titles are in a "random order" (they are!).
    

**To prevent merge conflicts, "Overview.md" is listed in .gitignore.**



*** 
_Mandatory_page_footer: This article and the rest of the [FreeKB](../README.md) is dedicated to the public domain via the [Creative Commons CC0](../LICENSE.md)._


