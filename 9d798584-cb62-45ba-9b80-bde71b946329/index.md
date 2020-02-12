# Writing a new article

## Summary
New articles are stored as "index.md" in a folder (named simply with a UUID).  
Writing a new article is as simple as copying the template article stored under 4b857b00-8bd4-4606-9ed6-be6f751ddfe7 into your new UUID folder and using that as a starting point for your article.

## Style Rules
### Use CommonMark
-  Due to ambiguities in John Gruber's original documentation regarding Markdown, you should use CommonMark.org to learn Markdown.  CommonMark offers a highly compatible and clear specification for Markdown, with beginner guides and a full specification document.   FreeKB uses the [CommonMark specification](https://spec.commonmark.org/current/) of Markdown.
- Do not embed HTML.  While it is otherwise permitted in Markdown, for the purposes of FreeKB it makes pages considerably less readable and harder to edit.  "Simple is better".

### Filing system
- Folders are named simply with a random UUID (UUID v4).  Never change the UUID of any folders (this would break hyperlinks).  All articles are named "index.md". 
- Your article title goes in the first line of your article (see template).  Only your article title should use the Heading Level 1 (#).
- All images referenced by your article should be stored in your article's folder as .PNG files (not .JPG).  PNG files are small and loss-less.  Use descriptive alt text in your article to assist users working with the raw Markdown.
- Always use relative references (such as to images and other articles).  [Example relative hyperlink to TEMPLATE article](../4b857b00-8bd4-4606-9ed6-be6f751ddfe7/index.md).
- If you see an image in another article you'd like to use, copy it into your article's directory first.  This is necessary as the other article may eventually modify/delete their copy of the image, or the other article may be removed entirely in the future.  Making a "local copy" in your article directory preserves the image for the lifetime of your article.

### Article text rules
- Use code blocks to show code and command/terminal output, rather than screenshots of code and terminal output.  Text is easy to edit and copy to the clipboard.  It also takes up a lot less disk & network than images.
- For numbered lists, use `1.` as the number in front of every item and sub-item.  This makes re-ordering and adding items painless, and your Markdown viewer will automatically show the correct numbering order.  You can see an example of this in the article template.


### You must write your own content
- Do not use absolute references to hot-link to images on the Web (the image will disappear off the Web sooner or later).  
- Don't copy images from the Web into FreeKB--these will be copyrighted!  You must create your own images.  
- You cannot copy content someone else has written (which would be copyrighted) and put it into FreeKB, which is public domain.  You don't have the right to release their copyrighted work into the public domain, only the author does.  You must write your own content, which will then go into [the public domain per FreeKB's license](../LICENSE.md).


## CommonMark Markdown quick reference page
https://commonmark.org/help/

## Automated method for creating a new article
- WSL script (requires `uuid` package to be installed):
    
        UUID="$(uuid -v 4)"  #generates random UUID
        mkdir "$UUID"  #makes a new article folder with UUID
        cp -v 4b857b00-8bd4-4606-9ed6-be6f751ddfe7/index.md "$UUID"  #copies template page into your article folder
        echo "Your article folder is $UUID"  #displays UUID to the user
        explorer.exe "$UUID"  #in WSL, opens the folder in Explorer

## Manual method for creating a new article
1. First we need to generate a folder for us to store our content for the new article in.  
We do this by creating a folder using any UUID v4 (random) generation tool.  This will give us a five part alphanumeric identifier that is guarunteed to be both permanent and non-conflicting with any other article in the knowledgebase.  A UUID looks like this: 9d798584-cb62-45ba-9b80-bde71b946329

    Use one of these techniques to generate your article's UUID:
    - Web:   https://www.uuidgenerator.net/ (Make sure it is a Version 4 UUID)
    - PowerShell: ``> [guid]::NewGuid()``
1. Next, create a folder with the foldername as the UUID, and copy the template from 4b857b00-8bd4-4606-9ed6-be6f751ddfe7/index.md to it.
1. Lastly, use your editor to open UUID/index.md and start editing.

## Private branch feature
If your article will contain sensitive information you don't want to put into the main instance of FreeKB, use the [private branch feature](../7ad7eca0-9a4a-4ecd-95a6-b6eff8d0116c/index.md).

## Privacy for your name or email address
Before you `git commit`, [ensure your configuration name and email address are what you want to show in your commits](./05771c30-f03e-4dbb-8aee-ea0c57545626/index.md).
    

***
_Mandatory_page_footer: This article and the rest of the FreeKB is dedicated to the public domain via the [Creative Commons CC0](../LICENSE.md)._


