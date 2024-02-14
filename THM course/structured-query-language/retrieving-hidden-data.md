# Retrieving hidden data

The application doesn't implement any defenses against SQL injection attacks. This means an attacker can construct the following attack, for example:

`https://insecure-website.com/products?category=Gifts'--`

This results in the SQL query:

`SELECT * FROM products WHERE category = 'Gifts'--' AND released = 1`

Crucially, note that `--` is a comment indicator in SQL. This means that the rest of the query is interpreted as a comment, effectively removing it. In this example, this means the query no longer includes `AND released = 1`. As a result, all products are displayed, including those that are not yet released.

You can use a similar attack to cause the application to display all the products in any category, including categories that they don't know about:

`https://insecure-website.com/products?category=Gifts'+OR+1=1--`

This results in the SQL query:

`SELECT * FROM products WHERE category = 'Gifts' OR 1=1--' AND released = 1`

The modified query returns all items where either the `category` is `Gifts`, or `1` is equal to `1`. As `1=1` is always true, the query returns all items.

**Warning**

Take care when injecting the condition `OR 1=1` into a SQL query. Even if it appears to be harmless in the context you're injecting into, it's common for applications to use data from a single request in multiple different queries. If your condition reaches an `UPDATE` or `DELETE` statement, for example, it can result in an accidental loss of data.

If this input is directly concatenated into the SQL query, the resulting query becomes:

```sql
sqlCopy codeSELECT * FROM users WHERE username = '' OR 1=1 --' AND password = 'input_password'
```

With the `OR 1=1` condition injected, the WHERE clause always evaluates to true, effectively bypassing the password check. The `--` denotes a comment in SQL, effectively nullifying the remaining part of the query.

If the application's code isn't properly secured and allows this injected query to proceed, the application might authenticate the user regardless of the provided password, granting unauthorized access.

Now, let's consider a more dangerous scenario. Suppose the application allows users to delete their own accounts using a query like:

```sql
sqlCopy codeDELETE FROM users WHERE username = 'input_username'
```

If an attacker injects `OR 1=1`, the resulting query becomes:

```sql
sqlCopy codeDELETE FROM users WHERE username = '' OR 1=1 --
```
