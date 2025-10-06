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

- UFW was reset, configured to deny all incoming traffic by default, and allow only necessary services.

  Using command:sudo ufw --force reset
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow from 192.168.1.128 to any port 22 proto tcp
sudo ufw allow 80/tcp
sudo ufw deny 21/tcp
sudo ufw deny 23/tcp
sudo ufw deny 3389/tcp
sudo ufw --force enable
sudo ufw status verbose | tee ~/ufw_status.txt
  
