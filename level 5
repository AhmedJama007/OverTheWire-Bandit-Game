## Level 5 to Level 6

## Goal
Find the file with the password for the next level somewhere under the `inhere` directory. It is human-readable, 1033 bytes in size, and not executable.

## Concept
When a directory holds many subdirectories, checking files one by one is slow. The `find` command searches through directories automatically and filters results by properties like type, size, and permissions. Combining filters narrows a large search down to a single file.

## Commands Used
`ssh`, `cd`, `ls`, `find`, `file`, `cat`

## What I Did
I logged in with `ssh` and moved into `inhere`. Running `file` on everything only showed directories, so I switched to `find`. I combined filters for file type, exact size in bytes, and not executable, which returned a single match. I confirmed it was readable with `file` and printed it with `cat`.

## What I Learned
`find` can search recursively and combine several conditions at once. It is far faster than looking through directories by hand, and it is a tool I will use often for locating files on a server.
