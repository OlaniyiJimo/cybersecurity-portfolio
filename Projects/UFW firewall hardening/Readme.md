## Host-Based Firewall Hardening with UFW and Nmap Verification

**Objective:* This project demonstrates Linux host hardening using the **UFW (Uncomplicated Firewall)** on an Ubuntu virtual machine.  
The objective was to reduce the system’s attack surface** by restricting network access to essential services only, applying **least privilege** principles, and verifying the results using **Nmap** from a Kali attacker machine.

## Tools Used
- **Target System:** Ubuntu 22.04 LTS VM (192.168.1.244)
- **Attacker System:**  Kali Linux VM (127.0.1.1) 
- **Network Mode:**  Host-Only Adapter (same subnet) 
- **Firewall Tool:** UFW (Uncomplicated Firewall) 
- **Validation Tool:** Nmap 

## Procedure summary
- Nmap was run from the Kali attacker to identify open services before implementing any firewall rules.
  
