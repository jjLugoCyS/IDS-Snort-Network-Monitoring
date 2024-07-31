# IDS-Snort-Network-Monitoring

## Objective

Implement network monitoring using IDS and Snort to detect and analyze network threats, enhancing security through continuous monitoring and rapid response.

### Skills Learned

- Proficiency in configuring and deploying Snort.
- Analyze network traffic to identify potential security threats.
- Troubleshooting and resolving configuration issues.
- Interpreting Snort alerts and logs for incident response.
- Improving security posture through monitoring and response.

### Tools Used

- Ubuntu: Linux distrobution
- Snort: An open-source intrusion detection system used for network traffic analysis and threat detection.

## Steps

1. Fire up the Ubuntu machine, open a terminal, and run update/upgrade before installing prerequisite packages.
2. Make a directory for Snort and intall prequisites and dependencies for Snort.
3. After Snort is installed create some rules for analysis. Using ICMP rules, create a local rules file to allow alerts. These tell Snort to send an alert if it detects ICMP traffic.<br>
![rules folder](https://github.com/user-attachments/assets/a8c7abd8-aa55-4407-a139-1ee6780839d0)<br>
*Ref 1: Rules Folder*<br>
![rules file](https://github.com/user-attachments/assets/273c3b85-462a-4e81-8cf2-a7a98ee43b38)<br>
*Ref 2: Rules File*<br>
4. Opening the rule file to create a rule: alert icmp-the alert typr, any any - representing the src address and port, -> any any- destination address and port, and the signature id (always start custom rules at 1 million because numbers 1 - 999,999 are reservec).<br>
![rule](https://github.com/user-attachments/assets/1fd61fe6-e3d5-456e-b3df-18426bfb4133)<br>
*Ref 3: The Rule*<br>
5. When Snort is ran to check the created rule it shows that Snort is now listening in on that traffic using our network adapter. On another machine run a ping to the Ubuntu machine's IP.<br>
![rule works](https://github.com/user-attachments/assets/82837bcd-20a3-4637-a587-c4667ea8c240)<br>
*Ref 4: The Rule Works*<br>
