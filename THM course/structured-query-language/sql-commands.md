# SQL commands

SELECT

The first query type we'll learn is the SELECT query used to retrieve data from the database. \


`select * from users;`\


| <p>id<br></p> | <p>username<br></p> | <p>password<br></p>  |
| ------------- | ------------------- | -------------------- |
| <p>1<br></p>  | <p>jon<br></p>      | <p>pass123<br></p>   |
| <p>2<br></p>  | <p>admin<br></p>    | <p>p4ssword<br></p>  |
| <p>3<br></p>  | <p>martin<br></p>   | <p>secret123<br></p> |

The first-word SELECT tells the database we want to retrieve some data, the \* tells the database we want to receive back all columns from the table. For example, the table may contain three columns (id, username and password). "from users" tells the database we want to retrieve the data from the table named users. Finally, the semicolon at the end tells the database that this is the end of the query. &#x20;

The next query is similar to the above, but this time, instead of using the \* to return all columns in the database table, we are just requesting the username and password field.

`select username,password from users;`

| <p>username<br></p> | <p>password<br></p>  |
| ------------------- | -------------------- |
| <p>jon<br></p>      | <p>pass123<br></p>   |
| <p>admin<br></p>    | <p>p4ssword<br></p>  |
| <p>martin<br></p>   | <p>secret123<br></p> |

The following query, like the first, returns all the columns by using the \* selector and then the "LIMIT 1" clause forces the database only to return one row of data. Changing the query to "LIMIT 1,1" forces the query to skip the first result, and then "LIMIT 2,1" skips the first two results, and so on. You need to remember the first number tells the database how many results you wish to skip, and the second number tells the database how many rows to return.

`select * from users LIMIT 1;`

| <p>id<br></p> | <p>username<br></p> | <p>password<br></p> |
| ------------- | ------------------- | ------------------- |
| <p>1<br></p>  | <p>jon<br></p>      | <p>pass123<br></p>  |

Lastly, we're going to utilise the where clause; this is how we can finely pick out the exact data we require by returning data that matches our specific clauses:

`select * from users where username='admin';`

| <p>id<br></p> | <p>username<br></p> | <p>password<br></p> |
| ------------- | ------------------- | ------------------- |
| <p>2<br></p>  | <p>admin<br></p>    | <p>p4ssword<br></p> |

This will only return the rows where the username is equal to admin.

`select * from users where username != 'admin';`

| <p>id<br></p> | <p>username<br></p> | <p>password<br></p>  |
| ------------- | ------------------- | -------------------- |
| <p>1<br></p>  | <p>jon<br></p>      | <p>pass123<br></p>   |
| <p>3<br></p>  | <p>martin<br></p>   | <p>secret123<br></p> |

This will only return the rows where the username is **NOT** equal to admin.

`select * from users where username='admin' or username='jon';`

| <p>id<br></p> | <p>username<br></p> | <p>password<br></p> |
| ------------- | ------------------- | ------------------- |
| <p>1<br></p>  | <p>jon<br></p>      | <p>pass123<br></p>  |
| <p>2<br></p>  | <p>admin<br></p>    | <p>p4ssword<br></p> |

This will only return the rows where the username is either equal to **admin** or j**on**.&#x20;

`select * from users where username='admin' and password='p4ssword';`

| <p>id<br></p> | <p>username<br></p> | <p>password<br></p> |
| ------------- | ------------------- | ------------------- |
| <p>2<br></p>  | <p>admin<br></p>    | <p>p4ssword<br></p> |

This will only return the rows where the username is equal to **admin**, and the password is equal to **p4ssword**.

Using the like clause allows you to specify data that isn't an exact match but instead either starts, contains or ends with certain characters by choosing where to place the wildcard character represented by a percentage sign %.

`select * from users where username like 'a%';`

| <p>id<br></p> | <p>username<br></p> | <p>password<br></p> |
| ------------- | ------------------- | ------------------- |
| <p>2<br></p>  | <p>admin<br></p>    | <p>p4ssword<br></p> |

This returns any rows with username beginning with the letter a.

`select * from users where username like '%n';`

| <p>id<br></p> | <p>username<br></p> | <p>password<br></p>  |
| ------------- | ------------------- | -------------------- |
| <p>1<br></p>  | <p>jon<br></p>      | <p>pass123<br></p>   |
| <p>2<br></p>  | <p>admin<br></p>    | <p>p4ssword<br></p>  |
| <p>3<br></p>  | <p>martin<br></p>   | <p>secret123<br></p> |

This returns any rows with username ending with the letter n.

`select * from users where username like '%mi%';`

| <p>id<br></p> | <p>username<br></p> | <p>password<br></p> |
| ------------- | ------------------- | ------------------- |
| <p>2<br></p>  | <p>admin<br></p>    | <p>p4ssword<br></p> |

This returns any rows with a username containing the characters **mi** within them.\


UNION\


The UNION statement combines the results of two or more SELECT statements to retrieve data from either single or multiple tables; the rules to this query are that the UNION statement must retrieve the same number of columns in each SELECT statement, the columns have to be of a similar data type and the column order has to be the same. This might sound not very clear, so let's use the following analogy. Say a company wants to create a list of addresses for all customers and suppliers to post a new catalogue. We have one table called customers with the following contents:\


\


