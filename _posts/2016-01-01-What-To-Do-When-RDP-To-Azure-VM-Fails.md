---
layout: post
title: What to Do When RDP to Azure Virtual Machine Fails
tags: others
cover: 
excerpt: Some lessons learned as a newbie in Microsoft Azure :)
---

Firstly, calm down. It can be recovered. I believe you have tried to search for solutions online but still unable to get the right solution. You have tried to restart the VM, reset access, resize the VM, etc. But the problem persists. Believe me, I have been there too. I was unable to access to the virtual machine after configuring some cipher. If you did the same, most likely the solution below will be helpful to you. So these are the steps that you can try.

- Create a new temp VM for troubleshooting.

- Delete, not shut down, the problematic VM (the VM that is experiencing problem) and kept the disk. Be extra careful not to delete the disks from the problem VM, ensure you do not tick the delete harddisk option. We have to delete the VM otherwise we will not be able to attach the OS harddisk to other VM.

- Atttach the disk to the temp VM as data disk. We can follow this link (follow the steps for attaching the harddisk) to finish this step.

- Open Regedit. Select `HKEY_LOCAL_MACHINE` in the left pane of Regedit, then click the File, Load Hive, and browse to the \Windows\System32\Config folder on the drive of the problem VM. For example, if the second VM only has its OS disk attached plus the drive from the problem VM, the path will likely be F:\Windows\System32\Config.

- Select the file named `SYSTEM` in the Config folder. This is the HKEY_LOCAL_MACHINE\System hive from the problem VM’s registry. Give it a key name such as ASystemHive (this is only a temporary name used while the hive is loaded), and click OK.

- Look at the `Select` key under ASystemHive (or whatever you called the loaded hive) and check the `Current` value. If `Current` is 1, make your changes in ControlSet001, if it is 2, make them in ControlSet002, etc.

- In the `ControlSet`, go to \services\SharedAccess\Parameters\FirewallPolicy in ControlSet001 (or in ControlSet002).

- Change the all EnableFirewall values found in DomainProfile, PublicProfile and StandardProfile to 0.

- Go to ControlSet001 (or in ControlSet002) folder and navigate to \Control\Terminal Server\Winstations\RDP-Tcp. (Note: We can also change RDP portnumber from here)

    - Change value of "SecurityLayer" to 0
    - Change value of " UserAuthentication " to 0
    - Change value of " fAllowSecProtocolNegotiation " to 0

- Then detach the disk from the temp VM by going to the Azure portal and create a new VM based on the kept disk. Check the RDP and hopefully it is working fine now.

If everything else fails, you can always raise a [support](https://azure.microsoft.com/en-us/support/legal/faq/) request to Azure team. In my experience, they are extremely helpful and patience. You just need to define the problems clearly. All the best!

