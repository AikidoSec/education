
# HowTo 105: Install GPG and encrypt/decrypt files
Deploy a vulnerable PHP app on Azure and protect it with Zen Firewall

## Overview

GnuPG is a complete and free implementation of the OpenPGP standard as defined by [RFC4880](https://www.ietf.org/rfc/rfc4880.txt) (also known as PGP). GnuPG allows you to encrypt and sign your data and communications; it features a versatile key management system, along with access modules for all kinds of public key directories. GnuPG, also known as GPG, is a command line tool with features for easy integration with other applications. A wealth of frontend applications and libraries are available. GnuPG also provides support for S/MIME and Secure Shell (ssh).

At the time of writing this page, the current version of GnuPG is 2.4.8. See the [download](https://gnupg.org/download/index.html) page for other maintained versions. GPG was created in 1997 by Werner Koch, who began development after attending a lecture by Richard Stallman. The first official production version, GPG 1.0.0, was released in 1999. 

This howto was created in order to offer a simple and secure method for sharing sensitive information "in the open." This means being able to send a GPG-encrypted file as an email attachment to someone and not worry about the email or file being intercepted or accessed by someone other than the recipient(s) for which you encrypted the file. You can also commit a GPG-encrypted text file with passwords and authentication tokens to a git repository in order to safely and securely maintain the credentials alongside the code itself for example.

---

## Learning Objectives

By the end of this howto, you will:

- Download GPG software for your computer
- Generate a private/public keypair
- Export an ASCII-armoured public key block
- Import someone's public key block
- Encrypt a file using someone's public key
- Decrypt a file using your private key

---

## Tools & Requirements

- [GPG](https://gnupg.org/)
- [Homebrew](https://brew.sh/) Mac package manager
- [Gpg4win](https://gpg4win.org/) Windows GPG release
- Text editor (e.g., VS Code, Sublime, nano, vi/vim, Emacs etc.)

---

## Setup

1. **Install GPG**

Install GnuPG (GPG) on your computer to enable encryption, signing, and verification of files and messages. This step ensures you have the necessary tools to securely manage keys and protect sensitive data like passwords and application tokens used for authentication (but without the need for a password manager).

---

## Instructions to use GPG basic features

### Step 1: Generate your private/public keys

---

### Step 2: Export your public key block

---

### Step 3: Import another person's public key

---

### Step 4: Encrypt a file

---

### Step 5: Decrypt a file

---

### Step 6: List the public keys in your kekyring

---

## Additional Resources

- one
- two
- three

---

## License

© 2025 [Mike Wilkes](https://www.linkedin.com/in/eclectiqus/). This work is licensed under the [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/) license.

Attribution should be given to [Aikido Security](https://aikido.dev).

[![Creative Commons License](https://licensebuttons.net/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0/)

