# nsa310On Linux, the best way to share files from computer to computer reliably is with NFS. Hosting an NFS server on Linux isn’t impossible, but it is difficult for beginners. If you’re dying to get a couple of NFS shares working, your best bet is to use OpenMediaVault. It’s a robust, beginner-friendly NAS solution with a web-based GUI tool that makes setting up NFS shares simple.

To follow this guide, you’ll need to have OpenMediaVault installed on your Linux server as well as appropriate hard drive space to hold all the data for NFS. Follow our tutorial and learn how to install OpenMediaVault, then come back to this article, and follow this guide to set up NFS shares.

Configure File System
Setting up an NFS share on OpenMediaVault first requires a usable file system. Unfortunately, OMV doesn’t allow the user to create a share from the web UI on the OS hard drive. It is because of this, we recommend using a dedicated hard drive for data. If you can’t afford to use multiple hard drives, consider reinstalling OpenMediaVault, and following a custom partition setup, rather than the automatic one in the setup. Another option would be virtualizing OpenMediaVault. Using the OS as a VM allows users to create custom virtual hard drives.

Once you’ve attached the second hard drive, open up the OMV web UI (https://ip.address.of.omv.server), look at the side-bar for “Storage”, and click the “Disks” option. Look under disks, and make sure the second hard drive is appearing correctly there. Click “wipe” to clear everything from it.



When the hard drive is blank, go back to “Storage” and click “File Systems”. You’ll notice that only /dev/sda1 (the main OS drive) appears in this menu. The reason that the second drive isn’t also listed is that it doesn’t have a file system on it. To create a new one, click the “+ Create” button, and select “/dev/sdb” under the “Device” menu in the pop-up.



Note: always go with Ext4 as the file system, if you’re unsure.

Now that the new /dev/sdb file system is up and running, you’ll see it under /dev/sda1. To make use of this hard drive, select /dev/sdb1 in the menu, then click “Mount”.

Creating Shared Folders
Using NFS on OpenMediaVault requires a shared folder. To create one, look at the side-bar under “Services” for “NFS” and click on it. Click on “Shares”. and then select “+ Add” to create a new folder. It’s important not to use an existing shared folder that is in use by another service on OMV.

In the “Add share” menu, there are many options. The first of which is a menu that lets the user select an existing share. In this menu, click the + sign. Clicking + brings up a sub-menu. In this sub-menu, you’ll need to fill out information for the new shared folder.

The first thing you’ll need to fill out is “Name”. Enter a name, and then move on to “Device”. Under device, click the drop-down menu and look for “/dev/sdb1”, as this is the hard drive we set up earlier.

After filling out the “Device” section, all that is left is “Path”, “Permissions” and “Comment”. Skip the “Path” section, as OpenMediaVault will do this automatically, and move on to “Permissions”.

Look through the Permissions area, and find the correct settings for your use case. When done, fill out a comment about the share, and click “Save”.



Clicking the save button will take you out of the sub-menu, and back to the original menu that opens when “+ Add” is clicked. In this menu, do the following:

Under “Client”, enter 192.168.1.0/24.

After the “Client” option, move on to “Privilege” and select Read/Write.

Add the share to the system by clicking “Save”.

Enable NFS On OpenMediaVault
Now that we have a shared folder for NFS to use, click the “Settings” tab in the NFS area. Enable NFS on your OpenMediaVault NAS by clicking the slider next to “Enable”, then select the “Save” button. Be sure to also click “Apply” on the pop-up that says “The configuration has been changed. You must apply the changes in order for them to take effect.”

Need to disable NFS? Click the slider again to disable it, then select “Save” to save the changes.

Deleting NFS shares
To delete an NFS share in OpenMediaVault, select “NFS” under “Services”, and then click on “Shares”. In the shares menu, highlight the share you’d like to delete, and click “X Delete” to remove it.

Access NFS Shares
With OpenMediaVault’s help, setting up something as tedious as NFS becomes much easier. Despite this, accessing shares can still be a chore. If you’re unsure on how to access and use NFS shares on Linux, do yourself a favor and follow our tutorial. It covers everything there is to know about accessing NFS on Linux.
