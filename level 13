## Level 13 to Level 14

## Goal
Log in to the next level using a private SSH key instead of a password. The password for the next level is stored in `/etc/bandit_pass/bandit14`, which only the user `bandit14` can read.

## Concept
SSH can authenticate with a key pair instead of a password. The private key proves who you are, so you never type a password. The server also refuses SSH connections that come from itself, so the key has to be used from my own machine. SSH also rejects private keys that other users on the system could read, so the key file needs strict permissions.

## Commands Used
`ssh -i`, `scp`, `chmod 600`, `cat`, `exit`

## What I Did
I first tried to connect to `localhost` from inside the server, and it was blocked. I logged out and copied the key to my own machine with `scp`, using the capital `-P` flag for the port. I locked the key down with `chmod 600`, then logged in as the next user with `ssh -i` and the key file. Once inside, I read the password file with `cat`.

## What I Learned
Key-based login is how SSH is used in real work, and it is more secure than passwords. I learned that `ssh` uses `-p` for the port while `scp` uses `-P`, and that error messages from the server are worth reading closely. Two of my failed attempts came from typos in a file name and a username, so I now check spelling before assuming the command is wrong.
