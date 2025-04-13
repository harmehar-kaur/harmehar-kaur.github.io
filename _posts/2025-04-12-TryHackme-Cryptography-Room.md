---
title: Cryptography Rooms Writeup
date: 2025-04-12
categories: [TryHackme Writeups]
tags: [Cyber, Cryptography, Encryption, Public Key]
author: Harmehar
image:
  path: /assets/crypto.jpg
  alt: crypto
---

## Room: Cryptography Basics

---

### Task 2: Importance of Cryptography

**What is the standard required for handling credit card information?**

---

### Task 3: Plaintext to Cipher Text

**What do you call the encrypted plaintext?**  
ciphertext

**What do you call the process that returns the plaintext?**  
decryption

---

### Task 4: Historical Ciphers

**Knowing that XRPCTCRGNEI was encrypted using Caesar Cipher, what is the original plaintext?**

---

### Task 5: Encryption

**Should you trust DES? (Yea/Nay)**  
Nay

**When was AES adopted as an encryption standard?**  
2001

---

### Task 6: Basic Math

**What’s 1001 ⊕ 1010?**  
0011

**What’s 118613842 % 9091?**  
3565

**What’s 60 % 12?**  
0

---

## Room: Public Key Cryptography Basics

---

### Task 1

**In the analogy presented, what real object is analogous to the public key?**  
Answer: Lock

---

### Task 2

**Knowing that p = 4391 and q = 6659. What is n?**  
Answer: 29239669

**Knowing that p = 4391 and q = 6659. What is ϕ(n)?**  
Answer: 29228620

---

### Task 3

**Consider p = 29, g = 5, a = 12. What is A?**  
Answer: 7

**Consider p = 29, g = 5, b = 17. What is B?**  
Answer: 9

**Knowing that p = 29, a = 12, and you have B from the second question, what is the key calculated by Bob?**  
Answer: 24

**Knowing that p = 29, b = 17, and you have A from the first question, what is the key calculated by Alice?**  
Answer: 24

---

### Task 4

**Check the SSH Private Key in `~/Public-Crypto-Basics/Task-5`. What algorithm does the key use?**  
Answer: RSA

```bash
ssh-keygen -l -f ~/Public-Crypto-Basics/Task-5
```

---

### Task 5

**What does a remote web server use to prove itself to the client?**  
Answer: Certificate

**What would you use to get a free TLS certificate for your website?**  
Answer: Let’s Encrypt

---

### Task 6

**Use GPG to decrypt the message in `~/Public-Crypto-Basics/Task-7`. What secret word does the message hold?**  
Answer: Pineapple

```bash
gpg --decrypt ~/Public-Crypto-Basics/Task-7
```

---

## Room: Hashing Basics

---

### Task 2

**What is the SHA256 hash of the `passport.jpg` file in `~/Hashing-Basics/Task-2`?**  
77148c6f605a8df855f2b764bcc3be749d7db814f5f79134d2aa539a64b61f02

**What is the output size in bytes of the MD5 hash function?**  
16

**If you have an 8-bit hash output, how many possible hash values are there?**  
256

---

### Task 3

**What is the 20th password in `rockyou.txt`?**  
qwerty

```bash
head -20 path/to/rockyou.txt
```

---

### Task 4

**Manually check the hash “4c5923b6a6fac7b7355f53bfe2b8f8c1” using the rainbow table above.**  
inS3CyourP4$$

**Crack the hash “5b31f93c09ad1d065c0491b764d04933” using an online tool.**  
tryhackme

**Should you encrypt passwords in password-verification systems? Yea/Nay**  
Nay

---

### Task 5

**What is the hash size in yescrypt?**  
256

**What’s the Hash-Mode listed for Cisco-ASA MD5?**  
2410

**What hashing algorithm is used in Cisco-IOS if it starts with `$9$`?**  
scrypt

---

### Task 6

**Use hashcat to crack the following hashes:**

1. **Hash in `hash1.txt`**  
Answer: 85208520  
```bash
hashcat -m 3200 -a 0 ~/Hashing-Basics/Task-6/hash1.txt /usr/share/wordlists/rockyou.txt
```

2. **SHA2-256 hash in `hash2.txt`**  
Answer: halloween  
```bash
hashcat -m 1400 -a 0 ~/Hashing-Basics/Task-6/hash2.txt /usr/share/wordlists/rockyou.txt
```

3. **Hash in `hash3.txt`**  
Answer: spaceman  
```bash
hashcat -m 1800 -a 0 ~/Hashing-Basics/Task-6/hash3.txt /usr/share/wordlists/rockyou.txt
```

4. **Hash in `hash4.txt`**  
Answer: funforyou

---

### Task 7

**What is SHA256 hash of `libgcrypt-1.11.0.tar.bz2` found in `~/Hashing-Basics/Task-7`?**  
09120c9867ce7f2081d6aaa1775386b98c2f2f246135761aae47d81f58685b9c

**What’s the hashcat mode number for HMAC-SHA512 (key = $pass)?**  
1750

---

### Task 8

**Use base64 to decode `RU5jb2RlREVjb2RlCg==`, saved as `decode-this.txt` in `~/Hashing-Basics/Task-8`. What is the original word?**  
Answer: ENcodeDEcode

```bash
base64 -d ~/Hashing-Basics/Task-8/decode-this.txt
```

