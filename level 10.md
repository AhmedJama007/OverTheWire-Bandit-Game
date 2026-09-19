## Level 10 to Level 11

## Goal
Find the password for the next level in `data.txt`. The file contains Base64 encoded data.

## Concept
Base64 is a way of encoding data as plain text characters. It is not encryption, because anyone can reverse it without a key. The `base64` command can decode it back into the original text.

## Commands Used
`ssh`, `ls`, `base64 -d`

## What I Did
I logged in with `ssh` and confirmed the file was in the home directory. I read the `base64` man page to find the decode flag. Running `base64 -d` on the file turned the encoded text back into a readable line, which was the password.

## What I Learned
Encoding and encryption are different things. Base64 only changes how data is represented, so it can be reversed by anyone. I also learned to check the man page and synopsis to work out the right flag and argument order.
