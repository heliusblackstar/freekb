# Writing a new article

## Summary
New articles are stored as "index.md" in a folder (named simply with a UUID).  
The article template stored under 4b857b00-8bd4-4606-9ed6-be6f751ddfe7 should be copied to your UUID folder and used as a starting point for your article.

## Style Rules
- Only use John Gruber's original variant of Markdown.
    - The original Markdown is normatively described at (https://daringfireball.net/projects/markdown/syntax), however, you may find the quick reference [Basic Markdown page at markdownguide.org easier to use.](https://www.markdownguide.org/basic-syntax/)  Everything on the Basic syntax page is Original Markdown.  Stick to what you see on these two pages.
    - Do not use other flavors/variants of Markdown or "extended" Markdown.  They are not standardized and will not display correctly for all users and all viewers.
    - Do not embed HTML.  While it is permitted by the original variant of Markdown, for the purposes of FreeKB it makes pages considerably less readable and harder to edit.  "Simple is better".
- Your article title goes in the first line of your article (see template).  Only your article title should use the Heading level 1 (#).
- If you see an image in another article you'd like to use, copy it into your article's directory first.  The other article may enventually modify or delete their copy of the image.  Making a "local copy" in your article directory preserves the image for your article's use.
- Do not use absolute references to images from the Web (the image will disappear off the Web sooner or later).  But also, don't copy images from the web into FreeKB--these will be copyrighted!  Create your own images.  
- Use code blocks to show code or command/terminal output, rather than screenshots of code or terminal output.  Text is easy to edit and takes up a lot less disk/network than images.
- For numbered lists, use `1.` as the number in front of every item and sub-item.  This makes re-ordering and adding items painless, and your Markdown viewer will automatically show the correct numbering order.  You can see an example of this in the article template.
- All images referenced by your article should be stored in your article's folder as .PNG files (not .JPG).  PNG files are small and loss-less.  Use descriptive alt text to assist users working with the raw Markdown.
- Always use relative references (such as to images and other articles).
- Never change the UUID of any folders.  Always name your article "index.md".

## Original Markdown quick reference page
https://www.markdownguide.org/basic-syntax/

## Automated method for creating a new article
- WSL script (requires `uuid` package to be installed):
    
        UUID="$(uuid -v 4)"  #generates random UUID
        mkdir "$UUID"  #makes a new article folder with UUID
        cp -v 4b857b00-8bd4-4606-9ed6-be6f751ddfe7/index.md "$UUID"  #copies template page into your article folder
        echo "Your article folder is $UUID"  #displays UUID to the user
        explorer.exe "$UUID"  #in WSL, opens the folder in Explorer

## Manual method for creating a new article
1. First we need to generate a folder for us to store our content for the new article in.  
We do this by creating a folder using any UUID v4 (random) generation tool.  We will give us a five part alphanumeric identifier that is guarunteed to be both permanent and non-conflicting with any other article in the knowledgebase.  A UUID looks like this: 9d798584-cb62-45ba-9b80-bde71b946329

    Use one of these techniques to generate your article's UUID:
    - Web:   https://www.uuidgenerator.net/ (Make sure it is a Version 4 UUID)
    - PowerShell: ``> [guid]::NewGuid()``
1. Next, create a folder with the foldername as the UUID, and copy the template from 4b857b00-8bd4-4606-9ed6-be6f751ddfe7/index.md to it.
1. Lastly, use your editor to open UUID/index.md and start editing.

## Private branch feature
If your article will contain sensitive information you don't want to put into the main instance of FreeKB, use the [private branch feature](../7ad7eca0-9a4a-4ecd-95a6-b6eff8d0116c/index.md).
    

***
_Mandatory_page_footer: This article and the rest of the FreeKB is dedicated to the public domain via the [Creative Commons CC0](../LICENSE.md)._


