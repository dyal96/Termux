# Termux
Useful Commands and Troubleshoots

### Install SSH 

run this command in termux terminal ` pkg install openssh `

Run SSH ` sshd ` in termux terminal

Find Username by running ` whoami ` in termux 

Set Password for login by running ` passwd ` command

Configure SSH Daemon for Root Login:

Open the sshd_config file for editing using a text editor like nano: `nano usr/etc/ssh/sshd_config.` 

Find the line that says #PermitRootLogin prohibit-password or `#PermitRootLogin yes` (it may be commented out with a #).
also set or add `Port 8022`

Change it to PermitRootLogin yes and remove the # if present.

You might also need to add the line `StrictModes no` if you encounter permission issues later.

### Install PROOT-Distros 

Install Proot by `pkg install proot-distro`

Install Debian by `proot-distro install debian`

 See Available Distros in by `proot-distro list`
<details>
</summary> Supported distributions (format: name < alias >): </summary>

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
</details>
Install selected one with: proot-distro install <alias>
 
### ADB Port Forwading
ADB port forwarding is a mechanism in the Android Debug Bridge command-line tool that allows you to **forward TCP traffic between your development machine and an Android device (or emulator)**. This is particularly useful for debugging network applications.  

Key Commands

There are two primary commands for port forwarding: 

- **`adb forward`**: Forwards a port on your computer to a port on the Android device.
    - **Syntax**: `adb forward tcp:<local_computer_port> tcp:<device_port>`
    - **Example**: `adb forward tcp:8080 tcp:3000`
    - **Result**: Traffic sent to port `8080` on your development machine is funneled to port `3000` on the connected Android device. This is useful for accessing a server running on the device from your computer's browser or other tools.
- **`adb reverse`**: Forwards a port on the device to a port on your development machine. This is the inverse of `adb forward`.
    - **Syntax**: `adb reverse tcp:<device_port> tcp:<host_computer_port>`
    - **Example**: `adb reverse tcp:9090 tcp:8080`
    - **Result**: Traffic sent to port `9090` on the Android device is redirected to port `8080` on your development machine. This is commonly used when you have a web server running on your computer (e.g., a local development server) and want to access it from an app or browser on the device.

Management Commands

- **List existing forwards**: `adb forward --list`
- **Remove a specific forward**: `adb killforward:<local_computer_port>`
- **Remove all forwards**: `adb killforward-all`
- **Remove a specific reverse forward**: `adb killreverse:<device_port>` (or `adb reverse --remove tcp:<device_port>`)
- **Remove all reverse forwards**: `adb reverse --remove-all` 

Prerequisites

- You need the [Android SDK Platform Tools](https://developer.android.com/tools/releases/platform-tools) installed and accessible from your command line.
- **USB debugging** must be enabled in the Developer options on your Android device.
- The device should be connected to your computer (either via USB or wireless debugging). You can verify the connection by running `adb devices`.


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

For Modded Ubuntu you can try this[ Ubuntu Mod Repo](https://github.com/modded-ubuntu/modded-ubuntu)

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

### VM using QEMU and Docker in Termux
Setup VM using [This Thread](https://medium.com/@kumargaurav.pandey/vms-on-mobile-without-root-yes-please-f14f473deec7)
Setup Docker [using this thread](https://medium.com/@kumargaurav.pandey/docker-on-mobile-that-too-without-root-how-7b0848833c42)

