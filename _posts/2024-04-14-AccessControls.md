---
title: "🛡️ Understanding Access Controls: Who Gets In, Who Stays Out, and Why It Matters"
date: 2024-04-14
categories: [Cyber Security Fundamentals]
tags: [access controls, object, subject, rules]
author: Harmehar Kaur
image:
  path: /assets/cyber-prefix.png
  alt: access control
---

In the world of cybersecurity, one of the most important questions is: **Who should have access to what — and when?** That’s where **access controls** come in.

Access control is about ensuring the right people (or systems) have access to the right resources, while keeping everyone else out. It sounds simple — but there's a lot going on behind the scenes. Let’s break it down together.

---

## 🔑 What Are Access Controls?

Access control limits what **objects** can be accessed by which **subjects**, based on **rules**.

Think of it like a security checkpoint. Only those with proper clearance get through — everyone else gets stopped at the door.

For example: A firewall can block outsiders from sneaking into your internal network, or prevent internal data from leaking out to the internet.

---

## 👥 Subjects, 🗂️ Objects, and ⚖️ Rules

### 🧑 Subject
The **subject** is the one making the request — a user, device, process, or program trying to access something.

- **Examples**: A person using a laptop, a mobile app, a background service
- **Key traits**: Active, initiates access, must have appropriate permissions

### 📁 Object
The **object** is what the subject is trying to access — like a file, database, printer, or network resource.

- **Examples**: Files, servers, buildings, memory blocks
- **Key traits**: Passive, responds to the subject’s request, has an owner

### 🧾 Rules
Rules determine **who gets what access** — and how much.

- Can allow, deny, or limit access
- May include time-based access, attribute-based filtering, or access control lists
- Example: A firewall rule that allows outbound access from the internal network to the internet

---

## 🧱 Types of Access Controls

### 🏢 Physical Access Controls
These are real-world controls you can touch — used to secure physical spaces.

- **Examples**: Swipe cards, security guards, locked doors, fences, CCTV, mantraps
- **Goal**: Protect people, property, and equipment from unauthorized physical access

#### A Few Notable Mechanisms:
- **Badge systems & turnstiles**: Verify identity before allowing entry
- **Environmental design (CPTED)**: Use layout and design to reduce crime risks
- **Biometrics**: Authenticate with unique human traits like fingerprints or iris scans
- - *Physiological*: Fingerprint, palm, iris
- - *Behavioral*: Voice, keystroke rhythm, signature

---

### 💻 Logical (Technical) Access Controls

These are **electronic** methods that limit access to systems, software, and data.

- **Examples**: Passwords, tokens, biometrics (on devices), system-based role restrictions
- **Goal**: Enforce access control digitally — even if someone is already inside the physical space

---

## 🔐 Access Control Models

Now let’s talk about the different **models or strategies** used to grant or restrict access.

### 📜 Mandatory Access Control (MAC)
- Access is set by a central authority (e.g., government or admin)
- Subjects can't modify access levels
- Great for environments requiring strict classification (e.g., military, government)

### 🧍 Discretionary Access Control (DAC)
- Object owners decide who can access their resources
- Users can share or restrict files as they wish
- Common in personal and business systems (like Windows, Linux, Unix)

### 🧑‍💼 Role-Based Access Control (RBAC)
- Access is based on a person’s **role** in the organization
- HR sees employee records, finance sees bank accounts, etc.
- Helps prevent over-permissioning, but requires good management to avoid **privilege creep**

---

## ⚠️ What’s Privilege Creep?

This happens when someone accumulates more access than they actually need — often due to role changes or temporary promotions that never get reset.

- **Solution**: Periodically review access rights and avoid cloning user roles when onboarding new staff.

---

## 🧠 Final Thoughts

Access control is about more than just passwords — it's about creating structured, layered security that ensures people (and systems) can only access what they’re supposed to.

From physical barriers like mantraps to digital rules about who can read or write to a file, access controls are foundational to every strong cybersecurity posture.

So next time you’re asked, *“Who has access to that?”* — you’ll know exactly how to answer (and more importantly, how to manage it).

Stay safe, stay in control! 🔐

---
