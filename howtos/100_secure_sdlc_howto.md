
# HowTo 100: Introduction to Secure Software Development Life Cycle (SDLC)

## Overview

This howto introduces the concept of a Secure **Software Development Life Cycle (SDLC)**. The SDLC is the process that guides how software is planned, built, tested, released, and eventually retired. A secure SDLC means weaving security considerations into every stage of that process, not tacking them on at the end.

When we talk about building software, most people picture developers writing code, designers shaping user experiences, and project managers keeping everything on track. What often gets overlooked, however, is security. Too many organizations treat security as something to check only at the very end of a project, like locking the doors after the house is already built. Unfortunately, by that point, vulnerabilities are harder, more expensive, and sometimes nearly impossible to fix.

This idea is often called “shifting left.” Imagine a timeline of the SDLC, moving from left to right: planning on the left, building and testing in the middle, and deployment on the right. Traditionally, most security checks happen on the right side just before or after release. Shifting left means moving those security practices earlier in the process, toward planning and design. It also entails having security controls and automation applied in "lower" environments such as dev and test so that issues are identified and remediated before reaching production. By doing so, problems are caught before they become costly risks. For example, identifying a weak authentication design during the planning phase is far easier than trying to patch or update a live system that has already been attacked and compromised.

---

## Learning Objectives

By the end of this howto, you will:

- Become familiar with some of the terms and acronyms used in infosec.
- Understand what the SDLC is and why a secure SDLC is needed.
- Create a GitHub account in order to become familiar with basic software development tools.
- Learn about the OWASP Top 10 most critical web application security risks.
- Interpret scan results of a demo software repository.

---

## Tools & Requirements

