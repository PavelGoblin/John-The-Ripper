# John the Ripper Attack – Educational Cybersecurity README

## Overview

This document provides a detailed educational overview of the password cracking and password auditing tool John the Ripper. The purpose of this README is to explain how password cracking attacks work, the attack lifecycle, common techniques, defenses, and cybersecurity concepts related to password security.

> Important: This document is strictly for cybersecurity education, ethical hacking, security awareness, and defensive learning purposes.

---

# Tool Information

## Tool Name

John the Ripper

## Tool Type

Password auditing and password recovery tool

## Common Uses

* Password security testing
* Ethical hacking
* Penetration testing
* Digital forensics
* Security auditing
* Password recovery

---

# Introduction to Password Cracking

Modern systems usually do not store passwords directly.
Instead, systems store password hashes.

Example:

```text
Password → Hash Algorithm → Stored Hash
```

Example hash:

```text
Password: hello123
MD5 Hash: 482c811da5d5b4bc6d497ffa98491e38
```

During login:

1. User enters password
2. System hashes password
3. Hash compared with stored hash
4. If matched → Login successful

---

# Main Goal of the Attack

The objective of a password cracking attack is:

```text
Recover the original password from the hash
```

Since hashes are one-way functions, attackers repeatedly guess passwords and compare generated hashes.



John the Ripper
This is the community-enhanced, "jumbo" version of John the Ripper. It has a lot of code, documentation, and data contributed by jumbo developers and the user community. It is easy for new code to be added to jumbo, and the quality requirements are low, although lately we've started subjecting all contributions to quite some automated testing. This means that you get a lot of functionality that is not necessarily "mature", which in turn means that bugs in this code are to be expected.

John the Ripper homepage is:

https://www.openwall.com/john/

If you have any comments on this release or on JtR in general, please join the john-users mailing list and post in there:

https://www.openwall.com/lists/john-users/

For contributions to John the Ripper jumbo, please use pull requests on GitHub:

https://github.com/openwall/john/blob/bleeding-jumbo/CONTRIBUTING.md

Included below is basic John the Ripper core documentation.

John the Ripper password cracker.
John the Ripper is a fast password cracker, currently available for many flavors of Unix, macOS, Windows, DOS, BeOS, and OpenVMS (the latter requires a contributed patch). Its primary purpose is to detect weak Unix passwords. Besides several crypt(3) password hash types most commonly found on various Unix flavors, supported out of the box are Kerberos/AFS and Windows LM hashes, as well as DES-based tripcodes, plus hundreds of additional hashes and ciphers in "-jumbo" versions.

How to install.
See INSTALL for information on installing John on your system.

How to use.
To run John, you need to supply it with some password files and optionally specify a cracking mode, like this, using the default order of modes and assuming that "passwd" is a copy of your password file:

john passwd
or, to restrict it to the wordlist mode only, but permitting the use of word mangling rules:

