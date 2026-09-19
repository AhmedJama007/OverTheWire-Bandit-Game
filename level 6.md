## Level 6 to Level 7

## Goal
Find the file with the password for the next level somewhere on the server. It is owned by user `bandit7`, owned by group `bandit6`, and is 33 bytes in size.

## Concept
The `find` command can search the whole filesystem, not just the current directory. Filtering by owner, group, and size narrows millions of files down to one. Searching system-wide also produces many "Permission denied" errors, which can be redirected so they do not hide the real result.

## Commands Used
`ssh`, `find`, `cat`, `2>/dev/null`

## What I Did
I logged in with `ssh` and started `find` from the root directory `/` so it covered the whole server. I combined filters for user, group, and exact size in bytes. I redirected the error output to `/dev/null` to keep the screen clean, which left a single path. I then printed that file with `cat`.

## What I Learned
Where `find` starts decides where it searches, and combining filters makes it precise. I also learned that stderr and stdout are separate streams, and that `2>/dev/null` discards the errors without touching the results.
