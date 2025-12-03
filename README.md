# Setting Up Vulnerable Services on a Windows VM Using Docker

## Objective

The goal of this lab is to transform a standard Windows 10 virtual machine into a multi-service vulnerable host by installing Docker and running several intentionally insecure applications inside containers. These services will later be discovered and enumerated using Nmap and other tools from a separate Kali Linux machine.

### Skills Learned

By the end of this setup, the Windows VM will expose:

- DVWA (Damn Vulnerable Web App) on port 8080
- MySQL 5.7 with weak credentials on port 3306
- Juice Shop (optional) on port 3000


### Prerequisites 

Host System

- VMware Workstation installed on your main system
- CPU virtualization enabled in BIOS (Intel VT-x or AMD-V)

Windows VM

- Windows 10 installed as a guest OS
- VM must have nested virtualization enabled

Enabling Nested Virtualization in VMware

- This step allows Docker to run inside the Windows VM.
- Shut down the Windows VM completely

In VMware Workstation:

- VM → Settings → Processors → Check:
- “Virtualize Intel VT-x/EPT or AMD-V/RVI”
- Power the VM back on

Verify Virtualization Inside the Windows VM

- Open Task Manager → Performance → CPU
- Look for:
- Virtualization: Enabled

This confirms the VM supports running Docker.


### Steps 

### 1. Install WSL2 (Windows Subsystem for Linux)

### <img width="721" height="173" alt="image" src="https://github.com/user-attachments/assets/c06f0870-53cd-4a6f-8a75-47c7a84cf058" />

Docker Desktop on Windows relies on WSL2 as the backend that actually runs containers. Without WSL2, Docker cannot start its engine, and containerized services won’t run. Enabling WSL2 ensures the VM has the Linux-compatible layer Docker needs -- ultimately, prepareing the windows VM for Docker, installs, the virtualiztion layer used by the Docker Engine, and ensures compatbility, with Linux based vulnerable images. 

### 2. Install Docker Desktop

Go to https://www.docker.com/products/docker-desktop/ inside of your windows VM. 

During installation allow for this setting:

- USE WSL2 Backend = Yes 

Docker Desktop is the tool that manages containers, pulls vulnerable images, exposes ports, and runs pre-built applications. It provides the interface and Docker Engine needed to run multiple vulnerable services simultaneously inside of our Windows machine.

Reboot as instructed. 

### 3. Deploying Vulnerable Services Using Docker

The goal of this section is to transform the Windows VM into a realistic multi-service target by running vulnerable applications inside Docker containers. These applications expose additional ports (8080, 3306, optionally 3000) that you can later discover using Nmap and enumerate from Kali.
Everything we run here is pre-built, intentionally vulnerable, and safe for lab use.


### 3.1 Deploy DVWA (Damn Vulnerable Web App)

### <img width="597" height="198" alt="image" src="https://github.com/user-attachments/assets/8e6d8096-51b6-4734-a40a-36dc8c8fbe7e" />

DVWA is a deliberately insecure PHP/MySQL web application. It is perfect for practicing:

- web reconnaissance
- forced browsing
- authentication testing
- file uploads
- SQL injection
- XSS
- brute force
- CSRF attacks

### 3.2 Deploy MySQL 5.7 With Weak Credentials

<img width="1050" height="120" alt="image" src="https://github.com/user-attachments/assets/7d86ac50-79b1-4ac0-93ff-8b13a9adedf5" />

This runs MySQL on port 3306 and then verifies it is running. MySQL is commonly found in real environments and provides an excellent opportunity to practice database enumeration, user/privilege discovery, service recognition from port scanning, and weak credential testing.

### 3.3 Pulling the DVWA Docker Image

In powershell run: 
docker pull vulnerables/web-dvwa

This retrieves the official DVWA image from Docker Hub.
DVWA is pre-configured, pre-built, and intentionally insecure — meaning no manual setup, web stack installation, or database configuration is required.

### 3.4  Run DVWA and Expose It Externally

### <img width="612" height="27" alt="image" src="https://github.com/user-attachments/assets/8a133c65-000e-459c-a2d2-c5bd948de7d8" />

### 3.5 Verify Docker Services are Running 

<img width="1072" height="96" alt="image" src="https://github.com/user-attachments/assets/aa2a94dd-d0d8-4f9e-8a34-fd3bb901e9e1" />





















