# KAN-50: Day-2-Infra Task 3 (Convert pem to ppk / ppk to pem)

- **Jira:** https://sasidharana504.atlassian.net/browse/KAN-50
- **Status:** Done
- **Assignee:** Mithun.U
- **Issue type:** Task
- **Priority:** Medium
- **Resolution:** Done
- **Reporter:** Mithun.U
- **Created:** 2026-10-12T10:41:33.840Z
- **Updated:** 2026-10-12T13:09:14.881Z
- **Due date:** —
- **Labels:** —
- **Components:** —

## Description

Description: Different cloud providers and SSH clients often require different key formats—OpenSSH standard (.pem) versus PuTTY's proprietary format (.ppk).

Today's mission ensures the team knows how to inspect, generate, and convert SSH key pairs between .pem and .ppk formats securely on Ubuntu without breaking permissions.

The Key Conversion & Management Toolkit

1. Installing the Conversion Utilities (putty-tools)

- Concept: Ubuntu doesn't convert .ppk natively by default out of the box, but the lightweight package putty-tools provides puttygen for command-line conversions.
- Practice:  - Install the tool: sudo apt update && sudo apt install putty-tools -y
2. Generating a Standard OpenSSH Key Pair (.pem)

- Concept: Create a secure RSA or Ed25519 key pair to serve as your source.
- Practice:  - Generate a private/public key pair: ssh-keygen -t rsa -b 4096 -f my_test_key - This creates two files: my_test_key (the private key / .pem equivalent) and my_test_key.pub (the public key).
3. Converting .pem (OpenSSH) to .ppk (PuTTY format)

- Concept: Transform a standard OpenSSH private key so it can be imported into PuTTY or FileZilla on Windows.
- Practice:  - Use puttygen to convert the format: puttygen my_test_key -o my_test_key.ppk - Optional: Add a passphrase during conversion for extra security if required.
4. Converting .ppk back to .pem (OpenSSH format)

- Concept: If a client or colleague hands you a PuTTY .ppk file and you need to use it in a Linux terminal or automation script via standard SSH, you must convert it back.
- Practice:  - Use puttygen to export the .ppk back to an OpenSSH private key: puttygen my_test_key.ppk -O private-openssh -o recovered_key.pem
5. Enforcing Strict Security Permissions on Private Keys (chmod 600)

- Concept: Linux SSH clients will outright reject private keys if their permissions are too open (e.g., readable by group or others).
- Practice:  - Secure your .pem key immediately after creation or conversion: chmod 600 recovered_key.pem - Verify the permissions read strictly as -rw-------.

## Attachments

- [screenshot-2026-10-12_17-52-56.png](attachments/screenshot-2026-10-12_17-52-56.png)
- [screenshot-2026-10-12_17-55-32.png](attachments/screenshot-2026-10-12_17-55-32.png)
- [screenshot-2026-10-12_17-56-34.png](attachments/screenshot-2026-10-12_17-56-34.png)
- [screenshot-2026-10-12_17-57-49.png](attachments/screenshot-2026-10-12_17-57-49.png)
