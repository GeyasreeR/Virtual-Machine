# Multi-VM Vagrant Setup

This project sets up a multi-VM environment using Vagrant. It includes two Ubuntu servers (`web01` and `web02`) and one CentOS server (`db01`). These VMs are configured with private network IPs for seamless communication within the environment.

## Prerequisites

Make sure you have the following installed before proceeding:

- **[Vagrant](https://www.vagrantup.com/downloads)**
- **[VirtualBox](https://www.virtualbox.org/)**

## VMs Configuration

| VM Name | Operating System        | IP Address      | Purpose         |
|---------|-------------------------|-----------------|-----------------|
| web01   | Ubuntu 18.04 (bionic64) | 192.168.56.10   | Web server 1    |
| web02   | Ubuntu 18.04 (bionic64) | 192.168.56.11   | Web server 2    |
| db01    | CentOS 7                | 192.168.56.12   | Database server |

## Setup Instructions

### 1. Clone or Create the Project Directory

```bash
mkdir Multivm
cd Multivm
```

### 2. Save the Vagrantfile
Copy the provided Vagrantfile into the project directory.

### 3. Bring Up the VMs
Run the following command to start all VMs:

```bash
vagrant up (To bring up all the Vms at once)
or
vagrant web01
vagrant web02
vagrant db01
to bring up the required Vms
```
### 4. Access the VMs
SSH into web01:
```bash
vagrant ssh web01
```
SSH into web02:
```bash
vagrant ssh web02
```
SSH into db01:
```bash
vagrant ssh db01
```

### Network Configuration
The VMs are configured with the following private network IPs:

web01: 192.168.56.10
web02: 192.168.56.11
db01: 192.168.56.12
You can modify these IP addresses in the Vagrantfile if necessary.
