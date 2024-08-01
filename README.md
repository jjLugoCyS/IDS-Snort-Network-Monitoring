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
5. When Snort is ran to check the created rule it shows that Snort is now listening in on that traffic using our network adapter. On another machine run a ping to the Ubuntu machine's IP. Snort starts up with rules network interface and alerts format.<br>
![snort validation](https://github.com/user-attachments/assets/55fb2c04-b332-4ea8-8991-1ece46d8fb26)<br>
*Ref 4: Snort validation*<br>
![snort start up with rules network interface and alerts format-done](https://github.com/user-attachments/assets/fe0b6b1c-8b9c-41ac-983e-ea57ea441881)
*Ref 5: Snort spun up with rules*
![snort listening in on network adapter](https://github.com/user-attachments/assets/d43074fa-5be4-4431-9e71-5d05e42c71f4)<br>
*Ref 6: Snort listening on network adapter*<br>
![rule works](https://github.com/user-attachments/assets/82837bcd-20a3-4637-a587-c4667ea8c240)<br>
*Ref 7: The Rule Works*<br>
6.Turn off recieve-offload automatically with every boot using a service.<br>
![rules folder](https://github.com/user-attachments/assets/a8c7abd8-aa55-4407-a139-1ee6780839d0)<br>
*Ref 8: Rules offload *<br>
7. Run Snort and point it toward the Snort configuration file.<br>
![running snort and pointing to rules file](https://github.com/user-attachments/assets/a94df377-33da-4975-84b1-6a8e9c2f6806)<br>
*Ref 9: Point Snort to Config file*<br>
8. Now open the default Snort configuration file.<br>
![defualt config](https://github.com/user-attachments/assets/28293f44-14f2-43ce-94ce-33f6c4988a27)<br>
*Ref 10: Default config*<br>
9.Look for a field called IPS, we can find this by pressing ctrl+W and typing "ips" into the search. Locate "enable_builtin_rules" and enable them by uncommenting that line. To specifiy where your rules are located, on a new line above "variables" enter "include =" with the path to a rules file.<br>
![enable rules and specify where they are located](https://github.com/user-attachments/assets/98033c3a-64a5-46e5-b5f5-933fd4cbabf3)<br>
*Ref 11: snort.lua config file*<br>
10. 
