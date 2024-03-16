# Basic yara rules

Guides to create YARA rules:\
[https://www.bsk-consulting.de/2015/02/16/write-simple-sound-yara-rules/\
https://www.bsk-consulting.de/2015/10/17/how-to-write-simple-but-sound-yara-rules-part-2/\
https://www.bsk-consulting.de/2016/04/15/how-to-write-simple-but-sound-yara-rules-part-3/](https://www.bsk-consulting.de/2015/02/16/write-simple-sound-yara-rules/https://www.bsk-consulting.de/2015/10/17/how-to-write-simple-but-sound-yara-rules-part-2/https://www.bsk-consulting.de/2016/04/15/how-to-write-simple-but-sound-yara-rules-part-3/)

Your First Yara Rule

The proprietary language that Yara uses for rules is fairly trivial to pick up, but hard to master. This is because your rule is only as effective as your understanding of the patterns you want to search for.\
\
Using a Yara rule is simple. Every `yara` command requires two arguments to be valid, these are:\
1\) The rule file we create\
2\) Name of file, directory, or process ID to use the rule for.\
\
Every rule must have a name and condition.\
\
For example, if we wanted to use "myrule.yar" on directory "some directory", we would use the following command:\
`yara myrule.yar somedirectory`\
\
Note that .yar is the standard file extension for all Yara rules. We'll make one of the most basic rules you can make below.\
\
1\. Make a file named "somefile" via `touch somefile`\
2\. Create a new file and name it "myfirstrule.yar" like below:

Creating a file named somefile

```shell-session
cmnatic@thm:~$ touch somefile
```

Creating a file named myfirstrule.yar

```shell-session
cmnatic@thm touch myfirstrule.yar
```

3\. Open the "myfirstrule.yar" using a text editor such as `nano` and input the snippet below and save the file:

```yaml
rule examplerule {
        condition: true
}
```

\
Inputting our first snippet into "myfirstrule.yar" using nano

```shell-session
cmnatic@thm nano myfirstrule.yar   GNU nano 4.8 myfirstrule.yar Modified
rule examplerule {
        condition: true
}
```

The name of the rule in this snippet is `examplerule`, where we have one condition - in this case, the condition is `condition`. As previously discussed, every rule requires both a name and a condition to be valid. This rule has satisfied those two requirements.\
\
Simply, the rule we have made checks to see if the file/directory/PID that we specify exists via `condition: true`. If the file does exist, we are given the output of `examplerule`\
\
Let's give this a try on the file "somefile" that we made in step one:\
`yara myfirstrule.yar somefile`\
\
If "somefile" exists, Yara will say `examplerule` because the pattern has been met - as we can see below:\
\
Verifying our the examplerule is correct

```shell-session
cmnatic@thm:~$ yara myfirstrule.yar somefile 
examplerule somefile
```

If the file does not exist, Yara will output an error such as that below:\
\
Yara complaining that the file does not exist

```shell-session
cmnatic@thm:~$ yara myfirstrule.yar sometextfile
error scanning sometextfile: could not open file
```

Congrats! You've made your first rule.

Checking whether or not a file exists isn't all that helpful. After all, we can figure that out for ourselves...Using much better tools for the job.\
\
Yara has a few conditions, which I encourage you to read [here](https://yara.readthedocs.io/en/stable/writingrules.html) at your own leisure. However, I'll detail a few below and explain their purpose.\


| <p>Keyword<br></p>    |
| --------------------- |
| <p>Desc<br></p>       |
| <p>Meta<br></p>       |
| <p>Strings<br></p>    |
| <p>Conditions<br></p> |
| <p>Weight<br></p>     |

\


## Meta

This section of a Yara rule is reserved for descriptive information by the author of the rule. For example, you can use `desc`, short for description, to summarise what your rule checks for. Anything within this section does not influence the rule itself. Similar to commenting code, it is useful to summarise your rule.

## Strings

Remember our discussion about strings in Task 2? Well, here we go. You can use strings to search for specific text or hexadecimal in files or programs. For example, say we wanted to search a directory for all files containing "Hello World!", we would create a rule such as below:

```yaml
rule helloworld_checker{
	strings:
		$hello_world = "Hello World!"
}
```

We define the keyword `Strings` where the string that we want to search, i.e., "Hello World!" is stored within the variable `$hello_world`\
\
Of course, we need a condition here to make the rule valid. In this example, to make this string the condition, we need to use the variable's name. In this case, `$hello_world`:

```yaml
rule helloworld_checker{
	strings:
		$hello_world = "Hello World!"

	condition:
		$hello_world
}
```

Essentially, if any file has the string "Hello World!" then the rule will match. However, this is literally saying that it will only match if "Hello World!" is found and will not match if "_hello world_" or "_HELLO WORLD_."\
To solve this, the condition `any of them` allows multiple strings to be searched for, like below:\


```yaml
rule helloworld_checker{
	strings:
		$hello_world = "Hello World!"
		$hello_world_lowercase = "hello world"
		$hello_world_uppercase = "HELLO WORLD"

	condition:
		any of them
}
```

Now, any file with the strings of:1. Hello World!2. hello world3. HELLO WORLD\
Will now trigger the rule.

## Conditions

We have already used the `true` and `any of them` condition. Much like regular programming, you can use operators such as:\


<= less than or equal to>= more than or equal to!= not equal to\
For example, the rule below would do the following:

```yaml
rule helloworld_checker{
	strings:
		$hello_world = "Hello World!"

	condition:
        #hello_world <= 10
}
```

\
The rule will now:

1\. Look for the "Hello World!" string\
2\. Only say the rule matches if there are less than or equal to ten occurrences of the "Hello World!" string

## Combining keywords

Moreover, you can use keywords such as:

andnotor \
To combine multiple conditions. Say if you wanted to check if a file has a string and is of a certain size (in this example, the sample file we are checking is less than <10 kb and has "Hello World!" you can use a rule like below:\
\


```yaml
rule helloworld_checker{
	strings:
		$hello_world = "Hello World!" 
        
        condition:
	        $hello_world and filesize < 10KB 
}
```

\
The rule will only match if both conditions are true. To illustrate: below, the rule we created, in this case, did not match because although the file has "Hello World!", it has a file size larger than 10KB:Yara failing to match the file mytextfile because it is larger than 10kb

```shell-session
cmnatic@thm:~$ <output intentionally left blank>
```

However, the rule matched this time because the file has both "Hello World!" and a file size of less than 10KB.Yara successfully matching the file mytextfile because it has "Hello World" and a file size of less than 10KB

```shell-session
cmnatic@thm:~$ yara myfirstrule.yar mytextfile.txt
helloworld_textfile_checker mytextfile.txt
```

Remembering that the text within the red box is the name of our rule, and the text within the green is the matched file.
