# John the ripper basics

{% code overflow="wrap" fullWidth="true" %}
```c
To crack a password hash using default modes:
john hash.txt

To specify a specific cracking mode (e.g., MD5):
john --format=raw-MD5 hash.txt

To specify a wordlist for cracking:
john --wordlist=wordlist.txt hash.txt

To use incremental mode:
john --incremental hash.txt

To specify a specific incremental mode (e.g., digits):
john --incremental=digits hash.txt

To specify rules for mangling words:
john --wordlist=wordlist.txt --rules hash.txt

To show cracked passwords:
john --show hash.txt

To continue an interrupted cracking session:
john --restore

To specify a hash manually:
echo "hash_value" > custom_hash.txt
john custom_hash.txt

To specify multiple hashes from a file:
john --fork=4 --wordlist=wordlist.txt --format=NT hashfile.txt

Remember to replace hash.txt with the path to your hash file and wordlist.txt with the path to your wordlist file.

Feel free to adjust the options and parameters according to your specific needs and the type of hashes you are attempting to crack. Make sure to use John the Ripper responsibly and only on systems and accounts that you have explicit permission to test.
```
{% endcode %}
