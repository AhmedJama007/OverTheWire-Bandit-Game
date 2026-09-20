## Level 4 to Level 5

## Goal
Find the one human-readable file among several in the `inhere` directory. It holds the password for the next level.

## Concept
File names do not tell you what is inside a file. Most of the files in this directory contain binary data that looks like gibberish if you print it. The `file` command checks the actual content and reports the type, so you can tell readable text from everything else.

## Commands Used
`ssh`, `cd`, `ls`, `file`, `cat`

## What I Did
I logged in with `ssh` and moved into the `inhere` directory with `cd`. I ran `file ./*` to check every file at once. Only one was reported as ASCII text, so I read it with `cat "./<filename>"`.

## What I Learned
You can check what kind of data a file holds before opening it. Starting the names with `./` stops files with dashes in their names from being misread as options, which I learned in the earlier level.
