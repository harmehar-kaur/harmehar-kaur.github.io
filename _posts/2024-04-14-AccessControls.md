---
title: Access controls
date: 2024-04-14
categories: [Cyber Security Fundamentals]
tags: [access controls, object, subject , rules]
author: Harmehar Kaur
image:
  path: /assets/cyber-prefix.png
  alt: 
---
XV.	Access controls: 
•	Access control involves limiting what objects can be available to what subjects according to what rules. One brief example of a control is a firewall, which is included in a system or network to prevent something from the outside from coming in and disturbing or compromising the environment. The firewall can also prevent information on the inside from going out into the Web where it could be viewed or accessed by unauthorized individual. It is about granting the appropriate level of access to authorized personnel and processes and denying access to unauthorized functions or individuals.
•	Access is based on the three elements: subject, object and rules.
•	Object
o		By definition, anything that a subject attempts to access is referred to as an object. An object is a device, process, person, user, program, server, client, or other entity that responds to a request for service. Whereas a subject is active in that it initiates a request for a service, an object is passive in that it takes no action until called upon by a subject. When requested, an object will respond to the request it receives, and if the request is wrong, the response will probably not be what the subject really wanted either. Note that by definition, objects do not contain their own access control logic. Objects are passive, not active (in access control terms), and must be protected from unauthorized access by some other layers of functionality in the system, such as the integrated identity and access management system.
o		
o		An object has an owner, and the owner has the right to determine who or what should be allowed access to their object. Quite often, the rules of access are recorded in a rule base or access control list.
o		
o		An object:
-	Is a building, a computer, a file, a database, a printer or scanner, a server, a communications resource, a block of memory, an input/output port, a person, a software task, a thread, or a process.
-	Is anything that provides service to a user.
-	Is passive.
-	Responds to a request.
-	May have a classification.
•	Rules
o	An access rule is an instruction developed to allow or deny access to an object by comparing the validated identity of the subject to an access control list. One example of a rule is a firewall access control list. By default, firewalls deny access from any address to any address, on any port. For a firewall to be useful, however, it needs more rules. A rule might be added to allow access from the inside network to the outside network. Here we are describing a rule that allows access to the object “outside network” by the subject having the address “inside network.” In another example, when a user (subject) attempts to access a file (object), a rule validates the level of access, if any, the user should have to that file.
o	To do this, the rule will contain or reference a set of attributes that define what level of access has been determined to be appropriate. A rule can:
-	Compare multiple attributes to determine appropriate access.
-	Allow access to an object.
-	Define how much access is allowed.
-	Deny access to an object.
-	Apply time-based access.
•	Subject 
•	A subject can be defined as any entity that requests access to assets. The entity requesting access may be a user, a client, a process, or a program, for example. A subject is the initiator of a request for service; therefore, a subject is referred to as “active.”
•	A subject:
-	Is a user, a process, a procedure, a client (or a server), a program, or a device such as an endpoint, workstation, smartphone, or removable storage device with onboard firmware.
-	Is active: It initiates a request for access to resources or services.
-	Requests a service from an object.
-	Should have a level of clearance (permissions) that relates to its ability to successfully access services or resources.
•	Physical access controls:
o	Physical access controls are items you can physically touch. They include physical mechanisms deployed to prevent, monitor, or detect direct contact with systems or areas within a facility. Examples of physical access controls include security guards, fences, motion detectors, locked doors/gates, sealed windows, lights, cable protection, laptop locks, badges, swipe cards, guard dogs, cameras, mantraps/turnstiles, and alarms.
o	Physical access controls are necessary to protect the assets of a company, including its most important asset: people. When considering physical access controls, the security of the personnel always comes first, followed by securing other physical assets.
o	Physical access controls prevent unauthorized individuals from entering a physical site, such as a workplace.
o	This is to protect not only physical assets such as computers from being stolen, but also the health and safety of the personnel inside.
o	Many types of physical access control mechanisms can be deployed in an environment to control, monitor, and manage access to a facility. These range from deterrents to detection mechanisms. Each area requires unique and focused physical access controls, monitoring, and prevention mechanisms.
o	mechanisms that may be used to control access to various areas of a site, including perimeter and internal security.
	 Badge Systems and Gate Entry:  Physical security controls for human traffic are often done with technologies such as turnstiles, mantraps, and remotely or system-controlled door locks. For the system to identify an authorized employee, an access control system needs to have some form of enrolment station used to assign and activate an access control device. Most often, a badge is produced and issued with the employee’s identifiers, with the enrolment station giving the employee specific areas that will be accessible. In high-security environments, enrolment may also include biometric characteristics. In general, an access control system compares an individual’s badge against a verified database. If authenticated, the access control system sends output signals allowing authorized personnel to pass through a gate or a door to a controlled area. The systems are typically integrated with the organization’s logging systems to document access activity (authorized and unauthorized). 
	Environmental Design: Crime Prevention through Environmental Design (CPTED) approaches the challenge of creating safer workspaces through passive design elements. This has great applicability for the information security community as security professionals design, operate, and assess the organizational security environment. Other practices, such as standards for building construction and data centres, also affect how we implement controls over our physical environment. Security professionals should be familiar with these concepts so they can successfully advocate for functional and effective physical spaces where information is created, processed, and stored. CPTED provides direction to solve the challenges of crime with organizational (people), mechanical (technology and hardware), and natural design (architectural and circulation flow) methods. By directing the flow of people using passive techniques to signal who should and should not be in a space and providing visibility to otherwise hidden spaces, the likelihood that someone will commit a crime in that area decreases.
	 Biometrics: To authenticate a user’s identity, biometrics use characteristics unique to the individual seeking access. A biometric authentication solution entails two processes:
