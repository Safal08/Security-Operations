# ASPX Reverse Shell Was Planted via SMB

Activity observed in the network capture and explains how an attacker uploaded and executed a malicious ASPX reverse shell using SMB and HTTP.

# 1 SMB Share Access

The attacker first connected to shares on the target server using SMB:
IPC$ – administrative share used for management.
Documents – the share where the malicious file was placed.

This is visible in the capture as Tree Connect Requests.

# 2 File Upload via SMB

Once connected to the Documents share, the attacker sent a Create Request to make a new file: shell.aspx, sent a Write Request to upload the malicious ASPX content

After these operations, the file Documents/shell.aspx existed on the server.

# 3 Execute via Web Server

The attacker then accessed the file through the web server (IIS) using:
http://10.0.2.15/Documents/shell.aspx
This caused the server to run the malicious code embedded in the ASPX file.

# 4 Reverse Shell Connection

When executed, the malicious ASPX page forced the server to initiate an outbound TCP connection to the attacker's machine, creating a reverse shell session.

**Network Traffic Analysis using Wireshark & PCAP**
This project demonstrates a detailed analysis of network traffic using Wireshark, focusing on identifying suspicious or malicious activity within a PCAP file. The goal is to simulate tasks typically performed by a SOC (Security Operations Center) analyst, such as detecting anomalies, filtering malicious traffic, and reporting findings.

**Takeaway**

The attacker used SMB to plant the malicious ASPX file and then triggered it via HTTP, resulting in a reverse shell.
If SMB shares and web directories aren’t tightly controlled, attackers can upload web-executable files and gain remote access.
