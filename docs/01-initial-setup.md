# NorthStar Lab — Initial Setup

## 1. Lab Environment
<!-- VM names, OS versions, CPU, RAM, and storage -->
The initial planned IT infrastructure for this lab consist of two virtual machines, NS-DC01 and NS-CLIENT01. The hypervisor chosen was Oracle's VirtualBox.  

|                     |  NS-DC01                   |  NS-CLIENT01            |
|---------------------|----------------------------|-------------------------|
| Purpose             | Domain Controller          | Client Machine          |
| OS edition/build    | Windows Server 2025/64-bit | Windows 11              |
| RAM/vCPU            | 2GB/2                      | 4GB/2                   |


## 2. Network Configuration
<!-- VirtualBox network mode, IP addresses, subnet masks, and DNS -->
Initial VirtualBox Network adapter was set up for Host-Only isolation purposes. 
|                     |  NS-DC01                   |  NS-CLIENT01            |
|---------------------|----------------------------|-------------------------|
| IP address          | 10.10.10.10/24             | 10.10.10.02/24          |
| DNS                 | 10.10.10.10                | not yet set             |
| DHCP                | currently off              | not yet set             |

## 3. Windows Server Configuration

### System Identification
- **Computer name:** NS-DC01
- **Operating system:** Windows Server 2025 Standard Evaluation
- **Installation type:** Desktop Experience
- **Purpose:** Serve as the domain controller and DNS server for the northstar.test lab domain, providing centralized authentication and management of domain users and computers.

### Initial Configuration
- Renamed the server to NS-DC01 to identify its function in the lab.
- Configured a static IPv4 address. Full network settings are
  documented in Section 2.
- Set the time zone to [time zone] and verified the date and time.
- No update has been issued since installation. Will update after fully operational 
### Installed Roles and Features
- Domain Controller active
- DNS [installed], configuration and functionality still need verification.
- Active Directory domain configuration is documented in Section 4.

### Management and Security
- **Windows Firewall:** On
- **Remote Desktop:** Disabled
- [Other configuration changes actually completed]


## 4. Active Directory and DNS
<!-- Record completed setup here, or mark it as pending -->

## 5. Windows Client Configuration
<!-- Client name, edition, network settings, and current domain status -->

## 6. Verification
<!-- Tests performed, expected results, and actual results -->

## 7. Issues and Resolutions
<!-- Symptoms, investigation, changes made, and verification -->

## 8. Next Steps
<!-- Remaining prerequisites and workstation domain join -->
