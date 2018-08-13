# HyperV-Dietpi-VM
Contains instructions on how to convert the dietpi image to HyperV environment.


# Intro:

I've been using Hyper-VM because Oracle VB is not so practical to me at this time. I wanted to prototype a couple ideas with linux and possibly with raspberry pi because I own a couple of the so I needed a working Hyper-VM dietpi option.



Bellow you can find all the steps I did to get it to work, but if you just want something ready to be used, just download the DietPi_VMWare-x86_64-Stretch.7z and inside you will find the vhd file ready to be used as a Hyper-V hard drive.



# Requirements:
  
- Enable HyperV. You can follow this compreensive guide / tutorial at https://www.youtube.com/watch?v=KQUQtSuwWpc
  
- Powershell should be enabled by default.
  
- Download and install mvmc_setup.msi which can be found inside this repo (root level) and also is available at https://www.microsoft.com/en-us/download/details.aspx?id=42497



# The following steps can be used:
  
- Visit dietpi.com and download VMWare dietpi image. Just press go to Download (top bar) --> PC/VM (option) to find the download link.
  
- Unzip the file to a folder, for example to C:\temp\. You just need the vmdk file
  
- Run the following commands as local administrator user:

```vb

PS C:\WINDOWS\system32>Import-Module 'D:\Programas\Microsoft VM Converter\MvmcCmdlet.psd1'

PS C:\WINDOWS\system32>ConvertTo-MvmcVirtualHardDisk -SourceLiteralPath C:\Temp\DietPi_VMware-x86_64-Stretch.vmdk -VhdType DynamicHardDisk -VhdFormat vhdx -destination C:\Temp\

```
  
- Wait for the vhd file is created.
  
- Create VM using Hyper VM adjusting all settings accordingly. When asked to select or create an hard drive, just use your new vhd file. All default settings like users and passwords were not changed.
  
- Optional: After booting it, you should update the vhd file to the latest dietpi version. Run dietpi-update.



# Usefull reading:

Hyper-V & Powershell HOW-TO: https://blogs.msdn.microsoft.com/timomta/2015/06/11/how-to-convert-a-vmware-vmdk-to-hyper-v-vhd/