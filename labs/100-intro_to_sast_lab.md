
# 🧪 Lab 100: Introduction to Static Application Security Testing (SAST)

## Overview

This lab introduces the concept of **Static Application Security Testing (SAST)** using a real GitHub repository and an open-source scanning tool called **Opengrep**. You’ll learn how to detect common security issues in source code and explore how secure coding and automated scanning can improve software security.

---

## Learning Objectives

By the end of this lab, you will:

- Understand what SAST is and how it differs from other security testing methods.
- Install and run a basic SAST tool to scan code.
- Interpret scan results to identify insecure coding patterns.
- Remediate at least one issue in a vulnerable application.
- Reflect on the importance of secure coding and continuous scanning.

---

## Tools & Requirements

- [Git](https://git-scm.com/) and [GitHub](https://github.com/)
- [cosign](https://github.com/sigstore/cosign) (for validating software packages and libraries)
- Terminal/Command Prompt
- [cURL](https://en.wikipedia.org/wiki/CURL)
- [Opengrep](https://www.opengrep.dev/) (SAST tool)
- Code editor (e.g., VS Code, Sublime, nano, vi/vim, Emacs etc.)

---

## Setup

1. **Clone a Sample Vulnerable Repository**
   ```bash
   git clone git@github.com:vulnerable-apps/vuln_node_express.git
   cd vuln_node_express
   ```
   From this directory you will scan the cloned copy of a vulnerable node express application that is one of over [100 forks](https://github.com/vulnerable-apps) of deliberately vulnerable web applications and APIs.

2. **Install Opengrep**
   ```bash
   curl -fsSL https://raw.githubusercontent.com/opengrep/opengrep/main/install.sh | bash
   ```
   Opengrep is a fork of Semgrep and was initiated by a collective of organizations including: [Aikido Security](https://www.aikido.dev/), [Arnica](https://www.arnica.io/), [Amplify](https://amplify.security/), [Endor Labs](https://www.endorlabs.com/), [Jit](https://www.jit.io/), [Kodem](https://www.kodemsecurity.com/), [Legit](https://www.legitsecurity.com/), [Mobb](https://www.mobb.ai/), [Orca Security](https://orca.security/) and [Phoenix Security](https://phoenix.security/) (and others).

   _Binaries available in the [release page](https://github.com/opengrep/opengrep/releases)._

---

## Lab Instructions

### Step 1: What is SAST?

Read the following:
> SAST stands for Static Application Security Testing. It involves analyzing source code or compiled code to find security vulnerabilities without executing the program. SAST helps developers catch issues early in the SDLC and is a key component of DevSecOps.

**Question:** How is SAST different from DAST (Dynamic Application Security Testing)?

---

### Step 2: Run a Scan

Run Opengrep to scan the codebase:
```bash
opengrep scan --config=auto .
```

This will analyze the code and print a list of findings with file names, line numbers, and rule descriptions.

---

### Step 3: Analyze Results

Pick **two findings** from the scan and complete the following for each:

- **Finding**: (copy the message)
- **Explanation**: What does the rule mean?
- **Fix Suggestion**: How could the developer improve or secure the code?

---

### Step 4: Fix a Vulnerability

Choose one finding and make a code change to resolve it. Then re-run Opengrep:
```bash
opengrep scan --config=auto .
```

Confirm that your change removed the issue.

---

### Step 5: Reflect

Write a short reflection (~150 words) answering:

- What did you learn from this lab?
- How can tools like Opengrep be integrated into a CI/CD pipeline?
- Would you trust automated tools to catch security issues?

---

## Submission Checklist

- [ ] Screenshot of your Opengrep scan output.
- [ ] Two findings analyzed.
- [ ] Code fix committed and verified.
- [ ] Reflection paragraph.

---

## Optional Extension

- Try [Bandit](https://bandit.readthedocs.io/en/latest/) if you're using Python code.
- Configure GitHub Actions to run Opengrep on each commit.
- Explore writing your own Opengrep rule.

---

## Grading Rubric (Sample)

| Task                              | Points |
|-----------------------------------|--------|
| Ran scan successfully             | 10     |
| Analyzed 2 findings               | 10     |
| Fixed 1 vulnerability             | 10     |
| Submitted reflection              | 10     |
| **Total**                         | **40** |

---

## Additional Resources

- [Opengrep Docs](https://opengrep.dev/docs/)
- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [OWASP Mobile Top 10](https://owasp.org/www-project-mobile-top-10/)
- [DevSecOps](https://www.redhat.com/en/topics/devops/what-is-devsecops)
- [Aikido Security for Students](https://www.aikido.dev/aikido-for-students)

---

## License

© 2025 [Mike Wilkes](https://www.linkedin.com/in/eclectiqus/). This work is licensed under the [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/) license.

Attribution should be given to [Aikido Security](https://aikido.dev).

[![Creative Commons License](https://licensebuttons.net/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0/)

