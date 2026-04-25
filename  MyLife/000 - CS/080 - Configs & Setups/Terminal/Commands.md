

## Git (Mac & Linux)

`lazygit` shows a responsive UI-Layout for your Git-workflow



## Finding a String (Mac & Linux)

`find . -type f -exec grep --color=always x {} ';'

. -> in this directory
-type f -> specifying its a file not a dir
-exec -> for every file I find I wanna execute the grep command
grep -> looks thought the file
--color=always -> highlights the string 
x -> the String you want to find 
{} -> will append every file found throught the find command to the grep command 
';' -> terminate the string with a semicolon (bash would be backward slash)
## Finding files

#### fzf (Mac & Linux)

`fzf` and tab to search for files,
`fzf --preview='cat {}'` also reveals a preview of the file,
`nvim $(fzf --preview='cat {}')` lets you open it in NVIM.

## Kill processes easily (Mac & Linux)

If you want to call a process in Linux, you would need to type this:

```bash
ps -eat | grep *
```

ps to list the processes, then pipe that output to grep and then type the name of the process, this returns a list of processes with their Id's.
Then you would need to kill them with another command:

```zsh
kill -9 *
```

Although, their is a much easier  with `fzf`:

```bash
kill -9 ** # ** tells fzf to fuzzy find
		   # if you then press tab it will
		   # bring up a list of all processes.
		   # You can also search with typing.
		   # Then just press 2x enter and done.
```