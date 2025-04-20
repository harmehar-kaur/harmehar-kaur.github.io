---
title: Exploring Web Vulnerabilities You Should Know About
date: 2024-08-06
categories: [Cyber Security Fundamentals]
tags: [web security, vulnerabilities, cyber threats, hacking, OWASP]
author: Harmehar Kaur
image:
  path: /assets/attack.jpg
  alt: Web Vulnerabilities
---

### Exploring Web Vulnerabilities You Should Know About

In the world of cybersecurity, understanding various **web vulnerabilities** is crucial to both securing applications and defending against potential cyber-attacks. In today’s post, we’ll look at a list of common vulnerabilities, their descriptions, and their potential impact on systems.

Here are some of the most important web vulnerabilities that you should be aware of:

---

#### 1. **Arbitrary File Access**
- **Description**: Occurs when user input is not sanitized, allowing attackers to access sensitive files on the server, often via file download functionality.

---

#### 2. **Blind XPath Injection**
- **Description**: A vulnerability that allows attackers to interfere with the logic of an application’s XML query to its data store by injecting malicious XPath queries.

---

#### 3. **Brute Force Attack**
- **Description**: An attack where multiple combinations of usernames and passwords are systematically tried to gain unauthorized access to an account.

---

#### 4. **Cache Poisoning**
- **Description**: An attack where an attacker inserts malicious data into a cache, causing users to receive the corrupted content.

---

#### 5. **Cash Overflow**
- **Description**: Likely a typo; could mean exploiting financial systems or payment-related mechanisms, leading to unintended credit or fund access.

---

#### 6. **Clickjacking**
- **Description**: A UI redress attack where malicious pages trick users into clicking elements on a website they cannot see, performing unintended actions.

---

#### 7. **Command Injection**
- **Description**: Allows attackers to execute OS commands on a server. Attackers exploit this vulnerability to compromise hosting infrastructure or pivot to other systems.
- **Types**:
    - **Blind OS Command Injection**: Detectable via time delays or indirect output redirection.
    - **Useful Commands**:
      - Current User: `whoami`
      - OS Details: `uname -a` (Linux), `ver` (Windows)
      - Network Config: `ifconfig` (Linux), `ipconfig /all` (Windows)

---

#### 8. **Comment Injection Attack**
- **Description**: Exploiting the ability to inject malicious content into comment sections of a web page.

---

#### 9. **Content Security Policy (CSP)**
- **Description**: A browser feature designed to prevent cross-site scripting (XSS) and data injection attacks by specifying allowed sources for content.

---

#### 10. **Content Spoofing**
- **Description**: Manipulating a web application to display misleading content to users, often used in phishing attacks.

---

#### 11. **Credential Stuffing**
- **Description**: Using stolen username-password pairs to gain unauthorized access to multiple systems.

---

#### 12. **Cross Frame Scripting**
- **Description**: Involves malicious interactions with iframes, often aiming to steal sensitive information.

---

#### 13. **Cross-Site History Manipulation**
- **Description**: Manipulating browser history to interfere with user navigation.

---

#### 14. **Cross-Site Tracing**
- **Description**: Exploiting the HTTP TRACE method to steal sensitive information.

---

#### 15. **Cross-Site Request Forgery (CSRF)**
- **Description**: Induces users to perform unintended actions by leveraging their authenticated sessions.
- **Impact**: Account compromise, privileged action execution, or complete control over data and functionality.

---

#### 16. **Cross-Site Port Attack**
- **Description**: Exploiting the interaction between a user’s browser and other services running on specific ports.

---

#### 17. **Cross-Site Scripting (XSS)**
- **Description**: Allows attackers to execute malicious scripts in users' browsers by exploiting unvalidated inputs.
- **Types**:
    - **Reflected**: Malicious script comes from the current HTTP request.
    - **Stored**: Script is stored on the server and served to other users.
    - **DOM-Based**: Vulnerability exists in client-side code.

---

#### 18. **Custom Special Character Injection**
- **Description**: Exploiting improper handling of special characters to inject malicious content.

---

#### 19. **Denial of Service (DoS)**
- **Description**: Disrupting the availability of a service by overwhelming it with traffic or resource-intensive tasks.

---

#### 20. **Exploitation of CORS**
- **Description**: Leveraging insecure Cross-Origin Resource Sharing configurations to access restricted resources.

---

#### 21. **Format String Attack**
- **Description**: Exploiting vulnerabilities in string formatting functions to execute arbitrary code or crash an application.

---

#### 22. **Full Path Disclosure**
- **Description**: Exposing the full path of files on the server, aiding attackers in identifying file locations.

---

#### 23. **Function Injection**
- **Description**: Manipulating application inputs to invoke unintended functions.

---

#### 24. **Host Header Injection**
- **Description**: Exploiting misconfigured server-side host header handling to perform web cache poisoning, SSRF, or bypass security controls.

---

#### 25. **HTTP Verb Tampering**
- **Description**: Exploiting improper handling of HTTP methods (e.g., GET, POST, DELETE) to bypass access controls.

---

#### 26. **HTML Injection**
- **Description**: Injecting malicious HTML content into web applications, often leading to XSS attacks.

---

#### 27. **LDAP Injection**
- **Description**: Manipulating LDAP queries to access unauthorized data or bypass authentication.

---

#### 28. **Log Injection**
- **Description**: Injecting malicious content into log files, potentially enabling further attacks like XSS or log file tampering.

---

#### 29. **Path Traversal**
- **Description**: Gaining unauthorized access to files outside the intended directory by manipulating file paths.

---

#### 30. **Server-Side Request Forgery (SSRF)**
- **Description**: Exploiting a server’s ability to send HTTP requests to access unauthorized internal or external resources.

---

#### 31. **Server-Side Includes (SSI) Injection**
- **Description**: Injecting malicious server-side include directives to execute arbitrary commands.

---

#### 32. **Session Fixation**
- **Description**: Forcing a user to use a known session ID, enabling the attacker to hijack the session.

---

#### 33. **Session Hijacking**
- **Description**: Stealing a user’s session ID to impersonate them and gain unauthorized access.

---

#### 34. **Email Header Injection**
- **Description**: Injecting malicious headers into emails sent by web applications, often used in phishing or spam.

---

#### 35. **Use-After-Free (UAF)**
- **Description**: Accessing memory after it has been freed, potentially leading to data corruption, crashes, or arbitrary code execution.

---

In the world of cybersecurity, staying informed about these vulnerabilities is key to preventing potential attacks. Make sure to secure your applications and stay ahead of attackers by addressing these issues early in the development and deployment stages.

