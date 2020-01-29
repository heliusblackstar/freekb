# "DataBee" data loss bug

## Summary
Like a bee copies pollen from one flower to another, you should be aware of this issue which can cause you to inadvertently copy stale files from one git branch to another.   
DataBee has been observed to cause both existing files to be overwritten as well as unwanted creation of files.  
This doesn't seem to be a Git bug, although it's hard to say if your OS or the your Editor is ultimately to blame.  
Or it might be the users fault.

## Detailed explanation of DataBee
When you run `git checkout`, your editor should automatically update to show you the new versions of the files you just checked out.  However, due to DataBee, in some environments, it will not.  So your editor will still show versions from "branch A", but you have checked out "branch B".   
You will then begin editing the files in your editor, unaware that your editor is still showing files from "branch A".  Then, when you hit Save/Save All in your editor, your editor will overwrite the copy of the files in "branch B" with the copies it is showing on-screen from "branch A".  It can also save an unwanted copy of files from "branch A" into "branch B".  
This will cause either data loss and/or unwanted data creation.  Regardless, you may not even be aware you've been stung by DataBee.  
Until it's too late.

## Known safe environment
 You can avoid this bug simply by running git and your editor on the same computer as your files.  

Known safe examples:
 - Visual Studio Code running on Windows 10, running git via WSL, editing files stored on Windows 10's local disk.
 - emacs running on a Debian 10 server, running git on the same server, editing files stored on the same server.

## Known vulnerable environments
If any of (git, your editor, or your files) are not all on the same computer, you may experience this bug.

Vulnerable examples:
- Atom or emacs running on Windows 10, editing remote files stored on a mapped network drive from a Linux network CIFS share, running git on the server.
- Atom running on Windows 10, running git on Windows 10 (Git for Windows), editing remote files stored on a mapped network drive from a Linux network CIFS share.

## How to detect if you are vulnerable
1. Find a file that has been changed a lot.  Run `git log filename.txt` to see commit hashes for this file.  We will use any 10 of these commit hashes.
1. Open this file in your editor.
1. Run `git checkout (put commit hash here)` on the next commit hash in the `git log` list to checkout the file from that commit.
1. Make sure without clicking any buttons in your editor that your editor shows the updated version.
1. Run `git checkout master`.
1. Make sure without clicking any buttons in your editor that your editor shows the updated version.
1. Repeat steps 3-6 about 10 times to determine if you are vulnerable to this issue. If at any time your editor does not auto-update promptly to show the new checked out version, close and re-open your editor.  If your editor now shows the new version, **you are vulnerable to DataBee and you must change your environment as above.**



***
_Mandatory_page_footer: This article and the rest of the FreeKB is dedicated to the public domain via the [Creative Commons CC0](../LICENSE.md)._

