---
title: Forensics 
date: 2024-11-05
categories: [Windows Forensics, DFIR]
tags: [Forensics, Forensic Procedure, Chain of Custody]
author: Harmehar Kaur
image:
  path: /assets/forensics.jpg
  alt: Cyber
---

## Digital Forensics

The use of science and mathematics to investigate crimes and establish facts is the foundation of forensics. More specifically, **digital forensics** is the process of uncovering and interpreting electronic data. The goal is to preserve evidence in its most original form while conducting a structured investigation by collecting, identifying, and validating digital information to reconstruct past events. 

> “The context is most often for the usage of data in a court of law, though digital forensics can be used in other instances.” – Techopedia

---

### Types of Forensic Investigations

There are broadly two types of investigations in which forensics can be used:

- **Private Sector Investigations:**  
  These are initiated by corporate entities or private individuals to investigate internal incidents, such as employee misconduct or breaches caused by threat actors compromising infrastructure or sensitive data.

- **Public Investigations:**  
  These are legal investigations carried out by government agencies or prosecutors to support the occurrence of a crime or prove a digital crime in a court of law.

---

### Key Considerations During a Forensic Investigation

- **Legal Authority:**  
  Investigators must have the appropriate legal authority before initiating any actions.

- **Chain of Custody:**  
  A meticulous chain of custody must be maintained to track who has handled the evidence at any given time.

- **Mathematical Validation:**  
  Hash functions are used to ensure the integrity of files, verifying that data remains unaltered.

- **Validated Tools:**  
  Forensic tools must be validated to confirm they operate accurately. For instance, when creating a disk image, it's crucial to ensure it's an exact replica of the original.

- **Repeatability:**  
  Results should be reproducible when the same tools and procedures are applied by other qualified individuals.

- **Reporting:**  
  A comprehensive report must be generated at the conclusion of the investigation, detailing the evidence and findings relevant to the case.

---

### Forensic Investigation Procedure (DFIR Perspective)

1. **First Response:**  
   Actions taken immediately after a security incident, depending on the nature and scope of the incident.

2. **Search and Seizure:**  
   Identifying and securing the compromised system or device to prevent further damage or evidence loss.

3. **Collect the Evidence:**  
   Using forensically sound methods to gather data such as forensic images, triage data, memory dumps, or log files.

4. **Secure the Evidence:**  
   Ensuring evidence is protected from tampering, which would compromise its admissibility.

5. **Data Acquisition:**  
   Retrieving data of interest (e.g., registry files, password dumps, malware traces) to help prove or disprove a hypothesis.

6. **Data Analysis:**  
   Examining, identifying, separating, converting, and modeling the data to extract meaningful insights and evidential artifacts.

7. **Evidence Assessment:**  
   Linking the analyzed data to the incident and evaluating its relevance and impact.

8. **Documentation/Reporting:**  
   Compiling all findings into a concise, well-organized report with supporting evidence and detailed documentation.

---
