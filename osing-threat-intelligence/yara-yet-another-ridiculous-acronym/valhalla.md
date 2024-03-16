# Valhalla

Valhalla is an online Yara feed created and hosted by Nextron-Systems (erm, Florian Roth). By now, you should be aware of the ridiculous amount of time and energy Florian has dedicated to creating these tools for the community. Maybe we should have just called this the Florian Roth room. (lol)

Per the website, "Valhalla boosts your detection capabilities with the power of thousands of hand-crafted high-quality YARA rules."

A picture displaying the search menu for the Valhalla tool.

From the image above, we should denote that we can conduct searches based on a keyword, tag, ATT\&CK technique, sha256, or rule name.

Note: For more information on ATT\&CK, please visit the MITRE room.

Taking a look at the data provided to us, let's examine the rule in the screenshot below:

A picture displaying the results of a rule, depicting the rule name, description and the date it was submitted to Valhalla

We are provided with the name of the rule, a brief description, a reference link for more information about the rule, along with the rule date.

Feel free to look at some rules to become familiar with the usefulness of Valhalla. The best way to learn the product is by just jumping right in.

Picking up from our scenario, at this point, you know that the 2 files are related. Even though Loki classified the files are suspicious, you know in your gut that they are malicious. Hence the reason you created a Yara rule using yarGen to detect it on other web servers. But let's further pretend that you are not code-savvy (FYI - not all security professionals know how to code/script or read it). You need to conduct further research regarding these files to receive approval to eradicate these files from the network.

Time to use Valhalla for some threat intelligence gathering...
