---
title: "Understanding Hashes and Cracking with John the Ripper"
date: 2025-04-27
categories: Cryptography, Penetration Testing
tags: Hashing, John the Ripper, Cybersecurity, Dictionary Attack, Wordlist
author: Harmehar Kaur
image:
  path: /assets/forensics.jpg
  alt: A visual representation of cryptography concepts
---

This room requires basic knowledge of various cryptography terms. For your convenience, we review the most relevant terms and concepts before we move into practical hash cracking.

## What are Hashes?

A hash is a way of taking a piece of data of any length and representing it in another fixed-length form. This process masks the original value of the data. The hash value is obtained by running the original data through a hashing algorithm. Many popular hashing algorithms exist, such as MD4, MD5, SHA1, and NTLM. Let’s try and show this with an example:

If we take “polo”, a string of four characters, and run it through an MD5 hashing algorithm, we end up with an output of `b53759f3ce692de7aff1b5779d3964da`, a standard 32-character MD5 hash.

Likewise, if we take “polomints”, a string of 9 characters, and run it through the same MD5 hashing algorithm, we end up with an output of `584b6e4f4586e136bc280f27f9c64f3b`, another standard 32-character MD5 hash.

## What Makes Hashes Secure?

Hashing functions are designed as one-way functions. In other words, it is easy to calculate the hash value of a given input; however, it is a hard problem to find the original input given the hash value. In simple terms, a hard problem quickly becomes computationally infeasible in computer science.

In computer science, P and NP are two classes of problems that help us understand the efficiency of algorithms:

- **P (Polynomial Time)**: Class P covers the problems whose solution can be found in polynomial time.
- **NP (Non-deterministic Polynomial Time)**: Problems in the class NP are those for which a given solution can be checked quickly, even though finding the solution itself might be hard.

While the algorithm to hash the value will be "P" and can be calculated reasonably, an "un-hashing" algorithm would be "NP" and intractable to solve, meaning that it cannot be computed in a reasonable time using standard computers.

## Where John Comes in

Even though the algorithm is not feasibly reversible, cracking hashes isn’t impossible. If you have the hashed version of a password, for example, and you know the hashing algorithm, you can use that algorithm to hash a large number of words, called a dictionary. You can then compare these hashes to the one you’re trying to crack to see if they match. If they do, you know what word corresponds to that hash — you’ve cracked it!

This process is called a **dictionary attack**, and **John the Ripper**, or **John**, is a tool for conducting fast brute-force attacks on various hash types.

## Wordlists

Now that we have John ready, we must consider another indispensable component: wordlists.

To use a dictionary attack against hashes, you need a list of words to hash and compare. Unsurprisingly, this is called a wordlist. There are many different wordlists out there, and a good collection can be found in the SecLists repository.

For all of the tasks in this room, we will use the infamous **rockyou.txt** wordlist, a very large common password wordlist obtained from a data breach on a website called rockyou.com in 2009.

## John Basic Syntax

The basic syntax of John the Ripper commands is as follows:

```bash
john [options] [file path]
```

- **john**: Invokes the John the Ripper program
- **[options]**: Specifies the options you want to use
- **[file path]**: The file containing the hash you’re trying to crack; if it’s in the same directory, you won’t need to name a path, just the file.

## Automatic Cracking

John has built-in features to detect what type of hash it’s being given and to select appropriate rules and formats to crack it for you. To do this, we use the following syntax:

```bash
john --wordlist=[path to wordlist] [path to file]
```

Example Usage:

```bash
john --wordlist=/usr/share/wordlists/rockyou.txt hash_to_crack.txt
```

## Identifying Hashes

Sometimes, John won’t play nicely with automatically recognising and loading hashes, but that’s okay! We can use other tools to identify the hash type and then set John to a specific format.

One tool is **hash-identifier**, a Python tool that can help you determine the hash format.

To use **hash-identifier**, you can use the following commands:

```bash
wget https://gitlab.com/kalilinux/packages/hash-identifier/-/raw/kali/master/hash-id.py
python3 hash-id.py
```

## Format-Specific Cracking

Once you have identified the hash that you’re dealing with, you can tell John to use it while cracking the provided hash using the following syntax:

```bash
john --format=[format] --wordlist=[path to wordlist] [path to file]
```

For example:

```bash
john --format=raw-md5 --wordlist=/usr/share/wordlists/rockyou.txt hash_to_crack.txt
```

## NTHash / NTLM

NThash is the hash format modern Windows operating system machines use to store user and service passwords. It’s also commonly referred to as **NTLM**. NThash is used in Windows systems to store user passwords and can be cracked in similar ways as the methods we’ve discussed.

## Single Crack Mode

John also has another mode called **Single Crack Mode**. In this mode, John uses only the information provided in the username to try and work out possible passwords heuristically by slightly changing the letters and numbers contained within the username.

For example, consider the username “Markus”. Some possible passwords could be:

- Markus1
- MArkus
- Markus!

John's word mangling feature helps generate these variations, creating a more effective password list based on these patterns.

## Using Single Crack Mode

To use single crack mode, we use the following syntax:

```bash
john --single --format=[format] [path to file]
```

## Custom Rules

Custom rules are defined in the **john.conf** file and let you create dynamic wordlists based on specific patterns. If you know the likely structure of a password, custom rules can help you generate passwords that match.

For example, if you suspect the password follows a pattern like **Polopassword1!**, you could define a custom rule to dynamically create variations of it.

---

Now, with all these tools and techniques in mind, you're ready to start cracking some hashes! Whether you're using dictionary attacks, single crack mode, or custom rules, John the Ripper gives you a powerful set of options to get the job done. Keep experimenting, and remember that practice is key to mastering these techniques.
