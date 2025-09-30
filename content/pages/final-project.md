---
content_type: page
description: This section provides details on the final project for the course, including
  due dates, an introduction, deliverables, and suggested project ideas.
draft: false
learning_resource_types:
- Projects
ocw_type: CourseSection
title: Final Project
uid: a8bc830d-8425-c49a-5db9-c42fab665c47
video_files:
  video_thumbnail_file: null
video_metadata:
  youtube_id: null
---
This course makes use of Athena, MIT's UNIX-based computing environment. OCW does not provide access to this environment.

**Idea discussions due:** One day after Lecture 13

**Proposals due:** Two days after Quiz 1

**Presentations due:** Lecture 24 (in class)

**Code and write-up due:** Two days after Lecture 24 (5:00pm)

## Introduction

In this lab, you will work on a final project of your own choice. Unlike in previous labs, you will work in groups of 3–4 for the final project. You will be required to turn in both your code and a short write-up describing the design and implementation of your project, and to make a short in-class presentation about your work. We will post your write-up and code on the web site after the end of the semester, unless you explicitly talk to us about why you want to keep yours confidential.

The primary requirement is that your project be something interesting. Your project should also have something to do with security, but that's relatively easy, and it's much more important for your project to be interesting.

We encourage students to choose any project idea that you might think is interesting. If you are not sure, we provides you with two kinds of ideas. First, we present two reasonably well-defined starting points for projects. Second, we give a list of half-baked ideas that we think could turn into an interesting project, but we haven't given them too much thought.

We encourage final projects that leverage multiple classes you might be taking, or that involve other research or projects you are already working on. For example, if you are also taking {{% resource_link "773688e1-8408-4bf0-b0c9-f1c078a0279c" "*6.828 Operating System Engineering*" %}} or 6.S897 (elections and voting technology), it would be fine with us to have a single project that counts for both 6.858 and another class. Same for other upper-level course-6 classes or MEng and AUP projects.

Most of the {{% resource_link "45214083-1e68-402e-abbd-b16a2d3f9777" "final projects from last year are posted online" %}}. Several final projects from previous years ended up being subsequently published as research papers (e.g., {{% resource_link "07715339-3183-4b09-ad88-8cd4c01f5d38" "UserFS (PDF)" %}}, {{% resource_link "2d2e4c99-eada-4bed-aa90-d846580867ce" "BStore (PDF)" %}}, and {{% resource_link "7ca76014-824e-4b50-92db-aa37bba64cad" "LXFI (PDF)" %}}). If this sounds interesting to you, try to pick an ambitious class project that you might want to continue working on afterwards!

## Deliverables

There are four concrete steps to the final project, as follows:

### 1\. Form a Group

Decide on the project you would like to work on, and post a short summary of your idea (one to two paragraphs). Discuss ideas with others. Use these discussions to help find other students interested in similar ideas for forming a group. Course staff will provide feedback on project ideas; if you'd like more detailed feedback, come chat with us in person.

### 2\. Project Proposal

Discuss your proposed idea with course staff over the next week, before the proposal deadline, to flesh out the exact problem you will be addressing, how you will go about doing it, and what tools you might need in the process. By the proposal deadline, you must submit a one-to-two-page proposal describing:

- Your group members list
- The problem you want to address
- How you plan to address it
- What are you proposing to specifically design and implement

### 3\. Project Presentation

Prepare a short in-class presentation about the work that you have done for your final project. We will provide a projector that you can use to demonstrate your project. Depending on the number of groups and the kinds of projects that each group chooses, we may decide to limit the total number of presentations, and some groups might end up not presenting in class.

### 4\. Write-up and Code

Write a document describing the design and implementation of your project, and turn it in along with your project's code by the final deadline. The document should be about 2–3 pages of text that helps us understand what problem you solved, and what your code does. The code and writeups will be posted online after the end of the semester. Take a look at the list of writeups from past years ({{% resource_link "c095ed5e-0b88-43b0-aa15-b22e53c0b61b" "2012" %}} and {{% resource_link "45214083-1e68-402e-abbd-b16a2d3f9777" "2013" %}}) to get a sense of what this writeup should look like.

## Well-defined Starting Points

