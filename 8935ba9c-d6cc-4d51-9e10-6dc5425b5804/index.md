# Do not snapshot a domain controller

## Summary
You should not snapshot a domain controller, nor take a snapshot of a domain controller with the intent to roll the domain controller back to that snapshot, regardless of the circumstances, as Microsoft repeatedly recommends not to snapshot any domain controller on any version of Windows Server up to and including Windows Server 2012, 2012R2, AND 2016.

## Evidence
Rather than challenging whether the answer that you should not snapshot a domain controller, challenge the question of why you are inclined to do so.  You are probably doing something wrong and should change your approach to the situation.  Do not attempt to justify using a hammer as a screwdriver.


Microsoft's "Virtualizing Domain Controllers" (https://docs.microsoft.com/en-us/windows-server/identity/ad-ds/get-started/virtual-dc/virtualized-domain-controllers-hyper-v#operational-considerations-for-virtualized-domain-controllers) article says:
- "**Do not use the Snapshot feature** as a backup to restore a virtual machine that was configured as a domain controller. Problems will occur with replication when you revert the virtual machine to an earlier state with Windows Server 2008 R2 and older. For more information, see USN and USN Rollback. Although using a snapshot to restore a read-only domain controller (RODC) will not cause replication issues, this method of restoration is still not recommended. " 
- "**Do not take or use a Snapshot of a virtual domain controller. It is technically supported with Windows Server 2012 and newer, it is not a replacement for a good backup strategy.** There are few reasons for taking DC snapshots or restoring the snapshots."
- " **the use of snapshots with domain controllers is not recommended.**"

Microsoft's "Safely virtualizing Active Directory Domain Services (AD DS)" (https://docs.microsoft.com/en-us/windows-server/identity/ad-ds/introduction-to-active-directory-domain-services-ad-ds-virtualization-level-100#virtualization-based-safeguards) article says:
- "**With Windows Server 2012**, AD DS employs safeguards on virtual domain controllers hosted on VM-GenerationID aware hypervisors and ensures that the **accidental application of snapshots** or other such hypervisor-enabled mechanisms that could rollback a virtual machine's state does not disrupt the AD DS environment (by preventing replication problems such as a USN bubble or lingering objects). **Restoring a domain controller by applying a virtual machine snapshot is not recommended as an alternative mechanism to backing up a domain controller. It is recommended that you continue to use Windows Server Backup or other VSS-writer based backup solutions.** "  

Microsoft's "Virtualized Domain Controller Troubleshooting" (https://docs.microsoft.com/en-us/windows-server/identity/ad-ds/manage/virtual-dc/virtualized-domain-controller-troubleshooting#BKMK_SpecificProblems) KB article says: 
- "If you snapshot a domain controller, an Event 2170, of Warning severity will be placed in the Directory Services Event Log: "A Generation ID change has been detected.  The Generation ID change occurs after the application of a **virtual machine snapshot**, after a virtual machine import operation or after a live migration operation. Active Directory Domain Services will create a new invocation ID to recover the domain controller. **Virtualized domain controllers should not be restored using virtual machine snapshots. The supported method to restore or rollback the content of an Active Directory Domain Services database is to restore a system state backup made with an Active Directory Domain Services aware backup application.**"
- Event ID 1109 may also be logged to the Directory Services Event Log:  "**Virtualized domain controllers should not be restored using virtual machine snapshots. The supported method to restore or rollback the content of an Active Directory Domain Services database is to restore a system state backup made with an Active Directory Domain Services-aware backup application.**" 
    


*** 
_Mandatory_page_footer: This article and the rest of the [FreeKB](../README.md) is dedicated to the public domain via the [Creative Commons CC0](../LICENSE.md)._


