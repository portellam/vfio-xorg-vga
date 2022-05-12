## What is VFIO?
* See hyperlink:  https://www.kernel.org/doc/html/latest/driver-api/vfio.html

#
## How-to
* In terminal, execute:
 
        sudo bash installer.sh
* It is NOT necessary to execute 'Auto-Xorg.sh'. The service will run once at boot. See '/etc/X11/xorg.conf.d/10-Auto-Xorg.conf'.
* Optionally, to restart the active Display Manager, execute:

        sudo bash Auto-Xorg.sh dm
  

#
## Auto-Xorg
Generates Xorg for first non-VFIO VGA device.
* Runs once at boot.
* Parses list of PCI devices:

        lspci -k
* Saves first (valid) available VGA device.
  * Valid example:

        04:00.0 VGA compatible controller: ...
        Kernel driver in use: nvidia
  * Invalid example:

        01:00.0 VGA compatible controller: ...
        Kernel driver in use: vfio-pci
* Appends to Xorg file ('/etc/X11/xorg.conf.d/10-Xorg-vfio-pci.conf').
* Optionally, restart active display manager

        sudo bash Auto-Xorg.sh dm
