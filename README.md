# Setting Up Vulnerable Services on a Windows VM Using Docker

## Objective

The goal of this lab is to transform a standard Windows 10 virtual machine into a multi-service vulnerable host by installing Docker and running several intentionally insecure applications inside containers. These services will later be discovered and enumerated using Nmap and other tools from a separate Kali Linux machine.

### Skills Learned

By the end of this setup, the Windows VM will expose:

- DVWA (Damn Vulnerable Web App) on port 8080
- MySQL 5.7 with weak credentials on port 3306
- Juice Shop (optional) on port 3000


### Prerequisites 

1.1 Host System

VMware Workstation installed on your main system

CPU virtualization enabled in BIOS (Intel VT-x or AMD-V)

1.2 Windows VM

Windows 10 installed as a guest OS

VM must have nested virtualization enabled

1.3 Enabling Nested Virtualization in VMware

This step allows Docker to run inside the Windows VM.

Shut down the Windows VM completely

In VMware Workstation:
VM → Settings → Processors → Check:
“Virtualize Intel VT-x/EPT or AMD-V/RVI”

Power the VM back on

1.4 Verify Virtualization Inside the Windows VM

Open Task Manager → Performance → CPU
Look for:
Virtualization: Enabled

This confirms the VM supports running Docker.





## Steps











