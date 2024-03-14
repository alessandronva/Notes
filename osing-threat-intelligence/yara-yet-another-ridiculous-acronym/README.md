# Yara (Yet Another Ridiculous Acronym)

All about Yara _"The pattern matching swiss knife for malware researchers (and everyone else)" (_[_Virustotal., 2020_](https://virustotal.github.io/yara/)_)_\
With such a fitting quote, Yara can identify information based on both binary and textual patterns, such as hexadecimal and strings contained within a file.\
Rules are used to label these patterns. For example, Yara rules are frequently written to determine if a file is malicious or not, based upon the features - or patterns - it presents. Strings are a fundamental component of programming languages. Applications use strings to store data such as text.\
For example, the code snippet below prints "Hello World" in Python. The text "Hello World" would be stored as a string.

```python
print("Hello World!")
```

\
We could write a Yara rule to search for "hello world" in every program on our operating system if we would like. \
Why does Malware use Strings?Malware, just like our "Hello World" application, uses strings to store textual data. Here are a few examples of the data that various malware types store within strings:\


| Type       | Data                                                                                                                                  | Description                                             |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------- |
| Ransomware | <p><a href="https://www.blockchain.com/btc/address/12t9YDPgwueZ9NyMgw519p7AA8isjr6SMw">12t9YDPgwueZ9NyMgw519p7AA8isjr6SMw</a><br></p> | <p>Bitcoin Wallet for ransom payments<br></p>           |
| Botnet     | <p>12.34.56.7<br></p>                                                                                                                 | The IP address of the Command and Control (C\&C) server |

\
