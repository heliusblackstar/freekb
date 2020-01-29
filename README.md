# README
## Welcome to FreeKB
FreeKB is a knowledge base for technical topics.  All content is in the public domain, thus "Free".

## Design framework of FreeKB
- **Simple** is better.
- **Distributed** is better than centralized.  Centralized gets expensive to maintain (see Wikipedia's recurring donation requests).  Currently FreeKB is managed & distributed via Git, but copies could also be distributed via BitTorrent, USB sticks, etc.
- **Plain-text** is better than a database or an app.
- Markdown syntax gives us plain-text with rich-text features.
- **Portable**  is important.  **Files in a folder on your own computer are better than a server** loaded up with a complex network of web libraries, interpreters, frameworks, and custom packages that will require maintenance to keep running and accessible.
- Everyone should be able to use the tools of their own choice to read and modify the KB, though we will all follow certain style and structure conventions.
- **Powerful search is already in your OS and editor/IDE**, no need to re-invent search tools.
- **Hyperlinks between articles should NEVER be broken**.  To ensure this, we give each article its own folder, not based on an article title (which may change), but on a UUID (example: 71dbb5b0-c3f6-4784-9d66-bde0cc64616d), which is dedicated to that article.
    - All articles are named "index.md", and the actual article title is in the plain-text of the article, on the first line.  This ensures the filename never changes, even if the article title changes (and thus hyperlinks are permanent and never break), and also provides ease-of-use for any scripts or programs built on top of FreeKB.
- Any images used by an article are stored in the same directory as the article, in loss-less PNG format.  Modern PNG is both small and loss-less.  Embedded images is a feature of Markdown, so any Markdown viewer will display an image if we insert a simple statement like the following code example:

        ![Example image](widget.PNG)
    
- All links within articles are relative (to images or to other FreeKB articles).
- To communicate an article link to a person, you can:
    - Use the friendly name, such as, "Writing a new article".
    - Use the UUID, such as "see article 9d798584-cb62-45ba-9b80-bde71b946329"
    - Send a link to the article on GitHub: https://github.com/heliusblackstar/freekb/blob/master/9d798584-cb62-45ba-9b80-bde71b946329/index.md .  The URL contains the UUID, so they can either use the link or look it up in their local copy of FreeKB.
- The entire knowledgebase is placed into the **public domain**, allowing anyone to use and modify the contents of the KB in any way they wish.  [See LICENSE.md](LICENSE.md).

## Using the Knowledgebase
### Searching for content on a subject
Rather than re-invent search, use the search tools already in your editor and OS.
- Open the FreeKB folder in your File Explorer or text editor/IDE and do a full-text search for the keywords you are interested in.
- Use grep to do a keyword search against the article titles:
 
        $ egrep --exclude-dir=.git -r "^# " * | grep -i "backups"
        2a945188-5721-472e-9efb-33dbae37a49e/index.md:# Backups with VRXA
- Use grep to do a full-text keyword search against all article content:

        $ grep --colour=ALWAYS --context=3 --exclude-dir=.git --recursive --ignore-case "linux"
        *
        9d798584-cb62-45ba-9b80-bde71b946329/index.md-https://www.markdownguide.org/basic-syntax/
        9d798584-cb62-45ba-9b80-bde71b946329/index.md-
        9d798584-cb62-45ba-9b80-bde71b946329/index.md-## Automated method for creating a new article
        9d798584-cb62-45ba-9b80-bde71b946329/index.md:- Bash/WSL/Linux:
        9d798584-cb62-45ba-9b80-bde71b946329/index.md-
        9d798584-cb62-45ba-9b80-bde71b946329/index.md-        #bash script:
        9d798584-cb62-45ba-9b80-bde71b946329/index.md-        UUID="$(uuid -v 4)"
        --
        d18c2f6b-a5e2-48ca-971b-61e5f5cabe9e/index.md-- Copy public key to server:
        d18c2f6b-a5e2-48ca-971b-61e5f5cabe9e/index.md-  - ssh-copy-id -i ~/.ssh/id_ed25519.pub remoteuser@server.top.tld
        d18c2f6b-a5e2-48ca-971b-61e5f5cabe9e/index.md--  On Windows, use Pageant or ssh-agent under WSL as your ssh-agent.
        d18c2f6b-a5e2-48ca-971b-61e5f5cabe9e/index.md:- On Linux/Mac, run these two commands:
        d18c2f6b-a5e2-48ca-971b-61e5f5cabe9e/index.md-  - ssh-agent
        d18c2f6b-a5e2-48ca-971b-61e5f5cabe9e/index.md-  - ssh-add -t 8h   #keeps keys in memory for 8 hours
        d18c2f6b-a5e2-48ca-971b-61e5f5cabe9e/index.md-  - ssh-add -D  #clears all keys out of memory

### Browsing all articles
#### Use grep to generate a table of contents
You can generate a table of contents with grep from the top-level folder:   
- Article UUIDs and titles:

        $ egrep --exclude-dir=.git -r "^# "
        4b857b00-8bd4-4606-9ed6-be6f751ddfe7/index.md:# TEMPLATE: Your article title must go here in the Heading level 1 style
        9d798584-cb62-45ba-9b80-bde71b946329/index.md:# Writing a new article
        d18c2f6b-a5e2-48ca-971b-61e5f5cabe9e/index.md:# SSH Public Key Authentication Commands
        README.md:# README

- Article Titles, alphabetized

        $ egrep --exclude-dir=.git -r "^# " | cut -c 47-500 | sort

        # Building an Overview page
        # Creating cross-sheet formula references in a spreadsheet
        # "DataBee" data loss bug
        # Enabling IPv6 on CentOS
        # Setting up a complex password pattern for KeePass's password generator
        # Setting up TAWS G-Code for 3D Printers
        # SSH Public Key Authentication Commands
        # TEMPLATE: Your article title must go here in the Heading level 1 style
        # Writing a new article

#### Building an Overview page of all articles
Want a page that links to each article and shows a title and summary?
[See this article.](0922a119-067c-4b34-95ea-0e8866aa4467/index.md)

### Suggested Markdown Editors/Viewers:
The benefit of Markdown is that you can edit and view it via any plain-text editor, but to see images inline and for a better experience, you can try an editor with Markdown support:
- [Visual Studio Code](https://code.visualstudio.com/docs/languages/markdown) has Markdown preview and also supports full-text searching when you use Open Folder.
- [Atom](https://atom.io/packages/markdown-preview) has Markdown preview.
- Online Markdown editors/viewers:
    - [StackEdit](https://stackedit.io/app#)
    - [Dillinger](https://dillinger.io/)

## Contributing
All content in the knowledgebase is dedicated to the public domain via [The Creative Commons CC0, stored in LICENSE.md](LICENSE.md).  Please review LICENSE.md before contributing any content.

You cannot place content written by others (and thus copyrighted) into the public domain, so please ensure any content you contribute is completely written by you.

### Writing a new article
[How to write a new article.](9d798584-cb62-45ba-9b80-bde71b946329/index.md)




***
_Mandatory_page_footer: This article and the rest of the FreeKB is dedicated to the public domain via the [Creative Commons CC0](LICENSE.md)._

