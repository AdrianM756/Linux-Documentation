## Samba

[Samba](https://serverspace.io/support/glossary/samba/) is a free software re-implementation of the SMB/CIFS (Server Message Block/Common Internet File System) protocol. It is used for sharing files and printers within networks, that enable files sharing between Linux, Unix systems and Windows operating systems.

## Installation

For the installation, we will install it on a ubuntu machine. Let us first update it's packages using the command:
```
apt update -y
```
<br>

Next, We will now install ```samba``` and ```smbclient```:
```
apt install samba smbclient -y
```
<br>

## Manage users

Once all the necessary packages is installed, we will then create a user for our samba:
```
useradd -m smbuser1 && passwd smbuser1
```
<br>

The ```-m``` parameter means create the user's home directory if it does not exist.

We will then add the created user on the smbpassword file:
```
smbpasswd -a smbuser1
```
<br>

The ```-a``` parameter is used when the smb username has not yet been added to the smbpasswd file.

**NOTE:** smbpasswd differs from how the passwd program works however in that it is not setuid root but works in a client-server mode and communicates with a locally running smbd.
<br>

## Creating shared folders

Let's create a folder name ```sambashare``` on the ```/home/smbuser1``` directory:
```
mkdir /home/smbuser1/sambashare
```
<br>

Once created, let's navigate to the ```/etc/samba/smb.conf```:
```
nano /etc/samba/smb.conf
```
<br>

Let's create a folder called "folder1" and insert it between ```[]``` then add the following:
```
[folder1]
path = /home/smbuser1/sambashare
read only = no
guest ok = no
browseable = no
valid users = smbuser1
```
<br>

***Explanation:***
* ```read only = no``` means the user is allowed to modify files inside the directory.
* ``` guest ok - no``` If this parameter is yes for a service, then no password is required to connect to the service. Privileges will be those of the guest account.
* ``` browseable = no``` This controls whether this share is seen in the list of available shares in a net view and in the browse list.
* ``` valid users = smbuser1``` means the only user that is allowed to access the shared file is the ```smbuser1```.
<br>

After changing the settings, the service should be restarted:
```
systemctl restart smbd.service
```
<br>

## SMBClient

Once configured, you can test access to shared folders from another host on the network. To check from the server itself, you can use the smbclient utility to verify:
```
smbclient -U smbuser1 //[IP ADDRESS]/folder1 -c 'ls'
```
<br>

***Explanation:***
* ```-U``` refers to the username.
* ```-c``` refers to the command we want to use. In this case is the ```ls ```.


