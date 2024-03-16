# Creating Yara rules with yarGen

From the previous section, we realized that we have a file that Loki didn't flag on. At this point, we are unable to run Loki on other web servers because if file 2 exists in any of the webs servers, it will go undetected.

We need to create a Yara rule to detect this specific web shell in our environment. Typically this is what is done in the case of an incident, which is an event that affects/impacts the organization in a negative fashion.

We can manually open the file and attempt to sift through lines upon lines of code to find possible strings that can be used in our newly created Yara rule.

Let's check how many lines this particular file has. You can run the following: strings | wc -l.

Using wc to count the amount of lines in the file cmnatic@thm-yara:\~/suspicious-files/file2$ strings 1ndex.php | wc -l 3580 If you try to go through each string, line by line manually, you should quickly realize that this can be a daunting task.

Catting the output of 1ndex.php if(res=='error'){ $('.ulProgress'+ulType+i).html('( failed )'); } else{ $('.ulRes'+ulType+i).html(res); } loading\_stop(); }, error: function(){ loading\_stop(); $('.ulProgress'+ulType+i).html('( failed )'); $('.ulProgress'+ulType+i).removeClass('ulProgress'+ulType+i); $('.ulFilename'+ulType+i).removeClass('ulFilename'+ulType+i); } }); }

function ul\_go(ulType){ ulFile = (ulType=='comp')? $('.ulFileComp'):$('.ulFileUrl'); ulResult = (ulType=='comp')? $('.ulCompResult'):$('.ulUrlResult'); ulResult.html('');

ulFile.each(function(i){ if(((ulType=='comp')&\&this.files\[0])||((ulType=='url')&&(this.value!=''))){ file = (ulType=='comp')? this.files\[0]: this.value; filename = (ulType=='comp')? file.name: file.substring(file.lastIndexOf('/')+1);

ulSaveTo = (ulType=='comp')? $('.ulSaveToComp')\[i].value:$('.ulSaveToUrl')\[i].value; ulFilename = (ulType=='comp')? $('.ulFilenameComp')\[i].value:$('.ulFilenameUrl')\[i].value;

\--snippet cropped for brevity--

Luckily, we can use yarGen (yes, another tool created by Florian Roth) to aid us with this task.

What is yarGen? yarGen is a generator for YARA rules.

From the README - "The main principle is the creation of yara rules from strings found in malware files while removing all strings that also appear in goodware files. Therefore yarGen includes a big goodware strings and opcode database as ZIP archives that have to be extracted before the first use."

Navigate to the yarGen directory, which is within tools. If you are running yarGen on your own system, you need to update it first by running the following command: python3 yarGen.py --update.

This will update the good-opcodes and good-strings DB's from the online repository. This update will take a few minutes.

Once it has been updated successfully, you'll see the following message at the end of the output.

### Updating yarGen cmnatic@thm-yara:\~/tools/yarGen$ python3 yarGen.py --update

```
               _____
__ _____ _____/ ___/__ ___
```

/ // / \_ \`/ _/ ( / -_) \_\
\_, /\_,_/_/ \_**/\_**_**/**_**//**_**/ /**_/ Yara Rule Generator Florian Roth, July 2020, Version 0.23.3

### Note: Rules have to be post-processed See this post for details: https://medium.com/@cyb3rops/121d29322282

Downloading good-opcodes-part1.db from https://www.bsk-consulting.de/yargen/good-opcodes-part1.db ...

To use yarGen to generate a Yara rule for file 2, you can run the following command:

python3 yarGen.py -m /home/cmnatic/suspicious-files/file2 --excludegood -o /home/cmnatic/suspicious-files/file2.yar

A brief explanation of the parameters above:

\-m is the path to the files you want to generate rules for --excludegood force to exclude all goodware strings (these are strings found in legitimate software and can increase false positives) -o location & name you want to output the Yara rule If all is well, you should see the following output.

Using yarGen to generate a rule for file2

```
       [=] Generated 1 SIMPLE rules.
       [=] All rules written to /home/cmnatic/suspicious-files/file2.yar
       [+] yarGen run finished
```

Generally, you would examine the Yara rule and remove any strings that you feel might generate false positives. For this exercise, we will leave the generated Yara rule as is and test to see if Yara will flag file 2 or no.

Note: Another tool created to assist with this is called yarAnalyzer (you guessed it - created by Florian Roth). We will not examine that tool in this room, but you should read up on it, especially if you decide to start creating your own Yara rules.

Further Reading on creating Yara rules and using yarGen:

https://www.bsk-consulting.de/2015/02/16/write-simple-sound-yara-rules/ https://www.bsk-consulting.de/2015/10/17/how-to-write-simple-but-sound-yara-rules-part-2/ https://www.bsk-consulting.de/2016/04/15/how-to-write-simple-but-sound-yara-rules-part-3/
