# Windows shows wrong time after dual-booting or cold boot

## Summary
This is a flaw in Microsoft Windows.  The incorrect behavior can be corrected with a registry setting.

## Symptoms
Windows VMs will report a drastically different time when cold booted.  This can also happen on physical machines if the machine dual-boots with Linux, and the system is booted into Linux and then later into Windows.  This time difference should be exactly a number of hours different from the actual time, depending on the time zone (e.g. it will be 6:05 PM and the Windows clock will show 11:05 PM).  While the displayed timezone will show as appropriately set, the time will match the current Coordinated Universal Time.

This behavior is rarely noticed as it is only apparent during a cold boot.  Cold boots occur rarely in production environments.

This can disrupt authentication with other systems such as external AD domains and RADIUS authentication.

## Root Cause
The root cause of this is a flaw in how Windows handles calculates time as read from BIOS/EFI by default, versus how all other operating systems do.

When a VM is cold booted, the VM's system clock is given the correct time in UTC.  Linux based systems will then apply a timezone offset to UTC to determine local time.  However, Windows does not use any timezone offset to determine local time--it will simply take the current system time (UTC) and displays it as local time.  Window's default behavior is to assume the BIOS hardware clock is already set to what it regards as "local time", even though the rest of the industry functions differently.

So for a cold-booted VM or dual-booted machine, Windows simply displays the current time as being the same as the system clock (UTC) instead of applying the configured timezone offset to determine the current time.   In theory if the system is configured to sync with an Internet time-source, Windows will realize this error and auto-correct, but in practice this does not always happen, and if outbound Internet access is unavailable/blocked, it will not happen.

This can disrupt authentication with other systems such as domain controllers.

## Workaround
Use the Windows UI to sync the time with an Internet timeserver after logging in.

## Permanent Fix

Note, changing your timezone is not the correct answer.

This is a flaw in Windows. 

There is a registry edit that can force Windows to properly interpret the current time based on the UTC received from the BIOS system clock. This command will set the registry key:

    reg add "HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\TimeZoneInformation" /v RealTimeIsUniversal /d 1 /t REG_DWORD /f

After setting this in the registry, reboot.   If you perform a cold-boot, Windows should display the time correctly immediately.  If you warm-rebooted and the system is unable to contact an NTP server, you will need to adjust the time manually after the reboot.

The time should remain correct on all subsequent reboots.

## Sources:
https://www.zerto.com/myzerto/knowledge-base/windows-vm-after-failover-failover-test-move-is-showing-up-with-an-incorrect-time/

https://oofhours.com/2020/10/07/windows-10-and-a-pcs-real-time-clock/

https://kb.vmware.com/s/article/1318?lang=en_US


*** 
_Mandatory_page_footer: This article and the rest of the [FreeKB](../README.md) is dedicated to the public domain via the [Creative Commons CC0](../LICENSE.md)._