We provide two starting points if you want a well-defined project. One involves building a defensive system, namely an encrypted file system that allows users to share data through an untrusted server. The other involves finding vulnerabilities in existing systems, namely in various MIT services that IS&T runs.

## Encrypted File System

Your goal for this project idea is to develop a file system that allows users to store data on an untrusted file server. The file server should not be able to obtain the user's plaintext data (i.e., your file system should encrypt the data), and the file server should not be able to corrupt the data either (i.e., your file system should authenticate the data it gets back from the file server).

Your file system should support many users, and allow users to share files with one another. For each file, it should be possible to control the set of users who can read, and who can write, to that file.

At a minimum, your file system should meet the following requirements:

- Users can create, delete, read, write, rename files.
- The file system should support directories, much like the Unix file system.
- Users should be able to set permissions on files and directories, which also requires that your file system be able to name users.
- File names (and directory names) should be treated as confidential.
- Users should not be able to modify files or directories without being detected, unless they are authorized to do so.
- If the server is not malicious, unauthorized users should not be able to corrupt the file system.
- The file server should not be able to read file content, file names, or directory names.
- The server should not be able to take data from one file and supply it in response to a client reading a different file.
- A malicious file server should not be able to create or delete files or directories without being detected.

The final result of this project should be a functional file system implementation that meets the above requirements. You can implement your prototype in any language you want, such as Python or C++ or Go. You can decide how the file system client and server should be run. One reasonable design would be to have the file system client provide a minimal shell environment that allows users to perform the operations described in the above requirements.

As a challenge, you may want to think about providing freshness guarantees: that is, that a client should always see the latest version of a file, or at least that a client should never see an older version of a file after it sees a newer one. The {{% resource_link "225dad53-fb32-4e98-84d9-8368e74ab18c" "SUNDR file system (PDF)" %}} may provide some inspiration for this, although it is a rather complicated system. You can choose to implement some limited freshness guarantees, unlike SUNDR's ideal fork consistency.

As another challenge, you may want to think about integrating your file system with the OS of your choosing. You may find {{% resource_link "bbd8bfee-49a8-4bdb-adc7-84085ed5c10b" "FUSE" %}} helpful for this.

## Looking for Vulnerabilities

If you are interested in a more attack-oriented final project, your goal for this project is to pick an interesting service provided by MIT's IS&T (or any other computing service at MIT, such as those provided by SIPB), and try to find vulnerabilities in it. We will judge your project based on what kinds of vulnerabilities you find. Beware that there's no guarantee of success with this (or any other attack-oriented) project, because you may accidentally choose a very secure service, and might end up finding no vulnerabilities, which can potentially result in a failing grade. However, if you have an interesting approach to finding vulnerabilities (e.g., you have designed a new tool for finding bugs), you may receive a good grade even without finding real vulnerabilities.

**Important:** In any attack-oriented project, you must be very careful to avoid disrupting existing services, inconveniencing users of those services, compromising the security of that service, or taking advantage of any vulnerabilities you find. If you are ever in doubt, please get in touch with us. If you discover real vulnerabilities in a service, please get in touch both with the operators of that service and with us. Please don't exploit the vulnerability to gain any additional privileges on a service, and don't announce it widely before the service operators have a chance to understand it.

Your grade in this project depends on how interesting the vulnerabilities are that you have found, or how interesting the techniques are that you used to discover those vulnerabilities. For example, obtaining passwords through traditional brute-forcing techniques is not interesting. The general scale of work expected should be comparable to the amount of work involved in building a file system (see project above). Of course, much of your work will involve reading and understanding an existing system, and carefully constructing proof-of-concent exploits to demonstrate the vulnerabilities that you discovered, and the total amount of resulting code may be minimal; think back to how much time you spent on lab 1, and how many lines of code your final exploits were.

## Half-baked Project Ideas

If you are interested in working on something other than the two projects proposed above, here are some half-baked ideas. Use them to come up with more well-defined projects; we expect the final work to be comparable in terms of total effort to the two well-defined projects listed above. Of course, we encourage you to come up with your own ideas for what you would like to work on; there's no need to restrict yourself to this list.

