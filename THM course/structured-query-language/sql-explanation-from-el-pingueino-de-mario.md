# SQL explanation from "El pingüino de Mario"

In the explanation we are using a HTB machine with a webpage login

<div>

<figure><img src="../../.gitbook/assets/sql-1.png" alt=""><figcaption></figcaption></figure>

 

<figure><img src="../../.gitbook/assets/sql-2.png" alt=""><figcaption></figcaption></figure>

</div>

The request comes in the following query:

select \* from acceso WHERE usuario='mario' AND contraseña='1234';

### 1=1-- - Explanation

<figure><img src="../../.gitbook/assets/sql-3.png" alt=""><figcaption><p>If we execute this it will return all the users in the DATABASE</p></figcaption></figure>

The instruction above could be read like = Select from table "acceso" the user 'mario' or "everything else". It doesn't matter if the user doesn't exist



Also it could be done like this mario'--

<figure><img src="../../.gitbook/assets/SQL-4.png" alt=""><figcaption></figcaption></figure>
