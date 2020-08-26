# VBox_Raspbian_NodeRED_MongoDB
Instructions for preparing a VirtualBox Image with Raspbian Desktop + Node-RED + MongoDB

Install the latest Oracle VirtualBox (https://www.virtualbox.org/)

#### Note: Windows 10 Pro and Enterprise users need to disable Hyper-V in order to make VirtualBox works (See https://support.microsoft.com/en-au/help/3204980/virtualization-applications-do-not-work-together-with-hyper-v-device-g)
 
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

Under **Oracle VM VirtualBox Manager**, Click **[Settings]**

 * Select **Storage**, select **Empty** under **Controller: IDE**
 * Click the **CD** icon next to **Optical Drive**, select the latest Raspbian Desktop image file (https://www.raspberrypi.org/downloads/raspberry-pi-desktop/)

Click **[OK]**

Under **Oracle VM VirtualBox Manager**, Click **[Start]**

Select **Graphical Install** from the bootup menu and follow the on-screen instructions

## Install the display driver (Optional)

Once Raspbian Desktop is installed, from the toolbar of the VirtualBox window on the **Host PC**, select **Devices --> Insert Guest Additions CD image**

Then, on **Raspbian Desktop**, open a Terminal, type
```
sudo sh /media/cdrom/VBoxLinuxGuestAdditions.run
sudo reboot
```
After rebooting, open a Terminal and type
```
lxrandr
```
Select your desired resolution and click **Apply**

## Install Node.js

In the Terminal and type
```
sudo apt-get update
sudo apt-get dist-upgrade
curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash -
sudo apt-get install -y nodejs
sudo apt-get install -y npm
```

## Install Node-RED

In the Terminal and type
```
sudo npm install -g --unsafe-perm node-red
```

## Install MongoDB

### Import the public key used by the package management system

In the Terminal and type
```
wget -qO - https://www.mongodb.org/static/pgp/server-4.2.asc | sudo apt-key add -
```

### Create a /etc/apt/sources.list.d/mongodb-org-4.4.list file for MongoDB

In the Terminal and type
```
echo "deb http://repo.mongodb.org/apt/debian buster/mongodb-org/4.2 main" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.2.list
```

Create the directory in the default location by running 
```
sudo mkdir -p /data/db
```
Make sure that the directory has the right permissions by running
```
sudo chown -R `id -un` /data/db
```

### Reload local package database

In the Terminal and type
```
sudo apt-get update
```

### Install the MongoDB packages

In the Terminal and type
```
sudo apt-get install -y mongodb-org=4.2.8 mongodb-org-server=4.2.8 mongodb-org-shell=4.2.8 mongodb-org-mongos=4.2.8 mongodb-org-tools=4.2.8
```

### Start Node-RED and MondoDB

In the Terminal and type
```
sudo mongod
node-red
```

## Install extra nodes
Open a browser and type http://127.0.0.1:1880

* Click the **Three Strips** icon on the top-right corner
* Select **Manage palette** 
* Select the **Install** Tab, search with the keyword **mqtt** 
* Install **node-red-contrib-mqtt-broker** (v. 0.2.4)

* Next, search wtih the keyword **mongo** 
* Install **node-red-node-mongodb** (v. 0.0.14)



