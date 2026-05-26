
# Project 03 — Azure VM Deployment & Management

## Overview
Deployed and managed Windows and Linux virtual machines in Azure,
configured high availability using Availability Sets, implemented
secure access via Azure Bastion, created snapshots for backup,
and configured auto-shutdown for cost management.

## What I built
A complete Azure compute environment demonstrating Windows and Linux
VM deployment, high availability configuration using Availability Sets,
secure browser-based access via Azure Bastion, disk snapshots for
backup, and auto-shutdown for cost management.

## Step-by-step — what I did

### 1. Created Resource Group and VNet
- rg-vm-lab resource group in North Europe
- vnet-vm-lab with subnet-vms (10.0.1.0/24) for VM connectivity

### 2. Deployed Windows Server VM
- Windows Server 2022 Datacenter, Standard E2s_v3 size
- No public IP — access via Bastion only
- Standard HDD OS disk for cost efficiency

### 3. Deployed Linux VM
- Ubuntu Server 22.04 LTS, Standard E2s_v3
- Same VNet and subnet as Windows VM
- Password authentication configured

### 4. Configured Availability Set
- Created avset-vm-lab with 2 fault domains and 5 update domains
- In production: VMs assigned at creation time to ensure
  Azure places them in separate physical racks
- Protects against hardware failure and planned maintenance

### 5. Set up Azure Bastion for secure access
- Deployed Bastion Basic tier in dedicated AzureBastionSubnet
- Connected to Windows VM via browser-based RDP session
- No RDP (3389) or SSH (22) ports exposed publicly
- Best practice for production VM access

### 6. Created VM snapshot
- Point-in-time snapshot of Windows VM OS disk
- Used for backup before configuration changes
- Can be used to restore or clone the VM

### 7. Configured Auto-shutdown
- Both VMs set to auto-shutdown at 17:00 GMT
- Email notification enabled before shutdown
- Prevents unexpected charges from forgotten running VMs

## Screenshots
| Resource group | [RG](screenshot/01-resource-group.png) |
| Windows VM deployed | [Win](screenshot/02-vm-windows.png) |
| Linux VM deployed | [Linux](screenshot/03-vm-linux.png) |
| Both VMs running | [Both](screenshot/04-both-vms-running.png) |
| Availability Set | [AvSet](screenshot/05-availability-set.png) |
| Bastion connection | [Bastion](screenshot/06-bastion-connection.png) |
| Bastion VM | [BastionVM](screenshot/07-bastion-vm.png) |
| VM Snapshot | [Snap](screenshot/08-snapshot.png) |
| Auto-shutdown | [Shutdown](screenshot/09-auto-shutdown.png) |
| Cleanup complete | ![Clean](screenshot/10-cleanup.png) |

## Key concepts demonstrated
- VM deployment — Windows and Linux side by side
- VM sizing — choosing right size for workload and cost
- Availability Sets — fault domains vs update domains
- Azure Bastion — secure access without public IP exposure
- Snapshots — point-in-time disk backup
- Auto-shutdown — cost management best practice
- No public RDP/SSH — security best practice

## AZ-104 domains covered
- Domain 3: Deploy and manage Azure compute resources
  - Create and configure VMs
  - Configure VM availability (Availability Sets)
  - Configure VM networking and secure access
  - Manage VM disks and snapshots