john --wordlist=password.lst --rules passwd
Cracked passwords will be printed to the terminal and saved in the file called $JOHN/john.pot (in the documentation and in the configuration file for John, "$JOHN" refers to John's "home directory"; which directory it really is depends on how you installed John). The $JOHN/john.pot file is also used to not load password hashes that you already cracked when you run John the next time.

To retrieve the cracked passwords, run:

john --show passwd
While cracking, you can press any key for status, or 'q' or Ctrl-C to abort the session saving its state to a file ($JOHN/john.rec by default). If you press Ctrl-C for a second time before John had a chance to complete handling of your first Ctrl-C, John will abort immediately without saving. By default, the state is also saved every 10 minutes to permit for recovery in case of a crash.

To continue an interrupted session, run:

john --restore
These are just the most essential things you can do with John. For a complete list of command line options and for more complicated usage examples you should refer to OPTIONS and EXAMPLES, respectively.

Please note that "binary" (pre-compiled) distributions of John may include alternate executables instead of just "john". You may need to choose the executable that fits your system best, e.g. "john-omp" to take advantage of multiple CPUs and/or CPU cores.

Features.
John the Ripper is designed to be both feature-rich and fast. It combines several cracking modes in one program and is fully configurable for your particular needs (you can even define a custom cracking mode using the built-in compiler supporting a subset of C). Also, John is available for several different platforms which enables you to use the same cracker everywhere (you can even continue a cracking session which you started on another platform).

Out of the box, John supports (and autodetects) the following Unix crypt(3) hash types: traditional DES-based, "bigcrypt", BSDI extended DES-based, FreeBSD MD5-based (also used on Linux and in Cisco IOS), and OpenBSD Blowfish-based (now also used on some Linux distributions and supported by recent versions of Solaris). Also supported out of the box are Kerberos/AFS and Windows LM (DES-based) hashes, as well as DES-based tripcodes.

When running on Linux distributions with glibc 2.7+, John 1.7.6+ additionally supports (and autodetects) SHA-crypt hashes (which are actually used by recent versions of Fedora and Ubuntu), with optional OpenMP parallelization (requires GCC 4.2+, needs to be explicitly enabled at compile-time by uncommenting the proper OMPFLAGS line near the beginning of the Makefile).

Similarly, when running on recent versions of Solaris, John 1.7.6+ supports and autodetects SHA-crypt and SunMD5 hashes, also with optional OpenMP parallelization (requires GCC 4.2+ or recent Sun Studio, needs to be explicitly enabled at compile-time by uncommenting the proper OMPFLAGS line near the beginning of the Makefile and at runtime by setting the OMP_NUM_THREADS environment variable to the desired number of threads).

"-jumbo" versions add support for hundreds of additional hash and cipher types, including fast built-in implementations of SHA-crypt and SunMD5, Windows NTLM (MD4-based) password hashes, various macOS and Mac OS X user password hashes, fast hashes such as raw MD5, SHA-1, SHA-256, and SHA-512 (which many "web applications" historically misuse for passwords), various other "web application" password hashes, various SQL and LDAP server password hashes, and lots of other hash types, as well as many non-hashes such as SSH private keys, S/Key skeykeys files, Kerberos TGTs, encrypted filesystems such as macOS .dmg files and "sparse bundles", encrypted archives such as ZIP (classic PKZIP and WinZip/AES), RAR, and 7z, encrypted document files such as PDF and Microsoft Office's - and these are just some examples. To load some of these larger files for cracking, a corresponding bundled *2john program should be used first, and then its output fed into JtR -jumbo.

Graphical User Interface (GUI).
There is an official GUI for John the Ripper: Johnny.

Despite the fact that Johnny is oriented onto JtR core, all basic functionality is supposed to work in all versions, including jumbo.

Johnny is a separate program, therefore you need to have John the Ripper installed in order to use it.

More information about Johnny and its releases is on the wiki:

https://openwall.info/wiki/john/johnny
---

# Attack Lifecycle

# Phase 1 – Reconnaissance

Attackers collect target information.

Possible sources:

* Social media
* Public information
* Data leaks
* Old credentials
* Human behavior patterns
* Company naming conventions

Example guesses:

```text
rahim123
football2025
messi10
admin@123
```

Humans often create predictable passwords.

---

# Phase 2 – Obtaining Password Hashes

Attackers usually require password hashes before cracking begins.

Common sources:

| Source               | Description              |
| -------------------- | ------------------------ |
| Database leaks       | Compromised websites     |
| Linux shadow file    | /etc/shadow              |
| Windows SAM database | Windows password storage |
| Backup files         | Unsecured backups        |
| Memory dumps         | Extracted credentials    |

---

# Linux Password Storage

Linux systems commonly store hashes in:

```text
/etc/shadow
```

Example:

```text
user:$6$randomsalt$hashedpassword
```

Meaning:

* $6$ → SHA-512
* Salt included
* Hashed password stored securely

---

# Windows Password Storage

Windows commonly stores:

* NTLM hashes
* SAM database credentials

Attackers may attempt to access these after gaining system privileges.

---

# Phase 3 – Hash Identification

Attackers identify the hash type before attempting recovery.

| Hash Type | Characteristics             |
| --------- | --------------------------- |
| MD5       | 32 hexadecimal characters   |
| SHA1      | 40 hexadecimal characters   |
| SHA256    | 64 hexadecimal characters   |
| bcrypt    | Starts with $2a$            |
| NTLM      | Windows authentication hash |

Correct identification is essential for successful attacks.

---

# Phase 4 – Attack Preparation

Attackers prepare:

* Wordlists
* Hardware resources
* Rules
* GPU acceleration
* Attack strategies

---

# Common Attack Methods

# 1. Dictionary Attack

A dictionary attack uses a predefined list of common passwords.

Example passwords:

```text
123456
password
admin123
bangladesh
```

Why it works:

* Many users choose weak passwords
* Human passwords are predictable

Advantages:

* Fast
* Efficient

Limitations:

* Fails against strong passwords

---

# 2. Rule-Based Attack

Rules automatically modify passwords.

Examples:

```text
password → Password123
admin → Admin@2025
football → Football#
```

This simulates human password habits.

---

# 3. Hybrid Attack

Combines dictionary attacks with brute-force patterns.

Examples:

```text
password2025
rahim@123
admin786
```

Very effective against normal user passwords.

---

# 4. Brute Force Attack

Brute force tries every possible combination.

Example sequence:

```text
a
aa
ab
abc
abcd
```

Possible combinations grow exponentially.

Factors affecting difficulty:

* Password length
* Character complexity
* Symbols
* Numbers
* Uppercase/lowercase letters

---

# GPU Acceleration

Modern password cracking often uses GPUs.

Why GPUs are effective:

* Thousands of parallel calculations
* Much faster than CPUs

Comparison:

| Hardware | Performance |
| -------- | ----------- |
| CPU      | Slower      |
| GPU      | Much faster |

---

# Incremental Mode

Incremental mode attempts:

* Smart pattern learning
* Optimized guessing order
* Prioritization of common combinations

This increases attack efficiency.

---

# Mask Attack

Mask attacks target partially known password structures.

Example structure:

```text
Name + 4 digits
```

Possible guesses:

```text
rahim2025
rahim1234
```

Useful when partial password information is known.

---

# Rainbow Table Attack

Rainbow tables contain precomputed hashes.

Purpose:

* Faster hash lookup
* Avoid recalculating hashes repeatedly

Modern defenses:

* Salting
* Strong hashing algorithms

---

# Salting

A salt is random data added before hashing.

Example:

```text
password + random_salt
```

Benefits:

* Prevents rainbow table reuse
* Makes identical passwords unique
* Increases cracking complexity

---

# Weak vs Strong Hashing Algorithms

## Weak Algorithms

* MD5
* SHA1
* LM Hash

## Strong Algorithms

* bcrypt
* Argon2
* PBKDF2

Strong algorithms intentionally slow password cracking.

---

# Credential Stuffing

Recovered passwords may be tested on:

* Email accounts
* Social media
* Banking systems
* University portals
* Cloud services

Reason:
Many users reuse passwords across multiple platforms.

---

# Real-World Attack Scenario

```text
1. Website database breached
2. Password hashes leaked
3. Hash type identified
4. Wordlists loaded
5. Rules applied
6. Weak passwords recovered
7. Accounts compromised
```

---

# Password Entropy

Entropy measures password unpredictability.

Higher entropy means:

* More randomness
* Greater complexity
* Increased cracking difficulty

Strong passwords significantly increase attack time.

---

# Strong Password Examples

Weak:

```text
rahim123
football10
password2025
```

Strong:

```text
T7@vL9#pQ2!x
```

---

# Multi-Factor Authentication (MFA)

MFA adds additional verification.

Examples:

* SMS codes
* Authenticator applications
* Hardware tokens

Even if passwords are cracked, MFA can block unauthorized access.

---

# Modern Defense Techniques

| Defense          | Purpose                    |
| ---------------- | -------------------------- |
| Strong passwords | Reduce guessing success    |
| MFA              | Additional security layer  |
| bcrypt/Argon2    | Slow password cracking     |
| Account lockout  | Stop repeated attempts     |
| Rate limiting    | Slow attackers             |
| Monitoring       | Detect suspicious activity |

---

# Ethical Hacking Applications

Cybersecurity professionals use John the Ripper for:

* Password auditing
* Security testing
* Employee awareness training
* Penetration testing
* Compliance verification

---

# Legal and Ethical Considerations

Authorized usage:

* Legal
* Educational
* Defensive

Unauthorized usage:

* Illegal
* Unethical
* Criminal in many countries

Always obtain permission before performing security testing.

---

# Advantages of John the Ripper

| Advantage           | Description                |
| ------------------- | -------------------------- |
| Fast                | Efficient password testing |
| Flexible            | Multiple attack modes      |
| Multi-platform      | Linux, Windows, macOS      |
| Community support   | Large user community       |
| Broad compatibility | Supports many hash types   |

---

# Limitations

| Limitation                 | Description                |
| -------------------------- | -------------------------- |
| Strong passwords difficult | May take years             |
| Modern hashing algorithms  | Slow attacks significantly |
| GPU requirements           | Hardware intensive         |
| Time-consuming             | Large password space       |

---

# Important Cybersecurity Lessons

This topic teaches:

* Weak passwords are dangerous
* Password reuse increases risk
* MFA is important
* Modern hashing algorithms matter
* Human behavior affects security

---

# Final Summary

| Topic                   | Details                         |
| ----------------------- | ------------------------------- |
| Tool Name               | John the Ripper                 |
| Tool Type               | Password auditing/cracking      |
| Main Target             | Password hashes                 |
| Common Attack Types     | Dictionary, brute force, hybrid |
| Main Weakness Exploited | Weak passwords                  |
| Main Defense            | Strong passwords + MFA          |
| Ethical Use             | Security auditing               |
| Illegal Use             | Unauthorized access             |

---

# Disclaimer

This document is intended only for:

* Cybersecurity education
* Ethical hacking learning
* Defensive security awareness
* Academic research

Do not use cybersecurity knowledge or tools against systems, networks, or accounts without explicit authorization.
