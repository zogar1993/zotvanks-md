## Commands

### Common
ls -> list everything inside a directory
more <filename> -> see the content of a file, you can scroll by pressing space
mkdir <dirname> -> create a directory
mv <filename> <filename2|dirname> -> renames if directory does not exist, moves it into the directory if it does. mv can be used to rename directories.
cd <dirname> -> change directory
pwd -> print working directory
cd .. -> change to parent directory
cp <filename> <filename2|dirname> -> copies if directory does not exist, copies into it into the directory if it does.
rmdir -> removes empty dir
rm -> removes file
ls -l -> get more information about files. -rwxrwxrwx: user, group, other
chmod ugo<+|->rwx <filename>
groups -> lists the groups you are in
man <command> -> help for the command
find <path> -name "<text_to_mach>" -> find files that match name
cat <+filename> -> concatenates files 
cat <+filename> > <file> -> writes the concat to a file overwritting it
cat <+filename> >> <file> -> writes the concat at the end of the file
df -> checks disk free space
ps aux -> shows processes
grep <word> <path> -> find every occurrence of the word

### Kill a process
ps aux | grep <text>
kill <PID>

### Misc
| pipes the result of a command as an input to the next

~ is a selector for home, and can be used standalone or to create relative paths to it (~/wea).

file selectors can use wildcards, like * or ?. * matches any characters or none, ? matches any one character.

Files have only one group owner. To give access to more than one group, we use ACLs (Access Control Lists)

When you login, you are in the home directory

-r for all folders recursively

Linux multiple disks are mounted into just one tree structure

## Sources

- https://linuxsurvival.com