---
title: Understanding Office Trust Records in DFIR  
date: 2024-12-05  
categories: [DFIR]  
tags: [DFIR, Forensics, Office, Trust Records, Artifacts]  
author: Harmehar Kaur  
image:  
  path: /assets/forensics.jpg  
  alt: Office Trust Records  
---

In the world of **Digital Forensics and Incident Response (DFIR)**, understanding how users interact with documents is crucial. One key artifact that often surfaces in investigations is the **Office Trust Records**. These records provide insight into how a user trusted a document when presented with a security warning, which can help investigators understand user behavior and document interactions.

---

### What Are Office Trust Records?

**Office Trust Records** are created when a user is presented with a security warning upon opening a document (such as a warning about macros, external content, or file sources). These records help ensure that the user only needs to grant permission once, as the system will remember their decision for subsequent openings of the same document.

Office Trust Records are valuable in that they record several key details, including:

- The **file path** of the document.
- The **time** the document was trusted.
- Which **permissions** were granted by the user when they decided to trust the document.

---

### Where Are Office Trust Records Stored?

The information about trusted documents and the user's interaction with them is stored in the **NTUSER.dat** hive, specifically in the following location:

- `NTUSER\Software\Microsoft\Office\<version>\Security\Trusted Documents\TrustRecords`

This registry key contains the trust records for documents, providing essential context about how a user interacted with potentially risky files.

---

### Why Is This Artifact Useful in DFIR?

The **Office Trust Records** are valuable in a DFIR investigation for a few key reasons:

1. **Document Interaction:** They show which documents were trusted by the user, providing evidence of document access and trust decisions.
2. **Permissions History:** By reviewing these records, an investigator can determine what permissions the user granted, such as enabling macros or allowing external content to be loaded.
3. **Timeline:** The timestamp in the trust record helps establish a timeline of when the document was first trusted, which can be used to corroborate other findings.

By examining **Office Trust Records**, investigators can better understand the user's behavior, what documents were interacted with, and whether those documents posed any potential security risks.

---

### Conclusion

In **Digital Forensics**, artifacts like **Office Trust Records** can provide valuable insight into user activity, specifically their interaction with documents that might have triggered security warnings. These records can help investigators piece together a clearer picture of what occurred on a system, especially in cases involving document-based threats or suspicious activity.

