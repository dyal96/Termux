# Termux
Useful Commands and Troubleshoots

### Install SSH 

run this command in termux terminal ` pkg install openssh `

Run SSH ` sshd ` in termux terminal

Find Username by running ` whoami ` in termux 

Set Password for login by running ` passwd ` command

### Install PROOT-Distros 

Install Proot by `pkg install proot-distro`

Install Debian by `proot-distro install debian`

 See Available Distros in by `proot-distro list`

Supported distributions (format: name < alias >):

  * Adélie Linux < adelie >
  * AlmaLinux < almalinux >
  * Alpine Linux < alpine >
  * Arch Linux < archlinux >
  * Artix Linux < artix >
  * Chimera Linux < chimera >
  * Debian (trixie) < debian >
  * Deepin < deepin >
  * Fedora < fedora >
  * Manjaro < manjaro >
  * OpenSUSE < opensuse >
  * Oracle Linux < oracle >
  * Pardus < pardus >
  * Rocky Linux < rockylinux >
  * Termux < termux >
  * Trisquel GNU/Linux < trisquel >
  * Ubuntu (25.10) < ubuntu >
  * Void Linux < void >

Install selected one with: proot-distro install <alias>


### Install SSH via USB using ADB

Download [ADB ( Platform Tools )](https://developer.android.com/tools/releases/platform-tools)

Windows Powershell `adb forward tcp:8022 tcp:8022 ; ssh -p 8022 root@localhost`

Linux ` adb forward tcp:8022 tcp:8022 && adb forward tcp:8080 tcp:8080 && ssh localhost -p 8022 `

This will also setup the port 8080, which is used by the httpd webserver on termux

Setup adb in adding the path of enviorment variables. 

### Reverse Tether (Share Internet PC to Phone Via USB ) ADB and & gnirehtet

- Download [gnirehtet](https://github.com/Genymobile/gnirehtet)
- Install Apk in Phone ( Available in Zip File )
- Run CMD in Folder and Then ` gnirehtet.exe run ` there should be adb already in path. 

### Mirror Screen on PC using Scrcpy
Download , Extract , Run Scrcpy.exe [Scrapy ](https://github.com/Genymobile/scrcpy/releases)


### Steps to Install Ubuntu Desktop in Termux

Install/Update Termux: Use the F-Droid version for better compatibility, then run:

`pkg update && pkg upgrade.`

Install proot-distro: Install the tool that allows running Linux distributions:

`pkg install proot-distro`

Install Ubuntu: Download and install the Ubuntu image:

`proot-distro install ubuntu`

Login to Ubuntu:

`proot-distro login ubuntu`

Update and Install GUI (XFCE): Inside the Ubuntu container, update packages and install the desktop environment:

`apt update && apt upgrade -y`
`apt install xfce4 xfce4-goodies tigervnc-standalone-server -y`

Configure VNC: Set up a password and configure VNC:
`
vncserver
### Set a password
`
Run the Desktop: Start the VNC server to enable GUI access:

`vncserver -geometry 1280x720 :1`

Connect: Open a VNC Viewer app (like VNC Viewer) and connect to 127.0.0.1:5901. 

