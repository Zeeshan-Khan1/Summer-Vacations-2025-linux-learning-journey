Oracle Linux is a free, enterprise-class Linux distribution developed by Oracle. It’s often used for servers, especially in enterprise environments.

1. Download Oracle Linux ISO

Go to Oracle Linux Downloads
.

Choose the latest stable version (e.g., Oracle Linux 9).

Download the ISO file (Full ISO for complete installation or Boot ISO for minimal installation).

2. Create a Bootable USB

On Linux:

sudo dd if=OracleLinux.iso of=/dev/sdX bs=4M status=progress


(replace /dev/sdX with your USB drive)

On Windows:

Use Rufus or BalenaEtcher to create a bootable USB from the ISO.

3. Boot from USB

Insert the USB into the server/PC.

Enter BIOS/UEFI (usually F2, F10, F12, or DEL at startup).

Select Boot from USB.

4. Start Installation

Choose Install Oracle Linux.

Select Language & Keyboard.

Set Time & Date.

Configure Installation Destination:

Use Automatic partitioning (recommended for beginners).

Or create custom partitions if required.

Select Software Selection:

Minimal Install (basic CLI only).

Server with GUI (if you need desktop environment).

Configure Network & Hostname (set a hostname, enable network).

Set Root Password and create a user.

5. Complete Installation

Click Begin Installation.

Wait for installation to finish.

Reboot the system.

6. Post-Installation Setup

After reboot, log in and update your system:

sudo dnf update -y


Check OS version:

cat /etc/os-release


Enable common services (example: SSH):

sudo systemctl enable sshd --now

7. (Optional) Add EPEL Repository
sudo dnf install -y oracle-epel-release-el9


✅ You now have Oracle Linux installed and ready to use!