•	Enrolment. During the enrolment process, the user’s registered biometric code is stored either in a system or on a smart card that is kept by the user.
•	Verification. During the verification process, the user presents their biometric data to the system so that the biometric data can be compared with the stored biometric code.
Even though the biometric data may not be secret, it is personally identifiable information, and the protocol should not reveal it without the user’s consent. Biometric takes two primary forms: physiological and behavioural.
	 Physiological: Physiological systems measure the characteristics of a person such as a fingerprint, iris scan (the coloured portion around the outside of the pupil in the eye), retinal scan (the pattern of blood vessels in the back of the eye), palm scan, and venous scans that look for the flow of blood through the veins in the palm. Some biometrics devices combine processes together—such as checking for pulse and temperature on a fingerprint scanner—to detect counterfeiting.
	Behavioural: Behavioural systems measure how a person acts by measuring voiceprints, signature dynamics, and keystroke dynamics. As a person types, a keystroke dynamics system measures behaviour such as the delay rate (how long a person holds down a key) and transfer rate (how rapidly a person moves between keys). Biometric systems are considered highly accurate, but they can be expensive to implement and maintain because of the cost of purchasing equipment and registering all users. Users may also be uncomfortable with the use of biometrics, considering them to be an invasion of privacy or present a risk of disclosure of medical information (since retina scans can disclose medical conditions). A further drawback is the challenge of sanitization of the devices.
•	Logical access control:
o	Whereas physical access controls are tangible methods or mechanisms that limit someone from getting access to an area or asset, logical access controls are electronic methods that limit someone from getting access to systems, and sometimes even to tangible assets or areas.
o	Types of logical access controls include:
	 Passwords
	 Biometrics (implemented on a system, such as a smartphone or laptop)
	 Badge/token readers connected to a system
