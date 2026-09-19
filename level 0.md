## Level 0 to Level 1

## Goal
Log in to the Bandit server over SSH, then find and read the file that holds the password for the next level.

## Concept
The command line is text-based. To work on a remote machine, you first need to connect securely with SSH. Once connected, you move around and read files using simple commands.

## Commands Used
`ssh`, `ls`, `cat`

## What I Did
I connected to the game server with `ssh` on port 2220 using the username given in the level. I used `ls` to list the files in the home directory, then `cat` to print the contents of the file I found there.

## What I Learned
How to open an SSH connection and how to look around and read a file on a remote server. It is the first step in remote server administration, and every later level builds on it.
