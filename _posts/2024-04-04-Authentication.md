---
title: Cyber Security Crucial Terms
date: 2024-04-04
categories: [Cyber Security Fundamentals]
tags: [Cyber, Authentication, Authorization, Non-repudiation]
author: Harmehar Kaur
image:
  path: /assets/cyber-prefix.png
  alt: Cyber
---

## Authentication

Authentication is a feature of communication, documents, or any other data that assures legitimacy and integrity. It verifies a user's identity and is the first step in any cryptographic solution.

- **Purpose:** Ensure the user is legitimate.
- **Examples:** Passwords, digital signatures, keys, biometrics, passports.

### Types of Authentication

- **Single Factor Authentication:** Uses one factor (something you know/have/are). Offers minimal protection.
- **Multifactor Authentication (MFA):** Uses two or more distinct factors. Example: password + OTP.

### Authentication Methods

- **Knowledge-Based Authentication:** Passwords, PINs, security questions. Vulnerable to brute force, spoofing, shoulder surfing, etc.
- **Ownership-Based Authentication:** ID cards, tokens, mobile phones.
- **Inherence-Based Authentication:** Fingerprints, retinal scans, voice, signature.

### Benefits of MFA

- Enhances security.
- Reduces IT costs and password fatigue.
- Improves user experience.
- Helps meet compliance and reduces fraud.

### Adaptive Authentication

- Dynamically adjusts authentication based on risk (location, behavior, etc.).
- Low-risk users face minimal checks; high-risk users get stronger verification.
- Improves balance between usability and security.

---

## Authorization

Authorization is a technique to determine the access level or privileges granted to users or systems. It ensures users can access only the resources they are permitted to.

---

## Non-Repudiation

Non-repudiation ensures that:
- A sender cannot deny sending a message.
- A recipient cannot deny receiving it.

### Purpose

Provides proof of origin and delivery, securing accountability and integrity in transactions.

### Tools

- Digital certificates
- Digital signatures

### Types of Non-Repudiation

- **Origin:** Proves who sent the message and when.
- **Delivery:** Proves the message reached the intended recipient.
  - *Proof of Submission*: Confirms the message was sent.
  - *Proof of Delivery*: Confirms delivery occurred.
- **Receipt:** Proves the message was received.

### Key Components

- Identity of Sender
- Message Content
- Timestamp
- Recipient Identity
- Acknowledgment of Receipt

### Mechanism

1. **Agreement**: All parties agree on using non-repudiation.
2. **Proof Generation**: e.g., digital signature.
3. **Proof Transmission**: Sent with the transaction.
4. **Proof Verification**: Confirms authenticity.
5. **Archival**: Stores proof for future reference.
6. **Retrieval**: For disputes or verification.
7. **Presentation**: Used in case of disputes.

### Mitigation Methods

- **Message Authentication**
  - Message Authentication Code (MAC)
  - Digital Signatures
- **Sender/Receiver Authentication**
  - Username/Password
  - SSL (Secure Socket Layer)

### Examples & Applications

- **Digital Receipts in Email**
- **E-commerce Transactions**
- **Contract Verification with Digital Certificates**

### Real-World Use Cases

- **Proof in Communication:** Signed receipts for email confirmations.
- **Server Verification:** Server logs for message receipt.
- **Healthcare:** Non-repudiation for critical patient records.

### Mechanisms for Implementation

#### Digital Certificates

- Issued by a Certifying Authority (CA)
- Verifies identity and provides a public key
- Used for encrypting and verifying communication

#### SSL / TLS

- Secures communication over the internet
- Provides encryption and certificate-based authentication
- TLS is an updated and more secure version of SSL

#### SOAP with DSIG

- XML-based protocol for web services
- Supports non-repudiation with digital signatures in message headers and bodies

---
