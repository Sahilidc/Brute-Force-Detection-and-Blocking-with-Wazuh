# Brute-Force Detection and Blocking with Wazuh
This project demonstrates the detection and blocking of brute-force attempts using Wazuh. The setup includes configuring Wazuh to detect SSH brute-force attacks and automatically block the attacking IP using active response mechanisms.

### UML Diagram
Refer to the UML diagram to understand the overall flow of events:

![Untitled Diagram drawio (1)](https://github.com/user-attachments/assets/a8d500a8-da70-4c68-9a8f-ce6ce4babc2d)

Brute-force Attempt: A hacker attempts an SSH brute-force attack.
Event Detection: The Wazuh agent detects the attack and sends events to the Wazuh manager.
Active Response Trigger: The Wazuh manager triggers an active response rule based on the detected event.
Blocking Action: The active response is executed, blocking the attacker's IP and generating logs.

### Screenshots
##### Active Response Rule: Configuration of the active response rule for SSH brute-force detection.
![rule](https://github.com/user-attachments/assets/f46c2738-a65e-4ec7-a79f-2add088ba9fd)

##### Rule 5763 Significance: Explanation of the specific rule used for SSH brute-force detection.
![rule significance](https://github.com/user-attachments/assets/ac1239e1-ff5a-468f-baf1-53c979804b8f)

##### SSH Login Trial Logs: Logs showing the SSH login attempts detected by Wazuh.SSH Login Trial Logs: Logs showing the SSH login attempts detected by Wazuh.
![dropped](https://github.com/user-attachments/assets/9a7a2864-de8e-486c-a1e4-c1023afeb207)

##### Kali Linux Brute-force Attempt: Screenshot of the brute-force attack conducted using Hydra.
![atatck](https://github.com/user-attachments/assets/9e7ac99e-a993-4163-ad73-405c89ad3791)

### Setup and Configuration
##### Prerequisites

- ###### Wazuh Manager deployed on Ubuntu.
- ###### Wazuh Agent configured on the machine where brute-force attempts will be detected.Wazuh Agent configured on the machine where brute-force attempts will be detected.

##### Step 1: Configure Detection Rule
Add or modify detection rules in the Wazuh manager to detect brute-force attempts. Ensure that Rule 5763 is enabled to detect SSH brute-force attempts.

```
nano /var/ossec/etc/rules/sshd_rules.xml

```
##### Step 2: Configure Active Response
```
nano /var/ossec/etc/ossec.conf

```
- Add an <active-response> entry for SSH brute-force attempts, specifying the command to block the attacker's IP.

#### Viewing Events and Active Responses
- Log into the Wazuh manager interface.

- Check the "Active Responses" and "Security Events" sections for details on detected brute-force attempts and blocked IPs.