o	These types of electronic tools limit who can get logical access to an asset, even if the person already has physical access.
o	Biometrics implemented on a system, such as a smartphone, is an example of a logical access control method.
o	Limiting access to data on the network would be considered a logical or technical control.
•	Mandatory access control
o	Mandatory access control is determined by the owner of the assets, on an across-the-board basis, with little individual decision-making about who gets access. For example, at certain government agencies, personnel must have a certain type of security clearance to get access to certain areas. In general, this level of access is set by government policy and not by an individual giving permission based on their own judgment. 
o	Often this is accompanied by separation of duties, where the scope of work is limited and users do not have access to information that does not concern them. This separation of duties is also facilitated by role-based access control.	
o	A mandatory access control (MAC) policy is one that is uniformly enforced across all subjects and objects within the boundary of an information system. In simplest terms, this means that only properly designated security administrators, as trusted subjects, can modify any of the security rules that are established for subjects and objects within the system. This also means that for all subjects defined by the organization (that is, known to its integrated identity management and access control system), the organization assigns a subset of total privileges for a subset of objects, such that the subject is constrained from doing any of the following:
-	Passing the information to unauthorized subjects or objects
-	Granting its privileges to other subjects
-	Changing one or more security attributes on subjects, objects, the information system or system components
-	Choosing the security attributes to be associated with newly created or modified objects
-	Changing the rules governing access control	
o	Although MAC sounds very similar to DAC, the primary difference is who can control access. With Mandatory Access Control, it is mandatory for security administrators to assign access rights or permissions; with Discretionary Access Control, it is up to the object owner’s discretion.
•	Discretionary access control:
o		Discretionary access control (DAC) is a specific type of access control policy that is enforced over all subjects and objects in an information system. In DAC, the policy specifies that a subject who has been granted access to information can do one or more of the following:
	Pass the information to other subjects or objects
	Grant its privileges to other subjects
	Change security attributes on subjects, objects, information systems, or system components
	Choose the security attributes to be associated with newly created or revised objects
	Change the rules governing access control; mandatory access controls restrict this capability. 	
o	Discretionary access control systems allow users to establish or change these permissions on files they create or otherwise have ownership of. Steve and Aidan, for example, are two users (subjects) in a UNIX environment operating with DAC in place. Typically, systems will create and maintain a table that maps subjects to objects, as shown in the image. At each intersection is the set of permissions that a given subject has for a specific object.
o	Many operating systems, such as Windows and the whole Unix family tree (including Linux) and iOS, use this type of data structure to make fast, accurate decisions about authorizing or denying an access request. Note that this data can be viewed as either rows or columns:
	An object’s access control list shows the total set of subjects who have any permissions at all for that specific object.
	A subject’s capabilities list shows each object in the system that said subject has any permissions for.

o	This methodology relies on the discretion of the owner of the access control object to determine the access control subject’s specific rights. Hence, security of the object is literally up to the discretion of the object owner. Most information systems are DAC systems. In a DAC system, a user who has access to a file is able to share that file with or pass it to someone else. It is at the discretion of the asset owner whether to grant or revoke access for a user. For access to computer files, this can be shared file or password protections
o	DACs are not very scalable; they rely on the access control decisions made by each individual object owner, and it can be difficult to find the source of access control issues when problems occur.
•	Role based access control
o	Role-based access control provides each worker privileges based on what role they have in the organization. Only Human Resources has access to personnel files, for example; only Finance has access to bank accounts; each manager has access to their own direct reports and their own department. Very high-level system administrators may have access to everything; new employees would have very limited access, the minimum required to do their jobs.
o	Monitoring these role-based permissions is important because if one person’s permissions are expanded for a specific reason—say, a junior worker’s permissions might be expanded so they can temporarily act as the department manager—but their permissions aren’t changed back when the new manager is hired, then the next person to come in at that junior level might inherit those permissions when it is not appropriate for them to have them. This is called privilege creep or permissions creep. 
o	Having multiple roles with different combinations of permissions can require close monitoring to make sure everyone has the access they need to do their jobs and nothing more. In this world where jobs are ever-changing, this can sometimes be a challenge to keep track of, especially with extremely granular roles and permissions. 
o	Upon hiring or changing roles, a best practice is to not copy user profiles to new users. It is recommended that standard roles are established, and new users are created based on those standards rather than an actual user. That way, new employees start with the appropriate roles and permissions.
o	Privilege creep (or permissions creep) is the term which refers to someone inheriting expanded permissions that are not appropriate for their role in RBAC.
