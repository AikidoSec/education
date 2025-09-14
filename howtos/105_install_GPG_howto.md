
# HowTo 105: Install GPG and encrypt/decrypt files

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

**GPG Installation on Mac**

- Ensure that you have [Homebrew](https://brew.sh/) installed on your Mac
- To install GnuPG, type the following command in the Terminal App:
```
brew install gnupg2
```

**GPG Installation on Windows**

Browse to the [binary releases of Gpg4win](https://gpg4win.org/download.html) and download the program to your Windows machine. As of this writing, Gpg4win latest version is 4.4.1.

---

## Instructions to use GPG basic features

### Step 1: Generate your private/public keys

**GPG Cheat Sheet Command Reference**

- To generate public and private keys, type the following command on the Terminal App:

```
gpg --full-generate-key
```

- To list the keys generated, type the following command on the Terminal App:

```
gpg -K
```

---

### Step 2: Export your public key block

- To export your public key in a form that can be share and used, type the following command on the Terminal App:

```
gpg --export --armor --output YourNameNoSpaces.pub
```

---

### Step 3: Import another person's public key

- To import public keys for others simply copy the public key blob text block and place it into a file and then type the following command on the Terminal App to import the public key for that user:

```
gpg --import --armor OtherUserPublicKeyBlock.pub
```

---

### Step 4: Encrypt a file

- To encrypt and sign a file using GPG, type the following command on the Terminal App:

```
gpg -se -u <user> <filename>
```

- To encrypt and sign a file using GPG for more than one user, type the following command on the Terminal App:

```
gpg -se -u <user1> -u <user2> <filename>
```

---

### Step 5: Decrypt a file

- To decrypt a file, type the following command on the Terminal App:

```
gpg -d <filename> > <outputfile>
```

---

### Step 6: List the public keys in your kekyring

- To list the public keys in your keyring, type the following command on the Terminal App:

```
gpg --list-keys
```

---

## Additional Resources

- [GPG Cheat Sheet](https://irtfweb.ifa.hawaii.edu/~lockhart/gpg/)
- [Another GPG Cheat Sheet](https://www.sysadmin.md/gpg-cheatsheet.html)
- [GPG Wikipedia Page](https://en.wikipedia.org/wiki/GNU_Privacy_Guard)

---

## License

© 2025 [Mike Wilkes](https://www.linkedin.com/in/eclectiqus/). This work is licensed under the [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/) license.

Attribution should be given to [Aikido Security](https://aikido.dev).

[![Creative Commons License](https://licensebuttons.net/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0/)

