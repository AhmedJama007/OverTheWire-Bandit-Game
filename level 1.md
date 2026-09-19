## Level 1 to Level 2

## Goal
Read the contents of a file named `-` in the home directory. It holds the password for the next level.

## Concept
Some file names can trick the command line into treating them as options instead of files. A lone dash tells many commands to read from standard input, so the shell never opens the file. Giving the file a path makes it clear that it is a real file.

## Commands Used
`ssh`, `ls`, `cat`, `./`

## What I Did
I logged in with `ssh` and used `ls` to confirm the file was there. Running `cat` on the dash alone made the terminal hang, waiting for input. Putting `./` in front of the name told the shell to look for a file in the current directory, and `cat` printed its contents.

## What I Learned
Relative paths do more than help you navigate. They also let you handle awkwardly named files that would otherwise be misread as arguments.
