# Abuse.ch (And its tools)

[Abuse.ch](https://abuse.ch/) is a research project hosted by the Institue for Cybersecurity and Engineering at the Bern University of Applied Sciences in Switzerland. It was developed to identify and track malware and botnets through several operational platforms developed under the project. These platforms are:

* **Malware Bazaar:**  A resource for sharing malware samples.
* **Feodo Tracker:**  A resource used to track botnet command and control (C2) infrastructure linked with Emotet, Dridex and TrickBot.
* **SSL Blacklist:**  A resource for collecting and providing a blocklist for malicious SSL certificates and JA3/JA3s fingerprints.
* **URL Haus:**  A resource for sharing malware distribution sites.
* **Threat Fox:**  A resource for sharing indicators of compromise (IOCs).

Let us look into these platforms individually.

### [MalwareBazaar](https://bazaar.abuse.ch/)

As the name suggests, this project is an all in one malware collection and analysis database. The project supports the following features:

* Malware Samples Upload: Security analysts can upload their malware samples for analysis and build the intelligence database. This can be done through the browser or an API.
* **Malware Hunting:** Hunting for malware samples is possible through setting up alerts to match various elements such as tags, signatures, YARA rules, ClamAV signatures and vendor detection.

![Malware Bazaar Dashboard](https://tryhackme-images.s3.amazonaws.com/user-uploads/5fc2847e1bbebc03aa89fbf2/room-content/55890b3448b3ecf9a55705cd1bd20b08.gif)\


### [FeodoTracker](https://feodotracker.abuse.ch/)

With this project, Abuse.ch is targeting to share intelligence on botnet Command & Control (C\&C) servers associated with Dridex, Emotes (aka Heodo), TrickBot, QakBot and BazarLoader/BazarBackdoor. This is achieved by providing a database of the C\&C servers that security analysts can search through and investigate any suspicious IP addresses they have come across. Additionally, they provide various IP and IOC blocklists and mitigation information to be used to prevent botnet infections.

![Feodo Tracker Dashboard](https://tryhackme-images.s3.amazonaws.com/user-uploads/5fc2847e1bbebc03aa89fbf2/room-content/22e34a463f65fbf7e621a54e347543be.gif)\


### [SSL Blacklist](https://sslbl.abuse.ch/)

Abuse.ch developed this tool to identify and detect malicious SSL connections. From these connections, SSL certificates used by botnet C2 servers would be identified and updated on a denylist that is provided for use. The denylist is also used to identify JA3 fingerprints that would help detect and block malware botnet C2 communications on the TCP layer.

You can browse through the SSL certificates and JA3 fingerprints lists or download them to add to your deny list or threat hunting rulesets.

![SSL Blacklist Dashboard](https://tryhackme-images.s3.amazonaws.com/user-uploads/5fc2847e1bbebc03aa89fbf2/room-content/78bb7ba13a89c203b3ed331df18e2c4d.gif)\


### [URLhaus](https://urlhaus.abuse.ch/)

As the name points out, this tool focuses on sharing malicious URLs used for malware distribution. As an analyst, you can search through the database for domains, URLs, hashes and filetypes that are suspected to be malicious and validate your investigations.

The tool also provides feeds associated with country, AS number and Top Level Domain that an analyst can generate based on specific search needs.

![URLHaus Dashboard](https://tryhackme-images.s3.amazonaws.com/user-uploads/5fc2847e1bbebc03aa89fbf2/room-content/f388122492011e9506410912afd749d1.gif)

### [ThreatFox](https://threatfox.abuse.ch/)

With ThreatFox,  security analysts can search for, share and export indicators of compromise associated with malware. IOCs can be exported in various formats such as MISP events, Suricata IDS Ruleset, Domain Host files, DNS Response Policy Zone, JSON files and CSV files.

![ThreatFox Dashboard](https://tryhackme-images.s3.amazonaws.com/user-uploads/5fc2847e1bbebc03aa89fbf2/room-content/e0fffff3133f4641f85190228990bdfb.gif)
