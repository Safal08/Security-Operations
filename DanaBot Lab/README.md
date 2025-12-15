**PCAP Analysis Report**

Reference: https://cyberdefenders.org/blueteam-ctf-challenges/danabot/#

Overview

This analysis focuses on a captured PCAP file involving malicious network activity targeting an internal host.

**Network Details**

Victim IP: 10.2.14.101

Attacker IP: 62.173.142.148

Source Port: 49786

Destination Port: 80

**Malicious Artifacts**

login.php

Contains an obfuscated JavaScript payload.

Used as an initial delivery mechanism.

resources.dll

Downloaded and executed as part of the attack chain.

**Attack Technique**

The attacker leveraged the Windows LOLbin (Living Off the Land Binary) wscript.exe to execute the malicious script, allowing execution without dropping obvious executable files and helping evade detection.

**Takeaway**

Abuse of LOLbins (wscript.exe) to execute malicious files is an effective evasion technique and should be closely monitored in enterprise environments.
