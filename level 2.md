## Level 1 to Level 2

## Goal
Read the contents of a file named with a special character (a dash `-`). It holds the password for the next level.

## Concept
Some file names can trick the command line into treating them as flags or arguments instead of files. A lone dash usually means "read from standard input", so the command waits for input instead of opening the file. Using a path tells the shell to treat it as a literal file.

## Commands Used
`ssh`, `ls`, `cat`, `./`

## What I Did
I logged in with `ssh` and used `ls` to find the file. Running `cat` on the dash alone made the terminal hang. Using `cat "./-"` pointed to the file in the current directory, and it printed the contents.

## What I Learned
Understanding relative paths is not just for navigating. It also lets you handle awkwardly named files that would otherwise be misread as arguments.
