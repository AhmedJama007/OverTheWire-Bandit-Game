## Level 7 to Level 8

## Goal
Find the password for the next level in a very large text file. It is stored on the same line as the word "millionth".

## Concept
Opening a massive file and scrolling through it by hand is slow and unreliable. Command-line tools can search a file for a specific pattern and print only the lines that match. This turns a huge file into a single line of output.

## Commands Used
`ssh`, `ls`, `grep`

## What I Did
I logged in with `ssh` and used `ls` to find the data file in the home directory. I then ran `grep` with the word "millionth" on that file. It printed only the matching line, which held the password next to the word.

## What I Learned
Text filtering tools are crucial for finding a needle in a haystack. `grep` is a foundational tool for searching files and parsing logs, and I expect to use it constantly.