| <p>id<br></p> | <p>name<br></p>             | <p>address<br></p>         | <p>city<br></p>       | <p>postcode<br></p> |
| ------------- | --------------------------- | -------------------------- | --------------------- | ------------------- |
| <p>1<br></p>  | <p>Mr John Smith<br></p>    | <p>123 Fake Street<br></p> | <p>Manchester<br></p> | <p>M2 3FJ<br></p>   |
| <p>2<br></p>  | <p>Mrs Jenny Palmer<br></p> | <p>99 Green Road<br></p>   | <p>Birmingham<br></p> | <p>B2 4KL<br></p>   |
| <p>3<br></p>  | <p>Miss Sarah Lewis<br></p> | <p>15 Fore Street<br></p>  | <p>London<br></p>     | <p>NW12 3GH<br></p> |

And another called suppliers with the following contents:

\


| <p>id<br></p> | <p>company<br></p>          | <p>address<br></p>                     | <p>city<br></p>    | <p>postcode<br></p> |
| ------------- | --------------------------- | -------------------------------------- | ------------------ | ------------------- |
| <p>1<br></p>  | <p>Widgets Ltd<br></p>      | <p>Unit 1a, Newby Estate<br></p>       | <p>Bristol<br></p> | <p>BS19 4RT<br></p> |
| <p>2<br></p>  | <p>The Tool Company<br></p> | <p>75 Industrial Road<br></p>          | <p>Norwich<br></p> | <p>N22 3DR<br></p>  |
| <p>3<br></p>  | <p>Axe Makers Ltd<br></p>   | <p>2b Makers Unit, Market Road<br></p> | <p>London<br></p>  | <p>SE9 1KK<br></p>  |

Using the following SQL Statement, we can gather the results from the two tables and put them into one result set:

`SELECT name,address,city,postcode from customers UNION SELECT company,address,city,postcode from suppliers;`

| <p>name<br></p>             | <p>address<br></p>          | <p>city<br></p>       | <p>postcode<br></p> |
| --------------------------- | --------------------------- | --------------------- | ------------------- |
| <p>Mr John Smith<br></p>    | <p>123 Fake Street<br></p>  | <p>Manchester<br></p> | <p>M2 3FJ<br></p>   |
| <p>Mrs Jenny Palmer<br></p> | <p>99 Green Road<br></p>    | <p>Birmingham<br></p> | <p>B2 4KL<br></p>   |
| <p>Miss Sarah Lewis<br></p> | <p>15 Fore Street<br></p>   | <p>London<br></p>     | <p>NW12 3GH<br></p> |
| Widgets Ltd                 | Unit 1a, Newby Estate       | Bristol               | BS19 4RT            |
| The Tool Company            | 75 Industrial Road          | Norwich               | N22 3DR             |
| Axe Makers Ltd              | 2b Makers Unit, Market Road | London                | SE9 1KK             |

INSERT

The **INSERT** statement tells the database we wish to insert a new row of data into the table. **"into users"** tells the database which table we wish to insert the data into, **"(username,password)"** provides the columns we are providing data for and then **"values ('bob','password');"** provides the data for the previously specified columns.

`insert into users (username,password) values ('bob','password123');`

| <p>id<br></p> | <p>username<br></p> | <p>password<br></p>    |
| ------------- | ------------------- | ---------------------- |
| <p>1<br></p>  | <p>jon<br></p>      | <p>pass123<br></p>     |
| <p>2<br></p>  | <p>admin<br></p>    | <p>p4ssword<br></p>    |
| <p>3<br></p>  | <p>martin<br></p>   | <p>secret123<br></p>   |
| <p>4<br></p>  | <p>bob<br></p>      | <p>password123<br></p> |

### UPDATE

The **UPDATE** statement tells the database we wish to update one or more rows of data within a table. You specify the table you wish to update using "**update %tablename% SET**" and then select the field or fields you wish to update as a comma-separated list such as "**username='root',password='pass123'**" then finally similar to the SELECT statement, you can specify exactly which rows to update using the where clause such as "**where username='admin;**".

`update users SET username='root',password='pass123' where username='admin';`

| <p>id<br></p> | <p>username<br></p> | <p>password<br></p>    |
| ------------- | ------------------- | ---------------------- |
| <p>1<br></p>  | <p>jon<br></p>      | <p>pass123<br></p>     |
| <p>2<br></p>  | <p>root<br></p>     | <p>pass123<br></p>     |
| <p>3<br></p>  | <p>martin<br></p>   | <p>secret123<br></p>   |
| <p>4<br></p>  | <p>bob<br></p>      | <p>password123<br></p> |

### DELETE

The **DELETE** statement tells the database we wish to delete one or more rows of data. Apart from missing the columns you wish to be returned, the format of this query is very similar to the SELECT. You can specify precisely which data to delete using the **where** clause and the number of rows to be deleted using the **LIMIT** clause.

`delete from users where username='martin';`

| <p>id<br></p> | <p>username<br></p> | <p>password<br></p>    |
| ------------- | ------------------- | ---------------------- |
| <p>1<br></p>  | <p>jon<br></p>      | <p>pass123<br></p>     |
| <p>2<br></p>  | <p>root<br></p>     | <p>pass123<br></p>     |
| <p>4<br></p>  | <p>bob<br></p>      | <p>password123<br></p> |

`delete from users;`

\


Because no WHERE clause was being used in the query, all the data is deleted in the table.\


###

| <p>id<br></p> | <p>username<br></p> | password |
| ------------- | ------------------- | -------- |
