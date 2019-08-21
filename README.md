# VBox_Raspbian_NodeRED_MongoDB
Instructions for preparing a VirtualBox Image with Raspbian Desktop + Node-RED + MongoDB

Install the latest Oracle VirtualBox (https://www.virtualbox.org/)

#### Note: Windows 10 Pro and Enterprise users need to disable Hyper-V in order to make VirtualBox works

## Install Raspbian Desktop into a Virtual Machine

Under **Oracle VM VirtualBox Manager**, Click **[New]**

 * Enter **RPi** as the name
 * Select **Linux** under the **Type** pull-down menu
 * Select **Debian (64-bit)** under the **Version** pull-down menu
 * Allocate **1024 MB** of memory to the virtual machine

Click **[Create]**

 * Allocate **16 GB** to the Virtual Hard Disk
 * Check **VDI (VirtualBox Disk Image)**
 * Check **Dynamically allocated**
 
Click **[Create]**

 * Under **Oracle VM VirtualBox Manager**, Click **[Settings]**
 * Select **Storage**, select **Emppty** under **Controller: IDE**
 * Click the **CD** icon next to **Optical Drive**, select the latest Raspbian Desktop image file (https://www.raspberrypi.org/downloads/raspberry-pi-desktop/)

Click **[OK]**

Under **Oracle VM VirtualBox Manager**, Click **[Start]**
