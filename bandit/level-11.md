## Level 11 to Level 12

## Goal
Find the password for the next level in `data.txt`. All lowercase and uppercase letters in the file have been rotated by 13 positions.

## Concept
ROT13 is a simple substitution cipher that replaces each letter with the one 13 places after it in the alphabet. The alphabet has 26 letters, so applying ROT13 twice returns the original text. The `tr` command replaces characters by matching two sets of characters by position, which makes it a good fit for this.

## Commands Used
`ssh`, `cat`, `tr`, `|`

## What I Did
I logged in with `ssh` and used `cat` to read the file, then piped the output into `tr`. I gave `tr` one set with every uppercase and lowercase letter, and a second set with the same letters shifted by 13 places. Each character in the first set was swapped for the one in the same position in the second set, which turned the text back into a readable line.

## What I Learned
ROT13 is not real encryption, and it is easy to reverse. I also learned that `tr` works by matching characters by position, and that it reads from standard input, so it needs a pipe or `<` to receive a file.
