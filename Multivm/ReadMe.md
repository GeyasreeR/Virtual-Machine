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
mkdir multivm-vagrant-setup
cd multivm-vagrant-setup
