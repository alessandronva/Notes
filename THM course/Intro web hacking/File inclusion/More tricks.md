**3.** Next, in the following scenarios, the developer starts to use input validation by filtering some keywords. Let's test out and check the error message!  

http://webapp.thm/index.php?lang=../../../../etc/passwd  

We got the following error!  

```php
Warning: include(languages/etc/passwd): failed to open stream: No such file or directory in /var/www/html/THM-5/index.php on line 15
```

  

If we check the warning message in the include(languages/etc/passwd) section, we know that the web application replaces the ../ with the empty string. There are a couple of techniques we can use to bypass this.

First, we can send the following payload to bypass it: ....//....//....//....//....//etc/passwd

Why did this work?

This works because the PHP filter only matches and replaces the first subset string ../ it finds and doesn't do another pass, leaving what is pictured below.  

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5d617515c8cd8348d0b4e68f/room-content/30d3bf0341ba99485c5f683a416a056d.png)  

Try out Lab #5 and try to read /etc/passwd and bypass the filter!