## Level 9 to Level 10

## Goal
Find the password for the next level in `data.txt`. It is in one of the few human-readable strings in the file, preceded by several `=` characters.

## Concept
Some files are mostly binary data, so printing them with `cat` fills the screen with junk. The `strings` command pulls out only the human-readable text. `grep` can then filter that text down to the lines that match a pattern, and a pipe (`|`) connects the two.

## Commands Used
`ssh`, `strings`, `grep`, `|`

## What I Did
I logged in with `ssh` and ran `strings` on `data.txt` to extract the readable text. I piped the output into `grep` with a run of `=` characters as the pattern. That cut a large amount of output down to a few lines, and the password was in one of them.

## What I Learned
Chaining commands lets me break a problem into steps: extract the readable text, then filter it. I also learned that `strings` is the right tool for looking inside binary files.
