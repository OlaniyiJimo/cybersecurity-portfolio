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

  using command sudo nmap -sS -sV -p 21,22,80,443 192.168.1.244
![nmap scan](../UFW_firewall_hardening/Screenshots/nmap_scan_before_firewall_rule.png.png)
- UFW was reset, configured to deny all incoming traffic by default, and allow only necessary services.

  Using command: <br/>
sudo ufw --force reset
sudo ufw default deny incoming. <br/>
sudo ufw default allow outgoing <br/>
sudo ufw allow from 192.168.1.128 to any port 22 proto tcp <br/>
sudo ufw allow 80/tcp <br/>
sudo ufw deny 21/tcp <br/>
sudo ufw deny 23/tcp <br/>
sudo ufw deny 3389/tcp <br/>
sudo ufw --force enable <br/>
sudo ufw status verbose | tee ~/ufw_status.txt <br/>

- Nmap was re-run from Kali to validate the new firewall configuration.
 Using command: sudo nmap -sS -sV -p 21,22,80,443 192.168.1.244


## Analysis
- Attack Surface Reduced: Only port 80 (HTTP) remained open to external connections.

- Access Control Enforced: SSH restricted to specific management IP (192.168.1.128).

- Legacy Services Disabled: FTP, Telnet, and RDP ports denied to prevent remote exploitation.

- Firewall Verified: Nmap results confirm filtering behavior for blocked ports.

- Network Security Principle: Least privilege successfully applied to host-level communication.

  

