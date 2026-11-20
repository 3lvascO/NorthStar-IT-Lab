# NorthStar Lab — Baseline Configuration

## 1. Objective
Establish a centrally managed security baseline for NorthStar’s Windows workstation using Group Policy.

|  Item               |  Value                           
|---------------------|------------------------------------------------------------|
| GPO                 | NorthStar - Workstation Baseline                           |
| Linked OU           | Lab Workstations                                           |
| Policy              | Interactive logon: Machine inactivity limit                |
| Value               | 600 seconds                                                |
| Verification        | GPO listed by gpresult; workstation locks after inactivity |
| Screenshots         | [Image](BaselineGPO_4PNG)
