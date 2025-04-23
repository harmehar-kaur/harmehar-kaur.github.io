---
title: MS Word Reading Locations in DFIR  
date: 2024-12-04  
categories: [DFIR]  
tags: [DFIR, Forensics, MS Word, Reading Locations, Artifacts]  
author: Harmehar Kaur  
image:  
  path: /assets/forensics.jpg  
  alt: MS Word Reading Locations  
---

When performing **Digital Forensics and Incident Response (DFIR)** investigations, tracking a user’s activity within documents can be crucial. One useful artifact to look at is the **MS Word Reading Location**, a feature introduced with **Word 2013**. This data can reveal the last known position of a user in a document, providing insight into what they were working on, even after closing the document.

---

### What Are MS Word Reading Locations?

MS Word keeps track of the user's last location in a document—whether it's text, a table, or any other section—so that they can return to it when they next open the document. This reading location data is stored for each document the user works on, and it includes details such as:

- The **last opened date**.
- The **last closed time**.
- The **last position** within the document, so the user can pick up where they left off.

These details, when combined with the **Office file MRU (Most Recently Used) key**, can also help determine the **last session duration** and provide additional context to the user’s actions.

---

### Where Is This Data Stored?

The **MS Word Reading Locations** data is stored in the **Windows registry**, specifically under the following location:

- `NTUSER\Software\Microsoft\Office\<version>\Word\Reading Locations`

This registry key will contain the data for the last known position within the document and the relevant timestamps.

---

### Why Is This Artifact Useful in DFIR?

For investigators, the MS Word **Reading Locations** data is particularly valuable as it can provide a snapshot of what the user was doing at a specific point in time. By examining this artifact, you can determine:

- What documents were being actively worked on.
- Where the user was last within the document, allowing for a deeper understanding of the user's activities.
- The timing of the document's last interaction, which can help piece together a timeline of events.

This artifact can provide key evidence in both **forensics investigations** and **incident response** scenarios, especially when trying to understand user behavior or reconstruct events leading up to or following an incident.

---

### Conclusion

The **MS Word Reading Locations** artifact may seem like a small piece of the puzzle, but it can offer valuable insights into a user's behavior and document interactions. By understanding where this data is stored and how it can be interpreted, DFIR professionals can add another layer to their investigation, offering a clearer view of the user's actions during the period of interest.

