## Level 14 to Level 15

## Goal
Get the password for the next level by submitting the current level's password to port 30000 on localhost.

## Concept
Not everything on a server is a shell. A service can listen on a network port and reply to whatever it receives. `nc` (netcat) opens a plain connection to a host and port, and passes what I type straight to the service. It does not run commands, so anything I type is sent as data.

## Commands Used
`cat`, `nc`, `|`

## What I Did
I read the current password from its file with `cat`. I first typed a command inside the `nc` session, which sent the command text as the password and got rejected. I then connected properly with `nc localhost 30000` and sent only the password itself. The service replied with the password for the next level.

## What I Learned
`nc` is not a shell, so it sends exactly what I type. I also learned that `nc` takes the port as a plain argument, with no `-p` flag and no `user@`. Piping the password in with `cat file | nc localhost 30000` avoids copying and pasting.
