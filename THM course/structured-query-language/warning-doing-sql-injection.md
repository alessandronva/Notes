# Warning doing SQL injection

## **Warning**

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