- Get the concolic execution system from lab 3 to work on real-world Python web applications, and try to find real bugs.
- Write an interesting web application in Ur / Web.
- Modify Linux to keep track of the last process and user that modified each file. Perhaps log a warning or raise an alarm when a file is modified by an application that hasn't written to that file before.
- Build a static analysis tool to find bugs in real web applications. It would be great to have a static analysis tool for Python programs, even if it's not perfectly sound, much like the PHP static analysis tool we discussed in lecture. In addition to the standard XSS bugs, can you find bugs where application developers forget to perform permission checks, or inadvertently leak sensitive data? Such a tool might also be useful to find non-security bugs in Python programs. One existing tool that's quite limited is {{% resource_link "270b27a9-aaf5-4313-9813-7b513a213e75" "PyLint" %}}.
- Find bugs in real C code. Take a look at some recent research papers on finding real bugs in the Linux kernel and other C-based programs, involving {{% resource_link "9cc3f38d-f283-479a-afb3-abc11deb4629" "integer errors (PDF)" %}} or {{% resource_link "0c475330-52ee-446d-9d1b-f94c5df63485" "undefined behavior (PDF)" %}}. We can give you access to our source code to these tools; you can apply them to existing software to see what bugs you can find, and also think about ways to extend the tools to make them more accurate, to make them find other kinds of bugs, etc.
- Extend program analysis tools used by Linux kernel developers, such as {{% resource_link "6b5baed9-c206-4703-83b7-d19492b68d3b" "sparse" %}} and {{% resource_link "15b6a852-c71c-41c3-93ab-f6c9099ba761" "smatch" %}}, to catch different kinds of bugs in the kernel.
- Use the {{% resource_link "6e539550-f2e6-44a5-a86d-7b2ab5f84ac6" "KLEE" %}} symbolic execution system to build an analysis tool that finds interesting bugs in C programs.
- Explore the extent to which covert channels / side channels matter, e.g. in shared VMs like EC2, vs. shared OS, vs. other environments. See {{% resource_link "bdb42632-2519-416c-a366-b080fd683fe1" "this paper (PDF)" %}} for some background information.
- Add Capsicum support to Linux. There has been some {{% resource_link "9fde1d39-90df-4220-a39f-477906b24718" "recent work" %}} toward capsicum on linux {{% resource_link "310f8c06-0067-4227-8521-c1d0063fcdf2" "proposed" %}}.
- Port an interesting application to use Capsicum (on FreeBSD).
- Build an interesting application on top of Webathena ({{% resource_link "c551e879-1c96-4475-9f37-e06dabef7eaa" "site" %}}, {{% resource_link "c3d33a7a-100b-4fdc-9851-5060738be0b6" "code" %}}), or extend it to support non-DES enctypes (AES, etc).
- Implement Kerberos for Android. We can put you in touch with some folks at the Kerberos Consortium that are working on this. It would be interesting to implement a Kerberos ticket caching service, accessed via Android intents, so that an application can use Kerberos tickets for a specific service without being able to steal the user's entire TGS ticket.
- Implement progressive authentication: instead of requiring the user to log in to do anything, require different levels of credentials for specific tasks. For example, on Athena, perhaps running a web browser should not require any credentials, but accessing your personal files (or your browser accessing your google.com cookie that gives access to gmail) should require your Kerberos password, etc. The same would apply on an Android phone: checking the weather or the map should not require any credentials, but accessing the mail app should prompt for a PIN, swipe pattern, or password. {{% resource_link "29e086c8-8281-4f2d-9d62-022f5391e72a" "A paper from Microsoft Research (PDF)" %}} might give you some things to think about, although it may not be worthwhile to implement all of the environment monitoring done in that work.
- Examine the security of Android applications. Look at some previous studies for inspiration ({{% resource_link "dac3fbc5-3eb7-4767-bc13-f3f825b772bc" "one (PDF)" %}}, {{% resource_link "5d29614f-fa67-4c93-9b05-e420e6bb76f4" "two (PDF)" %}}).
- Improve sandboxing for Android applications. Is there something that you could do to prevent a malicious application from exploiting kernel bugs? Consider {{% resource_link "4d08150f-ed0d-4ccc-abf9-b020b7e59cdd" "recent improvements to seccomp" %}}, using {{% resource_link "dcea3a01-489d-4eef-aa13-51a7570ef086" "Linux KVM" %}}, or using Native Client.
- Look for weaknesses in random number generation, or improve the random number generation. Some hints for where to start: {{% resource_link "6e7ecd07-3828-4b3c-88e5-572aa52a435d" "Mining your Ps and Qs (PDF)" %}}, {{% resource_link "bd0467a1-a3f8-4b25-bfdb-e0b3706decde" "Boot-time Entropy (PDF)" %}}, {{% resource_link "6051cdaa-f0e2-4a6c-9c8c-11b526a8b968" "Ted T'so on Linux PRNG design" %}}, {{% resource_link "bb2106ff-93c1-4dfe-a383-7bced9cc5a6c" "Theoretical weaknesses in the Linux PRNG (PDF)" %}}.
- Audit interactions between Android applications, perhaps by tracing all intents sent via the reference monitor. When something goes wrong, can your system tell the user why an application might be broken?
- Implement an {{% resource_link "64b66bb6-e341-4b98-b883-db384466e192" "environmental key generation system" %}}.
- Build a password manager for Android applications, perhaps by implementing a virtual keyboard that can automatically enter passwords into an application. The virtual keyboard can know exactly what application it's entering passwords into, which can guard against phishing-style attacks.
- Provide more fine-grained network access control in Android, to protect an internal corporate network from possibly-malicious applications on a phone.
- Implement an efficient version of Baggy bounds checking on top of {{% resource_link "7c8385a8-d0f7-4f58-a813-a6a2beb6f736" "Clang" %}} and {{% resource_link "30d36cfb-adc7-4775-a47e-c970f399e7ca" "LLVM" %}}.
- Use DynamoRIO's binary instrumentation to implement some cool security mechanism for unmodified binaries. For example, you could implement a binary-level taint tracking system that prevents secret files from being sent out over the network. You can look at {{% resource_link "48981a49-6bf8-495b-84a7-3bc952f4ed03" "a previous lab" %}} we used to have involving DynamoRIO from a few years ago.
- Use {{% resource_link "d59969f2-bf11-4015-9974-4446789c2246" "Resin's taint tracking for Python" %}} to enforce some interesting properties in zoobar.
- Find an interesting use for trusted hardware, and figure out how to expose trusted hardware safely to applications. Linux should already have a basic device driver for a TPM.
- Write a tool to help privilege-separating Python applications, and apply it to the Zoobar labs or other real applications.
- Implement more flexible protection mechanisms for Linux (so that any user can create additional protection domains -- sub-users -- to run code with less privileges, without having to be root). You can build upon a class project from a previous year, {{% resource_link "07715339-3183-4b09-ad88-8cd4c01f5d38" "UserFS (PDF)" %}}.
- Improve the security of HTTPS in web browsers in the face of possibly compromised CAs. For example, define a new URL syntax that includes the server's certificate public key in the URL itself, so that one site can unambiguously include a link to another site without relying on CAs. Or, include the CA name in the URL, so that another CA cannot subvert security. See {{% resource_link "3fc2be6e-29c5-46d9-ac9c-0669f541e79d" "SSL observatory" %}}, {{% resource_link "7e6e7ea9-b310-4cb3-a023-511d1ac5b177" "perspectives" %}}, and CertPatrol.
- Auditing support for web applications. For instance, suppose someone broke into your blog or forum, added a user account for themselves, changed permissions, and posted garbage messages. How can you track down all of the changes made by the attacker? Could be done with the help of a language runtime, such as Resin.
- The Tor Project has some {{% resource_link "ccb08f38-e667-4f59-a1aa-115beeaece5c" "ideas for possible Tor-related projects" %}}.
- Analyze the Bitcoin transaction graph. How hard is it to anonymize Bitcoin exchanges? Here's one recent {{% resource_link "365e0f15-8e2f-4d70-8066-7fb960a43b37" "paper (PDF)" %}} analyzing the Bitcoin data set, which might give you ideas for other things to try.
- Implement one of {{% resource_link "76f9b182-aff6-408d-99da-151a50071208" "Daniel J. Bernstein's ECC curves (e.g., Curve3617) in OpenSSL / OpenSSH" %}}.