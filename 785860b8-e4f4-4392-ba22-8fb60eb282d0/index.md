# KeePass - Enabling automatic backups

## Summary
A KeePass trigger can be used to setup automatic backups.  This can be done to the same directory as your KeePass file, or a different directory.

## Steps
1. Click `Tools`, `Triggers`.
        
1. Click `Add`, set name as `Backup database when opening`.

1. Under `Events` tab, use event `Opened database file`.   Leave the `File/URL` fields as-is. 

1. On the `Actions` tab, use action `Execute command line / URL`.  

1. For `File/URL`, enter `%comspec%`

1. For `Arguments`, enter `/c copy "{DB_PATH}" "{DB_DIR}\{DB_BASENAME}-backup-{DT_SIMPLE}".kdbx`

1. Under `Window style`, select `Minimized`.

1. Click `OK`, `Finish`, `OK`.

Effective immediately, each time you open or unlock your KeePass file, KeePass will create a backup copy of your KeePass file in the same directory as your file.  If you wish to store the backup in some other storage location, you can change the directory to some other absolute path by changing the `Arguments` for the trigger.  

Backups will be created in the same directory as your KeePass file and will be named similar to "YourDatabaseName-backup-20221120190358.kdbx" (YYYYMMDDHHMMSS).

Adapted from https://keepass.info/help/kb/trigger_examples.html#backuponopen
    

*** 
_Mandatory_page_footer: This article and the rest of the [FreeKB](../README.md) is dedicated to the public domain via the [Creative Commons CC0](../LICENSE.md)._


