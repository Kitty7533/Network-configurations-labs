# Some other Linux Basics

## Ojectives
- Understand how to execute many commands in one
- Command grouping and conditionnal chaining
- Using ls command
- Do a better use for the cd command
- Create files and diretories
- Copy and move files and directories
- Remove A file or a directory
- Used the grep command
- Used the find command
- Redirection
- Using the editor vi

# Commands used
```bash
touch file1 (create the file "file1")
mkdir Linux (create the directory "Linux")
rmdir directory_name (remove an empty directory)
rm -r file_or_directory_name (remove an empty or not file or directory)
cd ~/TPLINUX;touch ~/TPLINUX/fic1 (Navigate on TPLinux directory and after create the file "fic1", won't work)
cd ~/TPLINUX && touch ~/TPLINUX/fic1 (Do the same thing and won't work to)
cd ~/TPLINUX || mkdir ~/TPLINUX && touch ~/TPLINUX/fic1 ( The first command navigate on TPLINUX directory and won't work, the second command create a directory named "TPLINUX" and will work and the last command create a file named "fic1" and will work too)
ls (List files on the current directory)
ls /usr/bin (List files that are on the directory "/usr/bin")
ls /usr/bin/f* (List files begin with "f" that are on the directory "/usr/bin")
ls /usr/bin/*z* (List files that content "z" in the directory "/usr/bin")
ls /usr/bin/*"user"* (List files that content the chain "user" in the directory "/usr/bin")
ls /usr/bin/?? (List files that content two characters in the directory "/usr/bin")
cp source_path destination_path (Copy a file from the source to the destination)
cp -r source_path destination_path (Copy a directory from the source to the destination)
cd .. (Go back to the parent directory means the directory which content the directory we're on)
cd . (The dot . means the current directory)
cd or cd ~ (Navigate to the personnal directory)
grep HTTP services ( Research lines which content the chain "HTTP" in the file "services")
grep -i HTTP services (Research lines which content the chain "HTTP" if it's in lower case or upper case doesn't matter in the file "services")
grep ^http services ( Research lines which begin with the chain "HTTP" in the file "services")
grep SSL$ services ( Research lines which end with the chain "SSL" in the file "services")
sed 's/SSL/ESMT/g' (Replace the chain "SSL" by the chain "ESMT")
grep SSL$ services | sed 's/SSL/ESMT/g'  ( Research lines which end with the chain "SSL" in the file "services" and after replace the chain "SSL" by the chain "ESMT")
vi file-name (Editor used to read, modify a file)
find /usr/sbin/z* or find -type f -name "z*"(Looks on the diretory /usr/sbin/ for files which begin with "z")
find -type f -name "z*" -exec ls -lh {} \;(Looks on the diretory /usr/sbin/ for files which begin with "z" and shows their size)
find -type f -name "z*"(Looks on the diretory /usr/sbin/ for files which begin with "z")
find -type f -name "z*" -size +50k(Looks on the diretory /usr/sbin/ for files which begin with "z" and whose their size is larger than 50k)
find -type f -name "z*" -size +50k -exec ls -lh {} \;(Looks on the diretory /usr/sbin/ for files which begin with "z" and whose their size is larger than 50k and shows their size)
seq 100 | more (There we have to command the pipe "|" is used then if the first command is executed it took the output of the first command as a base to execute the second command)
```

## What I learned
- The possibility to combine multiple commands in Linux using operators like '&&' (the second command will be execute only if the first one succed), '||'(the second command will be execute only if the first one fails), ';' (Executed the first command and after the second command, they're not linked)
- File system navigation depends on understanding absolute and relative paths
- The 'ls' command can be used in many ways and have options that change the output of the ls command
- There is commands that are used for copying or moving files like 'cp' with the option '-r' for the direstories and 'mv' used to rename
- The 'grep' command is used to reseash characters in a file only
- Beside the 'find' command is used to reseach files or directory depending on the option or the argument used
- The 'sed' command is used to switch a character by another one we specify
- The pipe '|' is used to execute a command based on the output of another cammand we specify
- The '-exec' option in 'find' allows executing commands on the results.
- The 'vi' editor is a powerful tool to edit files directly from the terminal (if we do: `esc + :` and add 'x' or 'wq', we quit by save our work; '!q', we quit without saving)
- Command history and repetition techniques improve efficiency in the terminal.
