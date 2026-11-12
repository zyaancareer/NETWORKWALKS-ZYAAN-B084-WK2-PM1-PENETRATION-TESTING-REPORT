# PENETRATION TESTING REPORT
  FOOTPRINTING & NETWORK SCANNING PHASES </br>
  W2-PM-FINAL | CYBERSECURITY | NETWORKWALKS

| Pentester Name	| Zyaan Makda |
|----------------- | ------------ |
| Program/Batch	| B084-Networkwalks |
| Date |	10 November 2026
| Modules completed |	W2-PM1 (Multiple Kali Tools) W2-PM1 (Zenmap Scanning) |
| Client/Target |	1.	Networkwalks (secured written permissions already)</br>2.	My own local LAN Network |
| Permission secured from client? |	Yes |
| Phases covered |	Phase 1: Reconnaissance & Footprinting</br>Phase 2: Scanning & Network Discovery</br>Phase 3-5: In Progress |


# 1.	Liability Disclaimer
This exercise was conducted strictly for educational purposes on a network for which authorisation was obtained. All tools and techniques demonstrated are intended for ethical cybersecurity training and legitimate network assessments. No unauthorised access, exploitation or disruption of network devices was intended.

# 2.	Introduction
This report documents a practical exercise in network reconnaissance and host discovery conducted as part of my cybersecurity training. The exercise involved identifying local network configurations, understanding IP addressing and subnetting, and using tools such as Windows Command Prompt, Kali Linux and Zenmap to perform a Ping Scan and identify active devices on a network. The report outlines the procedures followed, tools used and results obtained, demonstrating an understanding of basic network discovery techniques.



# 3.	Tools Used
The table below lists each tool used in this report and its purpose.
| Tool | Purpose |
| ----- | ------ |
| Kali Linux & Windows | Operating systems used for reconnaissance. |
| WHOIS	| Find domain registration details (owner, dates, name servers). |
| whatweb |	Fingerprint web technologies (server, CMS, plugins, IP) |
| nslookup | Resolve the domain name to its IP address using DNS. |
| curl -I | Read the HTTP response headers of the website. |
| wafw00f | Detect whether a Web Application Firewall protects the site. |
| dnsrecon | Enumerate all DNS records (NS, MX, SPF, TXT, SRV). |
| Zenmap (Nmap GUI) |	Scan the local subnet to find live hosts, IPs and MAC addresses. |
| Windows CMD | Local IP and MAC address identification. |


# 4.	Activities Performed
# 4.1	Footprinting & Reconnaissance

I performed reconnaissance against the networks.com domain using six Linux tools: WHOIS, Nslookup, Curl, Wafw00f and DNSRecon. Each tool was used to collect a different type of information about the target.

I first used WHOIS to obtain the publicly available domain registration information and the name of its servers.  The results provided information about the domain registration and hosting infrastructure.

I then used WhatWeb to determine which technologies the website was using. WordPress 7.1.4 and WordPress Download Manager 3.3.76 were found in the results, along with further data exposed by the website.

I was able to connect the domain name to its IP address using Nslookup. 192.232.216.135 was found in the given result.

I examined the HTTP response headers using Curl and the -I iption. This revealed the WordPress REST API endpoint /wp-json/ and offered more details about the web application.

I then used Wafw00f to check if the website was protected by a Web Application Firewall. ModSecurity (SpiderLabs) was found in the outcome. 
Lastly, I enumerated DNS records using DNSRecon. Name servers, mail servers, SPF/TXT records, and DNS software information were all included in the results.

# 4.2	Network Scanning with Zenmap
After identifying the local Wi-Fi network configuration using Windows Command Prompt, Zenmap was launched to perform network discovery. The IPv4 subnet range was entered into the Target field, and the Ping Scan profile was selected to identify active devices on the network. 
Once the scan was completed, the results were analysed to identify responding hosts, their IP addresses and, where available, their MAC addresses.
 I found four live hosts: 
