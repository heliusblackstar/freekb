# TEMPLATE: Your article title must go here in the Heading level 1 style

## Summary
The uptime command can show you server uptime in two formats.

## Steps
1. If you run `uptime` with no parameters you will also see load average and the current time:
        
        $ uptime
        21:10:41 up 4 days,  2:14,  0 users,  load average: 0.52, 0.58,    0.59
    
1. Uptime is represented by this part:
    
        1:10:41 up **4 days,  2:05**,  0 users,  load average: 0.52, 0.58,    0.59

1. It may be easier to use the `--pretty` option:
        
        $ uptime --pretty
        up 4 days, 2 hours, 14 minutes
    




***
_Mandatory_page_footer: This article and the rest of the FreeKB is dedicated to the public domain via the [Creative Commons CC0](../LICENSE.md)._

