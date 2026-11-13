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
| DNS                 | 10.10.10.10                | 10.10.10.10             |
| DHCP                | currently off              | not set yet             |

The lab currently uses a single subnet because it contains only one department and one client workstation. Additional subnetting or network segmentation has not been implemented.

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
- DNS [installed].
- Active Directory domain configuration is documented in Section 4.

### Management and Security
- **Windows Firewall:** On
- **Remote Desktop:** Disabled 
- [Other configuration changes actually completed]
- [Screenshot](/images/NS-DC01_VB_Setup_.PNG)


## 4. Active Directory and DNS

### Active Directory Configuration
- **AD DS role:** Installed
- **Domain controller promotion:** Completed
- **Domain name:** northstar.test 
- **Domain controller hostname:** NS-DC01
- **NetBIOS domain name:** NORTHSTAR
### DNS Configuration
- **DNS Server role:** Installed
- **DNS server IP address:** 10.10.10.10
- **Forward lookup zone:** __msdcs.northstar.test
- **DNS forwarders:**  

### Current Status
- Initial configuration completed, client machined joined the domain under utilizing the newly created user account: "alex"

## 5. Windows Client Configuration

The Windows client VM serves as the end-user workstation for the NorthStar lab.
It will be used to test domain sign-in, Group Policy, and common help desk tasks.

- **Computer name:** NS-CLIENT01
- **Operating system:** Windows 11
- **VirtualBox network:** VirtualBox Host-Only Ethernet Adapter
- **IP assignment:** Static 10.10.10.12
- **DNS server:** 10.10.10.10
- [Screenshot](/images/NS-CLIENT_VB_Setup.PNG)

### Pre-Join Verification

From the client, I queried the Active Directory DNS SRV record for
`northstar.test`. The lookup returned `ns-dc01.northstar.test` as the
domain controller target.

### Follow-up

The workstation was later joined to `northstar.test`. See
[Workstation domain join](02-domain-join.md) for the procedure and verification.

## 6. Verification
Ping form Windows host to VM NS-DC01 : 10.10.10.10 / successful
Ping from Windows host to VM adapter: 10.10.10.1 / successful

## 7. Issues and Resolutions
<!-- Symptoms, investigation, changes made, and verification -->

## 8. Next Steps
<!-- Remaining prerequisites and workstation domain join -->
- Further safety configuration
- Test with different scenarios
