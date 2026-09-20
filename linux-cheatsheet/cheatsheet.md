# Linux Cheat Sheet

Replace anything in `<angle brackets>` with your own value. Anything in `[square brackets]` is optional.

## The Method

1. Read the problem and note every clue
2. Pick the tool that matches the problem (see the table below)
3. Fill in the pattern with your values
4. Check the output, then adjust and repeat

## Which Tool for Which Problem

| I want to... | Use |
| --- | --- |
| See hidden files | `ls -a` |
| Find a file by name, size, or owner | `find` |
| Find text inside a file | `grep` |
| Find the line that appears once | `sort` then `uniq -u` |
| Pull readable text out of a binary file | `strings` |
| Check what type a file is | `file` |
| Decode Base64 | `base64 -d` |
| Swap letters or characters | `tr` |
| Unpack a compressed file | `gzip -d`, `bzip2 -d`, `tar xf` |
| Log in with a key | `ssh -i` |
| Talk to a port | `nc` |

## Moving Around and Reading

| I want to... | Pattern | Example |
| --- | --- | --- |
| Go into a folder | `cd <folder>` | `cd projects` |
| Go up one level | `cd ..` | `cd ..` |
| Go to my home folder | `cd ~` | `cd ~` |
| See where I am | `pwd` | `pwd` |
| List files | `ls [options] [folder]` | `ls -la projects` |
| Show hidden files too | `ls -a` | `ls -a` |
| Read a file | `cat <file>` | `cat notes.txt` |
| Read a file with an odd name | `cat "./<file>"` | `cat "./-notes"` |
| Read the first lines | `head -n <number> <file>` | `head -n 5 notes.txt` |
| Check the file type | `file <file>` | `file notes.txt` |

## Files and Folders

| I want to... | Pattern | Example |
| --- | --- | --- |
| Make a folder | `mkdir <name>` | `mkdir backup` |
| Make a private temp folder | `mktemp -d` | `mktemp -d` |
| Copy a file | `cp <source> <destination>` | `cp notes.txt backup/` |
| Rename or move a file | `mv <old> <new>` | `mv notes.txt old-notes.txt` |
| Change permissions | `chmod <mode> <file>` | `chmod 600 mykey` |

## Searching with find

Pattern:

```
find <where to start> [filters] 2>/dev/null
```

| Where to start | Meaning |
| --- | --- |
| `.` | The current folder |
| `/` | The whole server |
| `<path>` | A specific folder |

| Filter | Pattern | Example |
| --- | --- | --- |
| By name | `-name "<name>"` | `-name "*.log"` |
| Files only | `-type f` | `-type f` |
| Folders only | `-type d` | `-type d` |
| Exact size | `-size <number><unit>` | `-size 1000c` |
| Bigger than | `-size +<number><unit>` | `-size +5M` |
| Smaller than | `-size -<number><unit>` | `-size -5M` |
| By owner | `-user <user>` | `-user alex` |
| By group | `-group <group>` | `-group staff` |
| Not executable | `! -executable` | `! -executable` |

Size units: `c` bytes, `k` kilobytes, `M` megabytes, `G` gigabytes. No space between the number and the unit.

Full example:

```
find / -type f -user alex -size 1000c 2>/dev/null
```

## Searching with grep

| I want to... | Pattern | Example |
| --- | --- | --- |
| Show lines containing text | `grep "<pattern>" <file>` | `grep "error" app.log` |
| Ignore upper and lower case | `grep -i "<pattern>" <file>` | `grep -i "error" app.log` |
| Show line numbers | `grep -n "<pattern>" <file>` | `grep -n "error" app.log` |
| Show lines that do not match | `grep -v "<pattern>" <file>` | `grep -v "error" app.log` |
| Count matching lines | `grep -c "<pattern>" <file>` | `grep -c "error" app.log` |
| Show lines after a match | `grep -A <number> "<pattern>" <file>` | `grep -A 2 "error" app.log` |
| Search a whole folder | `grep -r "<pattern>" <folder>` | `grep -r "error" logs/` |

## Pipes and Redirection

```
<command 1> | <command 2>        # pass the output of one command into the next
<command> > <file>              # save output to a file (overwrites it)
<command> >> <file>             # add output to the end of a file
<command> < <file>              # feed a file into a command
<command> 2>/dev/null           # hide error messages
```

Common chains:

```
sort <file> | uniq -u               # lines that appear once
sort <file> | uniq -d               # lines that are repeated
sort <file> | uniq -c               # count how often each line appears
strings <file> | grep "<pattern>"   # readable text that matches
history | grep "<pattern>"          # search past commands
```

Remember: `uniq` only compares neighbouring lines, so always `sort` first.

## Decoding and Unpacking

| I want to... | Pattern | Example |
| --- | --- | --- |
| Decode Base64 | `base64 -d <file>` | `base64 -d message.txt` |
| Swap characters | `tr '<from>' '<to>' < <file>` | `tr 'a-z' 'A-Z' < notes.txt` |
| Apply ROT13 | `tr 'A-Za-z' 'N-ZA-Mn-za-m' < <file>` | `tr 'A-Za-z' 'N-ZA-Mn-za-m' < message.txt` |
| Turn a hexdump back into binary | `xxd -r <file> > <output>` | `xxd -r dump.txt > data.bin` |
| Unpack gzip | `gzip -d <file>.gz` | `gzip -d data.gz` |
| Unpack bzip2 | `bzip2 -d <file>.bz2` | `bzip2 -d data.bz2` |
| Unpack tar | `tar xf <file>.tar` | `tar xf data.tar` |

Repeated compression loop:

1. `file <name>` to read the type
2. Rename to match (`.gz` or `.bz2`) if the tool needs it, `tar` does not
3. Unpack it
4. Repeat until `file` says `ASCII text`

## Remote and Network

| I want to... | Pattern | Example |
| --- | --- | --- |
| Log in to a server | `ssh <user>@<host> -p <port>` | `ssh alex@server.example.com -p 22` |
| Log in with a key | `ssh -i <keyfile> <user>@<host> -p <port>` | `ssh -i mykey alex@server.example.com -p 22` |
| Copy a file from a server | `scp -P <port> <user>@<host>:<remote file> <destination>` | `scp -P 22 alex@server.example.com:notes.txt .` |
| Connect to a port | `nc <host> <port>` | `nc localhost 8080` |
| Check if a port is open | `nc -vz <host> <port>` | `nc -vz server.example.com 22` |
| Test a connection | `ping -c <count> <host>` | `ping -c 3 server.example.com` |
| Look up a DNS address | `dig +short <host>` | `dig +short server.example.com` |

Watch out for:

- `ssh` uses lowercase `-p` for the port, `scp` uses capital `-P`
- Keys need `chmod 600 <keyfile>` or SSH refuses them
- `nc` is not a shell, whatever you type is sent as data

## Shortcuts

| I want to... | Do this |
| --- | --- |
| See past commands | `history` |
| Run a past command by number | `!<number>` |
| Repeat the last command | `!!` |
| Search past commands | Ctrl+R, press again for older matches |
| Edit a found command before running it | Ctrl+J |
| Autocomplete a name | Tab |
| Cancel what is running | Ctrl+C |

## Getting Unstuck

| I want to... | Pattern | Tip |
| --- | --- | --- |
| Read the manual | `man <command>` | Press `/` then a word to search, `q` to quit |
| Get quick help | `<command> --help` | Shorter than the manual |
