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
SQL Injection is a well-known web vulnerability that allows attackers to interfere with the queries that an application makes to its database.

In this blog, I will walk you through a simple SQL injection attack that reveals unreleased products by manipulating the product category filter.

Step-by-Step Guide to Exploiting SQL Injection

1. Understanding the Vulnerability
In this lab, we are exploiting a SQL injection vulnerability found in the product category filter. The application uses a SQL query like this:

SELECT * FROM products WHERE category = 'Gifts' AND released = 1;
The goal is to manipulate the query so that the released condition is bypassed, allowing us to see unreleased products.

2. Setting Up Burp Suite
To intercept and modify the request:

First, open Burp Suite and configure your browser to route traffic through Burp’s proxy. I have used foxy proxy for this.
Enable intercept mode to capture HTTP requests.
3. Intercepting the Request
Navigate to the website’s product page and select a category (e.g., “Gifts”).
In Burp Suite, you’ll see an intercepted request that looks something like this:
GET /products?category=Gifts HTTP/1.1
Host: vulnerable-website.com
Here, the category parameter is set to 'Gifts'. This is where the SQL query gets its input from.

4. Modifying the Request for SQL Injection
Now, we want to inject a SQL payload into the category parameter to manipulate the query.
Modify the category value to:
' OR 1=1--
This changes the original query to:

SELECT * FROM products WHERE category = '' OR 1=1--' AND released = 1;
Explanation:

The ' OR 1=1-- trick forces the query to always evaluate as true (1=1 is always true).
The -- comments out the rest of the SQL query, ignoring the released = 1 condition, which filters released products.
5. Submitting the Request
After modifying the request, forward it to the server using Burp Suite.
The server will now return products, including those that are unreleased, since the released = 1 condition has been bypassed.
6. Verifying the Results
In the HTTP response, check if there are unreleased products listed.
If successful, the modified query will display more products than before, indicating that the SQL injection was successful.
A sure way to verify if the lab is successful is through the solved tag that appears once we complete the lab.
Conclusion
This basic SQL injection technique is a common vulnerability that attackers can exploit to extract sensitive data from web applications. In this case, we leveraged Burp Suite to intercept and modify a query, successfully accessing unreleased products. Stay tuned for more walkthroughs and tutorials on web security vulnerabilities!
