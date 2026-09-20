## Level 8 to Level 9

## Goal
Find the password for the next level in `data.txt`. It is the only line of text that appears once in the file.

## Concept
`uniq` filters out repeated lines, but it only compares lines that sit next to each other. To find a line that is unique across a whole file, the file must be sorted first so identical lines end up together. A pipe (`|`) passes the output of one command straight into the next.

## Commands Used
`ssh`, `sort`, `uniq -u`, `|`

## What I Did
I logged in with `ssh` and sorted the contents of the file with `sort`. I piped that into `uniq` with the `-u` flag, which prints only the lines that are not repeated. That left a single line, which was the password.

## What I Learned
Small commands become powerful when chained together with pipes. I also learned that `uniq` needs sorted input to work properly, which is why `sort` always comes first.
