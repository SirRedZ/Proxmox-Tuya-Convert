## Proxmox Tuya-Convert Development/testing branch.

CURRENT STATUS: Tested Working - Please advise if this script did not work for you. 

Note: Some people report Vtrust-flash AP exists, but can not connect to it with Mobile phone, etc...

This script will create a new Proxmox LXC container with the latest Debian and setup tuya-convert. To create a new LXC container in the local-lvm storage, run the following in a SSH session or the console from Proxmox interface
---
bash -c "$(wget -qO - https://raw.githubusercontent.com/Tollbringer/Proxmox-Tuya-Convert/master/create_container.sh)" -s local-lvm
---

During the setup process, you will prompted to select a wireless interface only if you have more than 1 option; Otherwise the script will now auto-select the only capable wifi adapter. This interface will be assigned to container. (Note: When the container is running, no other container or VM will have access to the interface.) After the successful completion of the script, start the container identified by the script, then use the login credentials shown to start the tuya-convert script. If you need to stop tuya-convert, press CTRL + C and it will be halted and you will be brought back to the login prompt. If you login again it will start tuya-convert again.

### Prerequisite

Please make sure Proxmox is fully updated before running this script. In order for this script to work appropriately, you must first have the drivers installed and setup correctly for your WiFi adapter in Proxmox. The beginning the of the script will test for valid WLAN interfaces. An error will be produced if one can not be found.

### Custom Firmware

To add custom firmware (not supplied by tuya-convert), connect to the samba share created by the container (details are provided at the login prompt) and add the binary to the tuya-convert/files/ folder. Your binary will listed under the custom firmware menu.

This script is only possible thanks to Whiskerz007 efforts, and Tuya-Converts maintainer - Colin Kuebler
