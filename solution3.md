
# Virtual Machine and Nginx Hosting

This documentation provides a step-by-step guide to setting up a virtual machine with Ubuntu (or any other Linux distro) on VirtualBox, installing Nginx, and scanning the virtual machine using Nmap. The setup is done on a host machine running Linux Pop!_OS with Neovim as the text editor. Additionally, it addresses issues faced during the process.

## Prerequisites

- Oracle VirtualBox
- Nmap installed on the host machine
- Internet connection

## Steps to Setup VM and Install Nginx

### Step 1: Download and Install Oracle VirtualBox

1. Download VirtualBox from the official website: https://www.virtualbox.org/
2. Install VirtualBox using the appropriate package for your operating system.

### Step 2: Download Image

### Step 3: Create a New Virtual Machine in VirtualBox

1. Open VirtualBox and click on "New".
2. Follow the prompts to create a new VM, selecting the downloaded image as the virtual hard disk.

#### Output:
![image](https://github.com/user-attachments/assets/71dd0c7d-94d2-416e-bd00-25ca6f1b09d9)


### Step 4: Start the VM

1. Select the new VM and click "Start".

#### Output:
![Screenshot from 2024-08-01 19-39-44](https://github.com/user-attachments/assets/ba6284aa-0da5-4bc2-a394-42fecdd7deaf)


### Step 5: Install Nginx on Kali

1. Open a terminal in the Ubuntu VM.
2. Update the package lists:
   ```bash
   sudo apt update
   ```
3. Install Nginx:
   ```bash
   sudo apt install nginx
   ```
4. Verify the installation by navigating to the VM's IP address in a web browser. You should see the Nginx default page.

![Screenshot from 2024-08-01 19-40-21](https://github.com/user-attachments/assets/9b40a802-c465-4d4e-9315-a821c1409273)

### Step 6: Allocate IP Manually (if needed)

If the networking module did not automatically allocate an IPv4 address in bridged mode, manually allocate an IP address to the VM.

### Step 7: Ensure Docker and VirtualBox are not running together

Docker and VirtualBox may not run together due to conflicts with the hypervisor. Ensure that only one is running at a time to avoid issues.

## Scanning the VM with Nmap

### Step 1: Install Nmap on Host Machine

1. Open a terminal on your host machine.
2. Install Nmap:
   ```bash
   sudo apt install nmap
   ```

### Step 2: Scan the VM

1. Identify the IP address of your Ubuntu VM.
2. Run the following command to scan the VM:
   ```bash
   nmap -sV <VM_IP_ADDRESS>
   ```
#### Output:
![Screenshot from 2024-08-01 19-52-45](https://github.com/user-attachments/assets/9bfd5415-e937-4a92-aaca-9e9ea21fbca8)

### Step 3: Analyze the Output

- The scan will display open ports and services running on the VM. Look for the port where Nginx is running (default is port 80).

#### Output:

![image](https://github.com/user-attachments/assets/108f224a-8b4d-45c0-8b34-1024227c130f)

### Issues faced:

I faced two major issues when solving **question 3**. They are explained as follows:

1. I was not aware that Docker and VirtualBox would not run on the same device. Specifically, on my machine, which is Pop!_OS Linux, there was a KVM clash. As an alternative to Oracle VirtualBox, I tried to configure Virtual Machine Manager, which supports QEMU, but the configuration got too tedious, so I rolled back to VirtualBox.

   I solved this by allowing nested virtualization in VirtualBox and specifically configuring my VM **kalidenali** (which I have had as a VM image for a few years now). Then, I just shut down Docker, and the VirtualBox image used KVM as the backend.

2. Secondly, I faced an issue where, for some reason, via the **bridge** adapter, my VM was not automatically assigning an IPv4 address. So, I had to manually allocate an IP (192.168.1.123) in my VM machine, as I was aware that in my personal WLAN or LAN, that IP is available.


### Outro:
- As you may have noticed, it shows Apache2 Default page but actually I installed nginx. Maybe it's a kali package manager behaviour for distro.
- Moreover, I would like to bring in notice in *Step 2 output* is the screenshot from Kali VM and the *Step 3 output* screenshot is from my host device.
  I accessed the nginx default page from both virtual machine and host machine.

## Note

This setup is done on Linux Pop!_OS using Neovim as the text editor.

## Contact

For any issues or questions, contact Vishwesh Shukla at <vishweshshukla20@gmail.com>.
