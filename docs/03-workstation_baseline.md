# NorthStar Lab — Baseline Configuration

## 1. Objective
Establish a centrally managed security baseline for NorthStar’s Windows workstation using Group Policy.

## Steps
- Created an OU called Lab Workstations and moved the only workstation into it (CLIENT01). [Screenshot](/images/BaselineGPO_1PNG.PNG) 
- Created a GPO named Workstation Baseline and linked it to the Lab Workstations OU. [Screenshot](/images/BaselineGPO_2PNGPNG)

The following setting were applied to this Baseline GPO

1. Logon timeout
   
|  Item               |  Value                           
|---------------------|------------------------------------------------------------|
| GPO                 | NorthStar - Workstation Baseline                           |
| Linked OU           | Lab Workstations                                           |
| Policy              | Interactive logon: Machine inactivity limit                |
| Value               | 600 seconds                                                |
| Verification        | GPO listed by gpresult; workstation locks after inactivity |

2. Firewall Configuration
   
|  Item               |  Value                           
|---------------------|------------------------------------------------------------|
| GPO                 | NorthStar - Workstation Baseline                           |
| Linked OU           | Lab Workstations                                           |
| Security Setting    | WD Firewall                                                |
| Value               | inbound(blocked)/outbount(allowed) defaults, logging enabled                        |
| Verification        | Get-NetFirewallProfile shows rules [values](/images/BaselineGPO_Firewall_PS.PNG)                  |

Allowed remote management traffic from domain's ip address to expedite configuration changes effective time (no "gpudate" necessary at individual workstations fo updates to take effect).

3. Account Password and Lockout Policy
   Configured domain-user password and lockout policies at the domain level, separately from the workstation baseline GPO.

    Lockout Policy

   | Policy | Value |
   |---|---|
   | Account lockout threshold | **10 failed attempts** |
   | Account lockout duration | **15 minutes** |
   | Reset account lockout counter after | **15 minutes** |

   Password Policy

   | Policy | What it controls |  configuration |
   |---|---|---|
   | **Minimum password length** | Shortest password allowed | **15+ characters** where supported |
   | **Enforce password history** | Prevents reusing previous passwords | Remember **24 passwords** |
   | **Minimum password age** | Prevents quickly cycling passwords to bypass history | **1 day** |
   | **Password complexity** | Requires a mix of character categories and restricts account-name use | Commonly enabled in traditional AD environments |
   | **Maximum password age** | Forces periodic password changes | Historically 60–90 days; current guidance advises against routine expiration |
   | **Reversible encryption** | Stores passwords in a recoverable form for certain legacy authentication methods | **Disabled** |

   [Screenshot](/images/BaselineGPO_Pass.PNG)
   
## Verification
Ensured that the GP has been applied to the workstation. [Screenshot](/images/BaselineGPO_4PNG.PNG) 
