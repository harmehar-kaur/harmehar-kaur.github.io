---
title: 
date: 
categories: 
tags: 
author: 
image:
  path: 
  alt: 
---
In this blog, we will explore SQL injection (SQLi) attacks targeting various databases such as Oracle, MySQL, and Microsoft SQL Server. Through practical examples, you’ll learn how to use UNION attacks to query database type and version, list database contents, and extract sensitive data like usernames and passwords.

SQL injection vulnerabilities occur when an application improperly handles user input, allowing an attacker to interfere with the application’s SQL queries. By manipulating the input, attackers can access or modify unauthorized data. Let’s go step by step through various labs, where we’ll exploit SQL injection vulnerabilities.

Lab 1: Querying the Database Type and Version on Oracle
In this lab, the goal is to retrieve the database version string from an Oracle database. Here’s a step-by-step approach:

Step 1: Intercept the Request
Using Burp Suite, intercept and modify the request that sets the product category filter. The goal is to inject SQL payloads to manipulate the query.

Step 2: Determine the Number of Columns
To determine how many columns are being returned by the query, use a UNION attack:

'+UNION+SELECT+'abc','def'+FROM+dual--
In this example, dual is a special table in Oracle used for performing queries that do not require an actual table. If the query returns results with this payload, you know that it is returning two columns, and both are text.

Step 3: Display the Database Version
Once you’ve identified that two columns are returned, use the following payload to display the database version string:

'+UNION+SELECT+BANNER,+NULL+FROM+v$version--
Here, v$version is an Oracle system view that stores the database version. The BANNER column in this view contains the version information.

Lab 2: Querying the Database Type and Version on MySQL and Microsoft SQL Server
Similar to the Oracle lab, this lab involves extracting the database version from MySQL or Microsoft SQL Server.

Step 1: Intercept the Request
Use Burp Suite to intercept and modify the request that sets the product category filter, just like in the Oracle lab.

Step 2: Determine the Number of Columns
Use the following payload to test how many columns are returned by the query:

'+UNION+SELECT+'abc','def'#
If the query returns results, it indicates that two columns are being returned, and both contain text data.

Step 3: Display the Database Version
Once you’ve verified the number of columns, use the appropriate payload to display the database version for MySQL or Microsoft SQL Server:

For MySQL:

'+UNION+SELECT+@@version,+NULL#
For Microsoft SQL Server:

'+UNION+SELECT+@@version,+NULL--
@@version is a system function in both MySQL and Microsoft SQL Server that returns the version of the database.

Lab 3: Listing the Database Contents on Non-Oracle Databases
In this lab, the objective is to exploit a SQL injection vulnerability to list the contents of a database, specifically targeting tables that contain user credentials.

Step 1: Intercept the Request
Intercept the request with Burp Suite, and prepare to modify the SQL query.

Step 2: Determine the Number of Columns
To find out how many columns are returned by the query and which columns contain text data, use this payload:

'+UNION+SELECT+'abc','def'--
Once you determine the query returns two columns, you can proceed to enumerate the database.

Step 3: List the Tables in the Database
Use the following payload to retrieve a list of all tables in the database:

'+UNION+SELECT+table_name,+NULL+FROM+information_schema.tables--
The information_schema.tables view stores metadata about all the tables in the database. This will help you identify the table that holds user credentials.

Step 4: Retrieve the Columns of the Target Table
After identifying the table (for example, users_abcdef), use this payload to retrieve the details of the columns in the table:

'+UNION+SELECT+column_name,+NULL+FROM+information_schema.columns+WHERE+table_name='users_abcdef'--
This will give you the names of the columns containing usernames and passwords.

Step 5: Retrieve the Usernames and Passwords
Finally, retrieve the usernames and passwords using this payload:

'+UNION+SELECT+username_abcdef,+password_abcdef+FROM+users_abcdef--
Lab 4: Listing the Database Contents on Oracle Databases
This lab is similar to the previous one, but the target is an Oracle database. The goal is to retrieve the usernames and passwords from the Oracle database.

Step 1: Intercept the Request
Use Burp Suite to intercept and modify the request.

Step 2: Determine the Number of Columns
Use this payload to find out how many columns are returned and which ones contain text:

'+UNION+SELECT+'abc','def'+FROM+dual--
Step 3: List the Tables in the Database
Use the following payload to retrieve a list of all tables in the Oracle database:

'+UNION+SELECT+table_name,NULL+FROM+all_tables--
In Oracle, all_tables is a system view that contains information about all tables that the user has access to.

Step 4: Retrieve the Columns of the Target Table
Once you have the table name (e.g., USERS_ABCDEF), use this payload to retrieve the details of the columns:

'+UNION+SELECT+column_name,NULL+FROM+all_tab_columns+WHERE+table_name='USERS_ABCDEF'--
Step 5: Retrieve the Usernames and Passwords
Finally, use this payload to retrieve the usernames and passwords from the USERS_ABCDEF table:

'+UNION+SELECT+USERNAME_ABCDEF,+PASSWORD_ABCDEF+FROM+USERS_ABCDEF--
Conclusion
In this blog, we demonstrated how SQL injection attacks can be used to query the database type and version, as well as extract sensitive data like usernames and passwords. Whether the target is an Oracle, MySQL, or Microsoft SQL Server database, the core principles of SQL injection remain the same. By leveraging UNION attacks, you can manipulate queries to reveal valuable information stored in the database.

To prevent such attacks, it’s essential to follow best practices like using parameterized queries, implementing strong web application firewalls (WAFs), and conducting regular security audits. As attackers find new ways to bypass filters, it’s crucial to stay updated with the latest security trends and ensure your applications are protected.

Stay tuned for more hands-on labs and walkthroughs as I progress in my journey on learning about SQL injection and other vulnerabilities!
