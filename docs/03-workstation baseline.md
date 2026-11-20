# NorthStar Lab — Baseline Configuration

## 1. Objective
Establish a centrally managed security baseline for NorthStar’s Windows workstation using Group Policy.

## Steps
I created an OU called Lab Workstations and moved the only workstation into it (CLIENT01). [Screenshot](/images/BaselineGPO_1PNG.PNG) 
Then I created a GPO named Workstation Baseline and linked it to the Lab Workstations OU. [Screenshot](/images/BaselineGPO_2PNGPNG)

The following setting were applied to this Baseline GPO

1. Logon timeout
   
|  Item               |  Value                           
|---------------------|------------------------------------------------------------|
| GPO                 | NorthStar - Workstation Baseline                           |
| Linked OU           | Lab Workstations                                           |
| Policy              | Interactive logon: Machine inactivity limit                |
| Value               | 600 seconds                                                |
| Verification        | GPO listed by gpresult; workstation locks after inactivity |

## Verification
Ensured that the GP has been applied to the workstation. [Screenshot](/images/BaselineGPO_4PNG.PNG) 
