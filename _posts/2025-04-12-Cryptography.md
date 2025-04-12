---
title: Crptography
date: 2025-04-12
categories: [Cyber Security Fundamentals]
tags: [Cyber, Cryptography, Encrytion, Symmetric Key, Asymmentric key]
author: Harmehar Kaur
image:
  path: /assets/crypto.jpg
  alt: crypto
---

## Cryptography Basics

Cryptography is the practice of securing information through the use of coded algorithms and techniques, making it unreadable to those without the appropriate access key. It protects information by keeping its content secret and unintelligible to anyone who cannot decrypt (unlock) it. It is the practice and study of techniques for secure communication and data protection, especially in the presence of adversaries or third parties. These adversaries should not be able to disclose or alter the contents of the messages.

---

### 🔐 Importance of Cryptography

Cryptography’s ultimate purpose is to ensure secure communication in the presence of adversaries. The term "secure" includes:

- **Confidentiality**
- **Integrity**
- **Authenticity**

---

### 🔄 Plaintext to Ciphertext

**Plaintext** is the data or message in its normal, unencrypted form. It can be:

- Image, audio, or video files in their raw or compressed forms  
- Human-readable text and numeric data, with or without markup  
- Database files or individual records and fields  
- Any other digital format that can be processed or stored  

> It’s important to remember that plaintext can be any digital form — not all of it is human-readable.

**Ciphertext** is the scrambled, unreadable version of the message after encryption. Ideally, no information about the original plaintext can be inferred from it.

**Cipher** is an algorithm or method that converts plaintext into ciphertext and back.

**Key** is a string of bits used by the cipher for encryption and decryption. The cipher is often public, but the key must remain secret unless it’s the public key in asymmetric encryption.

**Encryption** is the process of converting plaintext into ciphertext using a cipher and key.

**Decryption** is the reverse — converting ciphertext back into plaintext using the cipher and key.

![alt text](/assets/plaintext.jpg)

---

### 🏛️ Historical Ciphers

One early example is the **Caesar Cipher** from the first century BCE. It shifts each letter in the alphabet by a certain number to encrypt a message. However, this is insecure today because there are only 25 possible key variations — making it trivial to decrypt.

---

### 🔑 Types of Encryption

#### 1. **Symmetric Encryption**

- Uses the same key for both encryption and decryption.
- The decryption process is a mirror image of encryption.
- The message remains secure unless someone obtains the shared key.

**Challenges with symmetric encryption:**

- If a communication path is compromised, key sharing is risky.
- The key must be sent via a separate (out-of-band) channel — e.g., courier, fax, or phone.
- Anyone with access to the key can change the message.
- **Scalability:** Every unique pair of users needs a unique key.
  - An organization of 1,000 people would need **499,500** keys for private communication between everyone.

**Primary uses:**

- Encrypting bulk data (e.g., backups, hard drives, portable media)
- Encrypting messages in transit (e.g., IPsec, TLS)
- Streaming large-scale, time-sensitive data (e.g., video, gaming)

**Other names for symmetric encryption:**

- Same key
- Single key
- Shared key
- Secret key
- Session key

**Example: Substitution Cipher (Decoding Ring)**  
A substitution cipher replaces each letter (or bit) of plaintext with another based on a crypto-variable. These simple ciphers work well in theory but are often insecure without complexity.

---

#### 2. **Asymmetric Encryption**

- Uses a **pair of keys**: one for encryption and another for decryption.
- A cryptographic application or **Public Key Infrastructure (PKI)** generates the key pair:
  - One is **private** (kept secret).
  - The other is **public** (shared openly).

**How it works:**

- Anyone can encrypt a message using the **recipient’s public key**.
- Only the recipient with the **private key** can decrypt it.

**Benefits of asymmetric encryption:**

- Solves the **key distribution** problem — no need for prior secure key exchange.
- Enables additional features:
  - Non-repudiation of origin/delivery
  - Access control
  - Data integrity
- **Scalability**: Each person only needs a key pair (public + private).
  - An organization with 100,000 users only needs **200,000 keys**, much more efficient than symmetric systems.

**Limitations:**

- **Slow** compared to symmetric encryption
- Not practical for encrypting large data volumes or frequent, high-speed transactions

**Key Pair Use:**

- Encrypt with recipient's **public key** → decrypt with **private key**
- Sign with **private key** → verify with **public key**

As long as the private key is kept secret, this allows secure, verifiable communication.

![alt text](/assets/asymmetric_enc.jpg)
---


