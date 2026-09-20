## Level 12 to Level 13

## Goal
Find the password for the next level in `data.txt`, which is a hexdump of a file that has been compressed many times over. I had to work in a temporary directory under `/tmp`.

## Concept
A hexdump is a text representation of binary data, and it can be reversed back into the original binary. The result was compressed repeatedly, with gzip, bzip2, and tar layers nested inside each other. The `file` command reads the real content of a file, so it tells you which layer you are looking at even when the file name says nothing useful.

## Commands Used
`ssh`, `mktemp -d`, `cp`, `mv`, `xxd -r`, `file`, `gzip -d`, `bzip2 -d`, `tar xf`, `ls`, `cat`

## What I Did
I created a working directory under `/tmp` with `mktemp -d` and copied the data file into it. I reversed the hexdump with `xxd -r` and redirected the output into a new file. From there I repeated the same loop: run `file` to find the type, rename the file with the matching extension where the tool needed one, decompress it, and check again. When `file` finally reported ASCII text, I read it with `cat`.

## What I Learned
Real file types come from the content, not the name, so `file` is worth running every round. Each tool behaves differently: `gzip -d` and `bzip2 -d` replace the original file, while `tar xf` leaves the archive and adds the extracted file next to it. I also learned to work in a private `/tmp` directory, since my home directory was not writable.
