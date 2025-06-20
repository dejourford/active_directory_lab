## Active Directory Lab


### Lab Network Topology: Active Directory & Internal Web Server

```
                [ Domain Controller ]
                     DC-01
                   (AD + DNS)
                        |
     ---------------------------------------------
     |                                           |
[ Employee Machine ]                    [ Employee Machine ]
     Win10-01                                Win10-02
 (Logged in with AD users)             (Optional clone)
                        |
                        |
           [ Ubuntu Machine (Vulnerable Server) ]
                      Ubuntu-01
              (DVWA, Juice Shop, etc.)
```

## Scenario

You have been tasked with setting up a small enterprise network for a new startup, Ford's Trucking Company, and its first few employees. Your job includes:

- Creating an **Active Directory Domain**
- Provisioning **employee workstations**
- Deploying an **internal company server** running a vulnerable web application (for internal use or security testing)

## Requirements

1. **Group Policy Organizational Units (OUs):**
   - `IT` — Full privileges (Domain Admins, help desk, etc.)
   - `Developers` — Moderate privileges (dev tools, limited admin access)
   - `Sales` — Least privileges (standard user access)

2. **Users and Machines:**
   - Each employee will be assigned a domain account
   - Each user will log into a domain-joined Windows machine
   - There will be one **internal Ubuntu server** hosting a vulnerable application (e.g., DVWA or Juice Shop)

3. **Networking:**
   - All machines must be on the same **Host-Only VirtualBox network**
   - The Domain Controller handles **DNS and AD authentication**
   - The Ubuntu machine is **not domain-joined**, but reachable internally

## What I Did

1. `Created a virtual machine, setup network information, installed Active Directory and DNS, and escalated to Domain Controller for the Ford's Trucking Company.` 
2. `Logged back in as Administrator now under the Ford's Trucking Company domain and created company employees.`


## Lessons Learned
- Rebooting system fixes weird issues such as the virtual machine not detecting user input
- Admin password needs to meet certain criteria (probably chars,nums, and letters)
- The Domain Controller needs to be setup using the same IP as the virtual server and point to itself for DNS looping back.
- After manually adding IP, restart system to apply updates. use "ipconfig" to verify changes
- When a user is created, admin creates the password but there's an option to prompt the user to reset their password once they log in to the new account for the first time.

## Planned Improvements
