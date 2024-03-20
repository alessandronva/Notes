# Email analysis PhishTool

Before going into the task, click the Start Machine button to start the attached VM and open it in Split View. You will be using the same machine through tasks 7 and 8.

This task will introduce you to a tool, PhishTool, that you would add to your toolkit of email analysis tools. Please take note that it would not be necessary to use it to complete the task; however, the principles learnt would be helpful.

### Email Phishing

Email phishing is one of the main precursors of any cyber attack. Unsuspecting users get duped into opening and accessing malicious files and links sent to them by email, as they appear to be legitimate. As a result, adversaries infect their victims’ systems with malware, harvesting their credentials and personal data and performing other actions such as financial fraud or conducting ransomware attacks.

For more information and content on phishing, check out these rooms:

* [Phishing Emails 1](https://tryhackme.com/room/phishingemails1tryoe)
* [Phishing Emails 2](https://tryhackme.com/room/phishingemails2rytmuv)
* [Phishing Emails 3](https://tryhackme.com/room/phishingemails3tryoe)
* [Phishing Emails 4](https://tryhackme.com/room/phishingemails4gkxh)
* [Phishing Emails 5](https://tryhackme.com/room/phishingemails5fgjlzxc)

[PhishTool](https://www.phishtool.com/) seeks to elevate the perception of phishing as a severe form of attack and provide a responsive means of email security. Through email analysis, security analysts can uncover email IOCs, prevent breaches and provide forensic reports that could be used in phishing containment and training engagements.

PhishTool has two accessible versions: Community and Enterprise. We shall mainly focus on the Community version and the core features in this task. Sign up for an account via this [link](https://app.phishtool.com/sign-up/community) to use the tool.

The core features include:

* **Perform email analysis:** PhishTool retrieves metadata from phishing emails and provides analysts with the relevant explanations and capabilities to follow the email’s actions, attachments, and URLs to triage the situation.
* **Heuristic intelligence:** OSINT is baked into the tool to provide analysts with the intelligence needed to stay ahead of persistent attacks and understand what TTPs were used to evade security controls and allow the adversary to social engineer a target.
* **Classification and reporting:** Phishing email classifications are conducted to allow analysts to take action quickly. Additionally, reports can be generated to provide a forensic record that can be shared.

Additional features are available on the Enterprise version:

* Manage user-reported phishing events.
* Report phishing email findings back to users and keep them engaged in the process.
* Email stack integration with Microsoft 365 and Google Workspace.

We are presented with an upload file screen from the Analysis tab on login. Here, we submit our email for analysis in the stated file formats. Other tabs include:\


* **History:** Lists all submissions made with their resolutions.
* **In-tray:** An Enterprise feature used to receive and process phish reports posted by team members through integrating Google Workspace and Microsoft 365.

![PhishTool Dashboard](https://tryhackme-images.s3.amazonaws.com/user-uploads/5fc2847e1bbebc03aa89fbf2/room-content/4c5d66d92d6aeb83d67961be5239842d.png)\


#### Analysis Tab

Once uploaded, we are presented with the details of our email for a more in-depth look. Here, we have the following tabs:

* **Headers:** Provides the routing information of the email, such as source and destination email addresses, Originating IP and DNS addresses and Timestamp.
* **Received Lines:** Details on the email traversal process across various SMTP servers for tracing purposes.
* **X-headers:** These are extension headers added by the recipient mailbox to provide additional information about the email.
* **Security:** Details on email security frameworks and policies such as Sender Policy Framework (SPF), DomainKeys Identified Mail (DKIM) and Domain-based Message Authentication, Reporting and Conformance (DMARC).
* **Attachments:** Lists any file attachments found in the email.
* **Message URLs:** Associated external URLs found in the email will be found here.

We can further perform lookups and flag indicators as malicious from these options. On the right-hand side of the screen, we are presented with the Plaintext and Source details of the email.

![Email analysis](https://tryhackme-images.s3.amazonaws.com/user-uploads/5fc2847e1bbebc03aa89fbf2/room-content/03364f3a4fb2177cce13abc3b181bca9.gif)\


Above the Plaintext section, we have a Resolve checkmark. Here, we get to perform the resolution of our analysis by classifying the email, setting up flagged artefacts and setting the classification codes. Once the email has been classified, the details will appear on the Resolution tab on the analysis of the email.

![Email investigation resolution](https://tryhackme-images.s3.amazonaws.com/user-uploads/5fc2847e1bbebc03aa89fbf2/room-content/b13d63d0c2fe177085a1b487efb4065e.gif)\


You can now add PhishTool to your list of email analysis tools.
