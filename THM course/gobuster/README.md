# Gobuster

* Scan to find directories gobuster dir -u precious.htb -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -t 50
* Scan to find subdomains gobuster vhost -w /opt/useful/SecLists/Discovery/DNS/subdomains-top1million-5000.txt -u precious.htb -t 50 --app end-domain

With this it could be beneficial to obtain useful output.

IMPORTANT:

Add k lower case option if its using deprecated ssl certificates:

\-k
