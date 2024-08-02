# IDS-Snort-Network-Monitoring

## Objective

Implement network monitoring using IDS and Snort to detect and analyze network threats, enhancing security through continuous monitoring and rapid response.

### Skills Learned

- Proficiency in configuring and deploying Snort.
- Analyzing network traffic to identify potential security threats.
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
4. Open the rule file to create a rule: alert icmp - the alert type, any any - representing the source address and port, -> any any - destination address and port, and the signature id (always start custom rules at 1 million because numbers 1 - 999,999 are reserved).<br<
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
![snort default configs-done](https://github.com/user-attachments/assets/59ce79e0-c322-462b-8499-cfc05b7a8835)<br>
*Ref 11: Default config file*<br>
10. Look for a field called IPS, we can find this by pressing ctrl+W and typing "ips" into the search. Locate "enable_builtin_rules" and enable them by uncommenting that line. To specifiy where your rules are located, on a new line above "variables" enter "include =" with the path to a rules file.<br>
![enable rules and specify where they are located](https://github.com/user-attachments/assets/98033c3a-64a5-46e5-b5f5-933fd4cbabf3)<br>
*Ref 12: snort.lua config file*<br>
11. Expand the ruleset and download pulledpork3 for free rulesets.<br>
![install pulledpork](https://github.com/user-attachments/assets/6d6ee1a4-a382-4004-984c-563f54bb3f75)<br>
*Ref 13: Pulledpork installation*<br>
12. Mext we open the pulledpork configuration file.<br>
![open config file](https://github.com/user-attachments/assets/048cc259-20e0-404f-9a93-aa909cd405f5)<br>
*Ref 14: Pulledpork.conf*<br>
13. In the configuration file locate "registered_ruleset" and change it to "true".<br>
![select registered ruleset by changing to true-done](https://github.com/user-attachments/assets/64c97f42-84b4-4815-8120-1655e4c052a1)<br>
*Ref 15: Registered_ruleset*<br>
14. Point pulledpork3 to the pulledpork configuration file.<br>
![point to pp3 and config file](https://github.com/user-attachments/assets/c29a816a-9049-4833-99ec-0fc1d4362d39)<br>
*Ref 16: Point PP3 to PP config*<br> 
15. Head back to Snort configuration files and change IPS to point it to pulledpork rules.
![change include to pp rules file](https://github.com/user-attachments/assets/5af668b3-266d-4f3c-8620-b51fcc671c6b)<br>
*Ref 17: Now pointing to PP rules file*
17. Run Snort pointed to the new configuration file and the specified rules.<br>
![running snort without rule path](https://github.com/user-attachments/assets/9885cb88-6113-47c1-a4ee-9fb6a77fd7ec)<br>
*Ref 18: Run Snort without rule path*<br>
![run snort pointed to config and specified rules path](https://github.com/user-attachments/assets/eadf524e-ecb9-425f-9631-6174c7fe553a)<br>
*Ref 18: Snort pointed to new rules*
![pp3 running succesful](https://github.com/user-attachments/assets/0e838b41-4b7a-4545-a110-e34c059d56f7)<br>
*Ref 19: Success!*
19. After we have doanloaded a test pcap we can run snort and generate some output. Run Snort on the malicious pcap and display only signatures and alerts.<br>
![running snort on malicious pcap and displaying only sigs or alerts](https://github.com/user-attachments/assets/fb5f012a-783f-4686-b8d7-c0bc8fbea766)<br>
*Ref 20: Pcap output command*
![pcap output](https://github.com/user-attachments/assets/8979139b-c816-42b5-a717-786e8a8dcd7e)<br>
*Ref 21: Pcap output*<br>
20. With the amount of alerts produced with this pcap we should output it to a file. We do this by adding "> pcap-signature.txt".<br>
![output to a file](https://github.com/user-attachments/assets/eea3e764-2d22-4ae7-8650-fe416d824923)<br>
*Ref 22: Out to a file*<br>
21. Clean up the out put by using the cut command to present information in an easier to read format.<br>
![more presentable by cutting information out](https://github.com/user-attachments/assets/04c679ef-abed-45c2-aeb8-f085784ec89e)<br>
*Ref 23: Command for presentation*<br>
22. To further make it look presentable use sort and uniq to de duplicate and list alerts by amount.<br>
![final presentation sort](https://github.com/user-attachments/assets/9f532648-ea7d-4a7a-a8db-2d40a9136ba6)<br>
*Ref 24: Final presentation*
23. Something interesting being spotted in the pcap needs further investigation. Use "grep -i malware pcap-signatures.txt" to isolate and view the alert.<br>
![malware info](https://github.com/user-attachments/assets/757df202-9976-42fd-86f4-c5d2a12f8219)<br>
*Ref 25: Isolated malware info*
24. Now we can take a look at the IP that is in the pcap and run it through an analyzer like Wireshark and analyze it.