- [GitHub](https://github.com/)
- [Google Authenticator](https://en.wikipedia.org/wiki/Google_Authenticator)

---

## Setup

1. **The Language of Cybersecurity**

Before diving into the Secure SDLC, it’s important to become familiar with some of the common terms and acronyms used in the field of information security (infosec). Here are a few to get started:

- **CIA Triad**: Confidentiality, Integrity, Availability are the three pillars of security.
- **Vulnerability**: A weakness in a system that could be exploited.
- **Exploit**: The method an attacker uses to take advantage of a vulnerability.
- **CVE**: Common Vulnerabilities and Exposures is a catalogo of publicly known information security vulnerabilities (e.g., [CVE-2021-44228](https://nvd.nist.gov/vuln/detail/cve-2021-44228))
- **CVSS**: Common Vulnerability Scoring System used to quantify the severity of a hardware or software vulnerability
- **MFA**: Multi-Factor Authentication is used to protect login credentials with an additional authentication factor (something that you are such as face recognition or fingerprint scan, something you know such as a password or something that you have such as an RSA key fob or authenticator application such as Google Authenticator
- **Threat Actor**: An individual or group that may attempt an attack (e.g., hackers, criminal groups, nation states).
- **APT**: Advanced Persistent Threat is an acronym for attackers, often backed by nation-states or well-resourced criminal organizations.
- **OWASP**: The Open Worldwide Application Security Project is a community that creates free resources on application security best known for publishing top 10 lists of common application security risks or mistakes.

2. **Understand the Secure SDLC**

The SDLC is often represented in stages. Here’s how security fits into each one:

- **Planning** - Define requirements, including security policies.
- **Design** - Identify potential threats (using methods like threat modeling).
- **Implementation (Coding)** - Use secure coding practices to avoid introducing vulnerabilities.
- **Testing** - Perform security testing such as static analysis and vulnerability scanning.
- **Deployment** - Configure environments securely, monitor for incidents.
- **Maintenance** - Apply patches and updates that address bugs and security issues.
- **Decommissioning** - Retire systems and any third-party integrations responsibly.

A clever way of describing the thinking behind having security applied to all phases of the SDLC is that we should not be in the business of building security features, but rather we should be in the business of designing features securely.

3. **Create a GitHub Account**

GitHub is a platform developers use to collaborate on software projects. Even without coding experience, you’ll use it to explore repositories and understand how development tools fit into the SDLC.

- Browse to [https://github.com](https://github.com)
- Click on "Sign Up" to create your account
- Enter your email address, provide a strong password, desired username and select your country/region or, if you have a Google account, click on "Continue with Google"
- Click on "Create account" if you entered your email address and other details
- Check your email for the code sent to your account that verifies you own the address that you supplied.
- Paste the code into the confirmation page and click "Continue"
- Login to your new account
- Create your first repository by clicking on the green button and give the repo a name (myfirstrepo or similar)
- Enter a description "this repository is my first but not my last"
- Change the visibility from "Public" to "Private" as there is no need to share this repo with the world
- Toggle the "Add README" from "Off" to "On" as it's a good habit to always create documentation alongside code
- Click the "Create repository" green button

Congratulations! You should see your repo has been created. You're well on your way now to learning the basics of software development and the use of Git!

---

## Instructions

### Step 1: What is the SDLC?

Read the following:
> SDLC stands for Software Development Life Cycle.

**Question:** How is SDLC different from a Secure SDLC?

---

### Step 2: Turn on MFA

- Install Google Authenticator on your mobile phone (if you have not installed it already)
- Browse to your GitHub profile: [https://github.com/settings/profile](https://github.com/settings/profile)
- Select "Password and authentication" from the left navigation menu
- Click on "Enable two-factor authentication"
- Scan the QR code to add GitHub as an app to your Google Authenticator
- Enter the six digit code from the authenticator app and click "Continue" to enable MFA

---

### Step 3: Sign in to Aikido Portal

Many of the labs in this repository make use of the Aikido Security platform which you can access to learn about the Secure SDLC by looking at code and scanning it for vulnerabilities and security issues.

- Browse to [https://app.aikido.dev](https://app.aikido.dev)
- Log in and sign up by clicking on the purple button "GitHub"
- Click on the green button "Authorize Aikido Security" to grant Aikido access to your GitHub profile
- If your course instructor has created a workspace and team for you to use, click on "Join My Team" otherwise click on "Use Demo Workspace"
- Enter your email address to receive notifications and digests for your repo vulnerabilities
- Check the box "I agree to Master Subscription Agreement & Data Processing Agreement."
- Click the purple button "Finished!" to complete the activation of your Aikido account
- Click on any of the findings that are presented on the portal homepage to learn more about them

---

### Step 4: Explore the OWASP Top 10

The [OWASP Top 10](https://owasp.org/www-project-top-ten/) is a list of the most common and critical security risks for web applications. Understanding these risks will help you see the kinds of problems a Secure SDLC tries to prevent.

Here are a few examples from the list:

- **Broken Access Control** – Users can access data or functions they shouldn’t.
- **Cryptographic Failures** – Poor handling of sensitive data like passwords.
- **Injection** – Untrusted data tricking a system into executing unintended commands.

Activity: Read through the top 10 list. Pick one risk and write a short summary in your own words.

### Step 5: Interpret Scan Results of the Demo Respository

Now let's apply these concepts by looking at automated security scan results. Developers use tools like SAST (Static Application Security Testing) to analyze code for vulnerabilities. Aikido's platform helps developers and security teams identify, prioritize, and remediate vulnerabilities across code, cloud infrastructure, and runtime environments.

- Browse to the Aikido Demo repository: [https://app.aikido.dev/repositories](https://app.aikido.dev/repositories)
- Review the scan results and issues by clicking on one of the numbers below the "Issues" column.
- Look at the findings. You may see terms like "SQL Injection" or "TLS not enforced with valid HSTS header."
- Compare the findings to the OWASP Top 10 list.

## Conclusion: Security as a Shared Responsibility

The Secure SDLC is not about turning everyone into a security engineer. It’s about building a culture where security is part of every decision, from planning to retirement. By learning the language of infosec, exploring GitHub, understanding the OWASP Top 10, and interpreting scan results, you are already practicing the mindset of "shifting left."

---

## Submission Checklist

- [ ] Screenshot of your GitHub profile.
- [ ] Screenshot of your Aikido home page.
- [ ] Identify an OWASP Top 10 vulnerability.
- [ ] Reflection paragraph.

---

## Optional Extension

- Try 
- Configure
- Explore

---

## Grading Rubric (Sample)

| Task                              | Points |
|-----------------------------------|--------|
| GitHub account creation           | 10     |
| Aikido account activation         | 10     |
| Browse demo repository            | 10     |
| Submitted reflection              | 10     |
| **Total**                         | **40** |

---

## Additional Resources

- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [OWASP Mobile Top 10](https://owasp.org/www-project-mobile-top-10/)
- [DevSecOps](https://www.redhat.com/en/topics/devops/what-is-devsecops)
- [Secure SDLC](https://www.hackerone.com/knowledge-center/what-ssdlc-secure-software-development-life-cycle)
- [Aikido Security for Students](https://www.aikido.dev/aikido-for-students)
- [Aikido Security for Educators](https://www.aikido.dev/aikido-for-higher-education)
- [Intigriti Security Research](https://www.intigriti.com/blog/business-insights/power-of-the-collective-investing-in-the-security-researcher-community-for-shared)

---

## License

© 2025 [Mike Wilkes](https://www.linkedin.com/in/eclectiqus/). This work is licensed under the [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/) license.

Attribution should be given to [Aikido Security](https://aikido.dev).

[![Creative Commons License](https://licensebuttons.net/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0/)

