Bruteforce DNS (Domain Name System) enumeration is the method of trying tens, hundreds, thousands or even millions of different possible subdomains from a pre-defined list of commonly used subdomains. Because this method requires many requests, we automate it with tools to make the process quicker. In this instance, we are using a tool called dnsrecon to perform this. Click the "View Site" button to open the static site, press the "Run DNSrecon Request" button to start the simulation, and then answer the question below.

Example 

user@thm:~$ dnsrecon -t brt -d acmeitsupport.thm  
[*] No file was specified with domains to check.  
[*] Using file provided with tool: /usr/share/dnsrecon/namelist.txt  

[*]     A api.acmeitsupport.thm 10.10.10.10  

[*]     A www.acmeitsupport.thm 10.10.10.10  

[+] 2 Record Found  

user@thm:~$

**Automation Using Sublist3r**

To speed up the process of OSINT subdomain discovery, we can automate the above methods with the help of tools like [Sublist3r](https://github.com/aboul3la/Sublist3r), click the "View Site" button to open up the static site and run the sublist3r simulation to discover a new subdomain that will help answer the question below.

Example:

user@thm:~$ ./sublist3r.py -d acmeitsupport.thm  
  
          ____        _     _ _     _   _____  
         / ___| _   _| |__ | (_)___| |_|___ / _ __  
         \___ \| | | | '_ \| | / __| __| |_ \| '__|  
          ___) | |_| | |_) | | \__ \ |_ ___) | |  
         |____/ \__,_|_.__/|_|_|___/\__|____/|_|  
  
         # Coded By Ahmed Aboul-Ela - @aboul3la  
  
[-] Enumerating subdomains now for acmeitsupport.thm  

[-] Searching now in Baidu..  

[-] Searching now in Yahoo..  

[-] Searching now in Google..  

[-] Searching now in Bing..  

[-] Searching now in Ask..  

[-] Searching now in Netcraft..  

[-] Searching now in Virustotal..  

[-] Searching now in ThreatCrowd..  

[-] Searching now in SSL Certificates..  

[-] Searching now in PassiveDNS..  

[-] Searching now in Virustotal..  
[-] Total Unique Subdomains Found: 2  

web55.acmeitsupport.thm  

www.acmeitsupport.thm  

user@thm:~$