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
Introduction
SQL injection is a vulnerability that allows attackers to manipulate SQL queries sent to the database. One of the common exploits through SQL injection is bypassing an application’s login functionality. In this blog, I will discuss how attackers can subvert an application’s logic to gain unauthorized access by performing a login bypass using Burp Suite.

Subverting Application Logic
In some web applications, the login form is vulnerable to SQL injection. This allows attackers to alter the SQL query logic, enabling them to log in without valid credentials.

Let’s consider a typical login scenario:
When a user submits a username and password, the following SQL query is executed:

sql
Copy code
SELECT * FROM users WHERE username='apex' AND password='blindeye';
If the credentials match, the user is granted access. However, this query can be manipulated using SQL injection to bypass password validation.

Example of Subverting the Logic:
The attacker can inject the SQL comment sequence (--) to remove the password check.
For example, submitting administrator as the username and leaving the password blank leads to a query like this:
sql
Copy code
SELECT * FROM users WHERE username='administrator'--' AND password='';
The -- comments out the rest of the query, meaning the application only checks if the username exists, bypassing the need for a correct password.

Step-by-Step Guide: SQL Injection to Bypass Login Authentication
Let’s walk through a lab that demonstrates this type of SQL injection using Burp Suite.

1. Intercept the Login Request with Burp Suite
Start Burp Suite and configure your browser to send traffic through Burp’s proxy.
Navigate to the login page of the vulnerable application.
Enter any username and password and capture the login request.
2. Modify the Username Parameter
In Burp Suite, locate the request you intercepted and focus on the username parameter.
Modify the username field as follows:
administrator'--
Explanation:

The SQL query will become:
SELECT * FROM users WHERE username='administrator'--' AND password='';
The -- ensures that everything after it (including the password check) is ignored, meaning that only the username is checked, not the password.
3. Forward the Modified Request
Forward the modified request to the server through Burp Suite.
If the SQL injection is successful, the server will log you in as the administrator, bypassing the need for a password.
4. Verify Successful Login
After forwarding the request, check if you are logged in as the administrator.
You should have access to administrative functions or restricted sections of the application.
Conclusion
SQL injection vulnerabilities in login forms can allow attackers to bypass authentication mechanisms, potentially giving them full control over user accounts or administrative access. Understanding how this attack works helps in identifying and fixing such issues in web applications.

Stay tuned for more in-depth tutorials on security vulnerabilities I learn as I progress in my journey of learning new things in VAPT and Cyber Security!
