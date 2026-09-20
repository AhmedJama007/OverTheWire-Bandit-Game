# Level 19 to Level 20

## Goal
Use a specialized executable file that has the 'setuid' bit set to read a file you normally wouldn't have permissions to access.

## Concept Explanation
The SetUID (SUID) permission bit allows an executable to run with the privileges of its owner rather than the user executing it. This is a crucial concept in Linux privilege escalation and security.

## Commands Used
- `ls -l`, executing SUID binaries

## What I Learned
I learned about advanced Linux permissions. Understanding SUID is critical for both system administration and securing servers against privilege escalation vulnerabilities.
