# Azure Virtual Desktop Deployment for Seamless Remote Access

## Introduction

This project outlines the deployment and configuration of an Azure Virtual Desktop (AVD) environment, optimized to provide reliable, secure remote access for users working across multiple devices. By implementing robust cloud infrastructure, network optimizations, and user profile management with FSLogix, this setup enhances remote accessibility and improves performance for end-users.

## Click here for the video demonstration
[![Video Demonstration](https://github.com/gurkaran-singh1/Azure-Virtual-Desktop-Deployment-for-Seamless-Remote-Access/blob/main/images/AZproject.JPG)](https://seneca-my.sharepoint.com/:v:/g/personal/gurkaran-singh1_myseneca_ca/ERia6qkg7hFCs82p2MZ_aXYBoc0N6rc8TuSi601mq3euSg?e=82Lu2z&nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJTdHJlYW1XZWJBcHAiLCJyZWZlcnJhbFZpZXciOiJTaGFyZURpYWxvZy1MaW5rIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXcifX0%3D)

## Table of Contents

1. [Goal](#goal)
2. [Requirements](#requirements)
3. [Step-by-Step Instructions](#step-by-step-instructions)
4. [Uses and Functionality](#uses-and-functionality)
5. [Contributing](#contributing)

## Goal

The primary goal of this project is to deploy and configure an Azure Virtual Desktop environment that supports secure, high-performance remote access while managing user profiles and data securely across sessions.

## Requirements

- **Azure Subscription**
- **Azure AD tenant**
- **On-premises AD for hybrid integration** (optional)
- **Basic knowledge of PowerShell or Azure CLI** for scripting tasks
- **FSLogix** for managing user profiles

## Step-by-Step Instructions

### 1. **Create a Virtual Network (VNet)**
   - Log into Azure and go to **Virtual Networks**.
   - Create a new VNet with your assigned address space (e.g., `192.168.9.0/24`).
   - Configure subnets, including a dedicated subnet for AVD host pools.

### 2. **Provision Virtual Machines for Session Hosts**
   - Create VMs within your VNet to serve as session hosts.
   - Configure these VMs with **Windows 10 Enterprise multi-session** images.
   - Enable **boot diagnostics** for easy troubleshooting.

### 3. **Configure the VM as a Domain Controller**
   - RDP into the VM and use Server Manager to add the **Active Directory Domain Services** role.
   - Promote the VM to a Domain Controller by creating a new forest (e.g., `yourdomain.local`).

### 4. **Setup FSLogix Profile Containers**
   - Install FSLogix on all session hosts.
   - Configure Azure Files or Azure NetApp Files to store profile containers.
   - Use FSLogix GPO templates to specify container storage locations.

### 5. **Enable Conditional Access Policies**
   - Set up Conditional Access policies in Azure AD to enforce secure access:
     - Allow only corporate or approved personal devices.
     - Require MFA for all users, with exceptions if necessary.

### 6. **Configure Load Balancing and Scaling**
   - Use **Breadth-first load balancing** to evenly distribute users across session hosts.
   - Enable **scaling automation** to start/stop VMs during off-peak hours.

### 7. **Optimize Network Performance**
   - Configure Site-to-Site VPN or ExpressRoute for on-premises connectivity if applicable.
   - Use **Azure Virtual Desktop Experience Estimator** to select an optimal region.
   - Implement **Azure Firewall** and Network Security Groups (NSGs) for network security.

### 8. **Testing and Monitoring**
   - Test AVD access using both internal and remote user devices.
   - Enable **Azure Monitor** and **Log Analytics** to track AVD performance and user activity.

## Uses and Functionality

- **Remote Access**: Provides secure, high-performance remote access for distributed users.
- **Profile Management**: FSLogix manages user profiles, ensuring a consistent experience across sessions and devices.
- **Conditional Access**: Ensures only approved devices and authenticated users can access resources.
- **Scalability**: The deployment scales based on demand, optimizing costs during off-peak hours.
- **Network Security**: Integrates VPN and NSGs to secure traffic, supporting compliance and protecting sensitive data.

## Contributing

Feel free to suggest improvements, report issues, or submit pull requests to enhance this AVD deployment guide.
