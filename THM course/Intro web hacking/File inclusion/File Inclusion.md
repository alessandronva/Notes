# File Inclusion

In some scenarios, web applications are written to request access to files on a given system, including images, static text, and so on via parameters. Parameters are query parameter strings attached to the URL that could be used to retrieve data or perform actions based on user input. The following diagram breaks down the essential parts of a URL.!\[\[dbf35cc4f35fde7a4327ad8b5a2ae2ec.png]] For example, parameters are used with Google searching, where GET requests pass user input into the search engine. https://www.google.com/search?q=TryHackMe. If you are not familiar with the topic, you can view the [How The Web Works](https://tryhackme.com/module/how-the-web-works) module to understand the concept. &#x20;

Let's discuss a scenario where a user requests to access files from a webserver. First, the user sends an HTTP request to the webserver that includes a file to display. For example, if a user wants to access and display their CV within the web application, the request may look as follows, http://webapp.thm/get.php?file=userCV.pdf, where the file is the parameter and the userCV.pdf, is the required file to access.

!\[\[dc22709e572d5de31ed4effb2ebc161f.png]]
