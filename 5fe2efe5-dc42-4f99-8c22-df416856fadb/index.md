# Windows shows wrong time after dual-booting or cold boot

## Summary
This is a flaw in Microsoft Windows.  The incorrect behavior can be corrected with a registry setting.

## Estimated Time to Read
2 minutes at 200 words per minute.

## Symptoms
Windows VMs will report a drastically different time when cold booted.  This can also happen on physical machines if the machine dual-boots with Linux, and the system is booted into Linux and then later into Windows. 

The time difference should be exactly a certain number of hours different from the actual time, depending on the time zone (e.g. it will be 6:05 PM and the Windows clock will show 11:05 PM).  While the displayed timezone will match expectations, Windows clock will show the current time as whatever UTC is currently.

## Root Cause
The root cause of this is a flaw in how Windows handles calculates time as read from BIOS/EFI by default, versus how all other operating systems do.

When a VM is cold booted, the VM's system clock is given the correct time in UTC.  Linux based systems will then apply a timezone offset to UTC to determine local time.  However, Windows does not use any timezone offset to determine local time--it will simply take the current system time (UTC) and displays it as local time.  It does this because it assumes the hardware clock will always be set to "local time", as this is what Windows sets it to, even though this is not a standard expectation for hardware clocks.

So for a cold-booted VM or dual-booted machine, Windows simply displays the current time as being the same as the system clock (UTC) instead of applying the configured timezone offset to determine the current time.   In theory if the system is configured to sync with an Internet time-source, Windows will realize this error and auto-correct, but in practice this does not always happen.

This can disrupt authentication with other systems such as domain controllers.

## Workaround
Use the Windows UI to sync the time with an Internet timeserver after logging in.

## Permanent Fix

Note, changing your timezone is not the correct answer.

There is a registry edit that can force Windows to expect the hardware clock to be set to UTC, and to therefore apply the timezone offset correctly.  This change is:

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\TimeZoneInformation]
"RealTimeIsUniversal"=qword:00000001

In 32-bit Operating systems, you will want to use DWORD instead of QWORD. 

After setting this in the registry, reboot.  Login again, and force a time sync with an Internet time source, or manually fix the system time in the VM.  This should correct this behavior error.


*** 
_Mandatory_page_footer: This article and the rest of the [FreeKB](../README.md) is dedicated to the public domain via the [Creative Commons CC0](../LICENSE.md)._


