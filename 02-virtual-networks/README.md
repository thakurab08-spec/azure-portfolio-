
# Project 02 - Azure Virtual Network Setup

## Overview
Built a complete Azure networking environment with two VNets,
subnets, Network Security Group rules, and VNet Peering to
connect the networks privately.

## What I built
- Created resource group in region North Europe
- Created 2 VNets (vnet-hub, vnet-spoke)
- Created 2 Subnets (subnet-web, subnet-app)
- Applied 3 NSG rules (Allow HTTP, Allow HTTPS, Deny All)
- Did VNet Peering (hub to spoke)

## Network Architecture

[Network Diagram](screenshots/network-diagram.png)

## Step-by-step — what I did

### 1. Created a Resource Group
- rg-vnet-lab in North Europe region
- Contains all lab resources for easy cleanup

### 2. Created two Virtual Networks
- vnet-hub: address space 10.1.0.0/16
  with subnet-web (10.1.1.0/24)
- vnet-spoke: address space 10.2.0.0/16
  with subnet-app (10.2.1.0/24)
- Different address spaces required — overlapping
  spaces prevent peering

### 3. Created and configured NSG
- Created nsg-web with 3 inbound rules:
  - Priority 100: Allow HTTP (port 80)
  - Priority 110: Allow HTTPS (port 443)
  - Priority 4000: Deny all other inbound traffic
- Associated NSG to subnet-web in vnet-hub
- Note: NSGs must be explicitly associated, creating one does not activate it

### 4. Configured VNet Peering
- Created bidirectional peering between vnet-hub
  and vnet-spoke
- Both peering links show status: Connected
- Resources in either VNet can now communicate
  privately without traversing the public internet

## Screenshots
| Resource group | [RG](screenshots/01-resource-group.png) |
| vnet-hub overview | [Hub](screenshots/02-vnet-hub.png) |
| vnet-spoke overview | [Spoke](screenshots/03-vnet-spoke.png) |
| NSG inbound rules | [NSG](screenshots/04-nsg-rules.png) |
| NSG subnet association | [Assoc](screenshots/05-nsg-association.png) |
| VNet peering connected | [Peering](screenshots/06-vnet-peering.png) |
| Cleanup complete | [Cleanup](screenshots/07-cleanup.png) |


## Key concepts demonstrated
- VNet design and IP address planning (CIDR)
- Subnet segmentation
- NSG rule priority (lower number = higher priority)
- NSG must be associated to activate
- VNet Peering for private cross-network communication
- Address spaces must not overlap for peering to work

## AZ-104 domains covered
- Domain 4: Implement and manage virtual networking
  - Create and configure VNets and subnets
  - Configure NSGs and security rules
  - Configure VNet peering
