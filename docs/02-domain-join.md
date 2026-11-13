# NorthStar Lab — Workstation Domain Join

## Objective

Join the Windows client VM to the `northstar.test` Active Directory domain
and verify its domain membership after restarting.

## Environment

- **Workstation:** NS-CLIENT01
- **Windows edition:** Windows 11 Pro              
- **Domain:** `northstar.test`
- **Domain controller:** `ns-dc01.northstar.test`

See [Initial lab setup](01-initial-setup.md) for the VM and network configuration.

## Pre-Join DNS Check

From the client VM, I queried the Active Directory DNS SRV record to verify
that the workstation could locate the domain controller.

```powershell
Resolve-DnsName -Name "_ldap._tcp.dc._msdcs.northstar.test" -Type SRV -DnsOnly
```

**Result:** The lookup returned `ns-dc01.northstar.test` as the target.

## Domain Join Procedure

1. Signed in to the workstation with a local administrator account.
2. Opened System Properties (`sysdm.cpl`) and selected **Computer Name → Change**.
3. Selected **Domain**, entered `northstar.test`, and supplied authorized
   domain credentials when prompted.
4. Restarted the workstation after Windows confirmed the join.

## Verification

After restarting, I verified domain membership using [System Properties or
PowerShell—use whichever you checked].

- **Domain:** `northstar.test`
- **Evidence:** [Screenshot showing the domain, or command output showing
  `PartOfDomain : True`]

## Follow-Up: Standard Domain User Sign-In

**Status:** [Pending / Verified]

[After testing, record whether the standard domain user reached the desktop
and include the output of `whoami`.]
