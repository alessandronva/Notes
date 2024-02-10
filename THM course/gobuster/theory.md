# Theory

Example: gobuster dir --url http://10.129.174.83/ --wordlist /usr/share/wordlists/dirbuster/directory-list-2.3-small.txt -x php,html

\--url --wordlist /directory-local -x exclude directory extensions

The -x option in gobuster is used to specify an extension to use during the directory/file brute force process. For example, if you use -x php, gobuster will only search for files with the .php extension.

Here's an example command using the -x option in gobuster:

bash

gobuster dir -u http://example.com -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x php -t 50

This command tells gobuster to search for directories on http://example.com, using the directory-list-2.3-medium.txt wordlist, and only searching for files with the .php extension. The -t option sets the number of threads to use for the scan.

Now Let’s Enumerate subdomains using gobuster

gobuster vhost -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-5000.txt -u stocker.htb -t 50 --append-domain

The -vhost option in Gobuster allows you to specify the virtual host for which the directory/file enumeration will be carried out. This option is useful when you want to brute-force a web server that is hosting multiple domains or subdomains.

For example, if you have a web server with two virtual hosts, example.com and test.example.com, you can use the -vhost option to specify which virtual host to enumerate:

bash

gobuster dir -u http://example.com -w wordlist.txt -vhost test.example.com

This command will brute-force the test.example.com virtual host instead of the default virtual host example.com.
