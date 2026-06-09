+++
title = "Blue Team VM Hardening Lab"
date = 2026-06-09
description = "A comprehensive guide detailing system hardening procedures for Linux servers."
tags = ["Blue Team", "Linux Security", "SIEM"]
+++

## Lab Overview
This project focuses on auditing and securing a vanilla Ubuntu Server installation against common attack vectors.

### Core Objectives
*   Configure system firewalls using **UFW** to block all unauthorized traffic.
*   Enforce strong password policies and disable root SSH login.
*   Implement central log collection utilizing an ELK stack pipeline.

### Steps Taken
1. **SSH Hardening**: Edited `/etc/ssh/sshd_config` to change the default port and restrict authentication strictly to SSH keys.
2. **Auditd Setup**: Deployed Linux Audit Framework rules to track unauthorized file changes in critical system directories.

```bash
# Example rule used to monitor password changes
-w /etc/passwd -p wa -k passwd_changes
```