•	192.168.18.241
•	192.168.18.1
•	192.168.18.200
•	192.168.18.236
The results also included for MAC addresses.
After completing the scan, I opened the Topology section in Zenmap, enabled the legend and saved the network topology in PDF format as required by the practical task.






# 5.	Risk Analysis / Impact
Based on the information collected during the footprinting and network scanning activities, I identified the following potential risks.

| #	| Risk/Finding	| Evidence/Observation | Potential Impact | Risk Level |
| - | ------------ | --------------------- | ---------------- | ----------- |
| 1	| Exposure of domain registration information |	WHOIS revealed publicly available domain registration details | Attackers could use this information to identify domain ownership and infrastructure details. |	Medium |
| 2	| Website technology exposure |	WhatWeb identified technologies and frameworks used by the target website |	Attackers could identify outdated software or potential vulnerabilities. | Medium |
| 3	| Public information exposure |	Search engine results revealed information associated with the target. |	Information could be misused for social engineering or targeted attacks.	| Medium |
| 4	| Network device discovery	| Zenmap Ping Scan identified responding hosts within the scanned network range.	| Attackers could use discovered IP addresses to map the network and identify potential targets.	| Medium |
| 5 |	MAC address exposure |	MAC addresses may be displayed for discovered devices when available. | Device identifiers could assist with network profiling and device identification. | Low |
| 6	| Unauthorised network scanning	| Network scanning tools can generate detectable traffic when used against networks without permission. |	Could trigger security alerts, violate network policies or result in legal consequences. | High |
| 7	| Excessive network scanning	| Repeated or aggressive scans can generate additional network traffic.	| Could affect network performance or trigger intrusion detection systems.	| Medium |


The risks shown above are observations from the footprinting and scanning excercises, not confirmed vulnerabilities. Information gathering and host discovery were the main tasks of the practical exercises. These two modules did not include any exploitation or vulnerability validation.
Consequently, the existence of data like an IP address, DNS record, or software version does not automatically indicate that the system is vulnerable. Any real vulnerability would need to be confirmed by additional authorised security testing.

# 6.	Recommendations
Based on the observations from these activities, I recommend the following improvements:

1.	**Domain Privacy:** Enable WHOIS privacy protection where supported by the domain registrar to reduce the amount of personal registration information publicly accessible.
2.	**Website Security:** Keep website software, plugins, frameworks and server components updated to reduce exposure to known vulnerabilities.
3.	**Information Exposure:** Review publicly accessible information and remove unnecessary sensitive details to minimise information that attackers could use for reconnaissance.
4.	**Network Security:** Use a firewall to restrict unnecessary inbound and outbound connections and help prevent unauthorised network access.
5.	**Device Security:** Keep devices updated and disable unused network services and ports to reduce potential entry points for attackers.
6.	**Network Monitoring:** Monitor network traffic and use intrusion detection or prevention systems where appropriate to identify suspicious activity.
7.	 **Wi-Fi Security:** Use WPA2-AES or WPA3 encryption with a strong, unique Wi-Fi password to protect wireless communications.
8.	**Access Control:** Use strong passwords and enable multi-factor authentication (MFA) where available to reduce the risk of compromised accounts.
9.	**Network Scanning:** Conduct network scans periodically and only with appropriate authorisation to identify active devices and potential security weaknesses.
10.	**Data Backups:** Maintain regular backups of important data and verify that they can be restored to minimise data loss following a security incident.

# 7. Conclusion
This project provided practical experience in footprinting and network scanning using tools such as WHOIS, WhatWeb, Kali Linux and Zenmap. Through these activities, I gained a better understanding of how publicly available information can be collected, how website technologies can be identified and how active devices can be discovered on a local network. The risk analysis highlighted potential security concerns associated with information exposure and network reconnaissance, while the recommended security improvements demonstrated ways to minimise these risks. 
Overall, this exercise strengthened my understanding of fundamental cybersecurity concepts and the importance of responsible, authorised security testing in identifying and reducing potential vulnerabilities.

# 8. Evidences Collected
*Screenshots collected as evidence during the activities (stored in the `screenshots/` folder):*
