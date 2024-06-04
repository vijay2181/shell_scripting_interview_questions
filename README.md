# Shell Scripting Interview Questions and Answers

## 1. How do you specify the interpreter for a shell script?
****Answer:**** Use the shebang `#!` followed by the path to the interpreter.
```sh
#!/bin/bash
echo "Script running"
```

## 2. How can you assign a value to a variable and print it?
****Answer:**** Assign using = and print with echo.
```sh

greeting="Hello"
echo "$greeting"
```

## 3. What technique allows command output to be used as a variable's value?
****Answer:**** Command substitution.

```sh

time_now=$(date)
echo "Current time: $time_now
```

## 4. How do you capture input from the user?
****Answer:**** Use the read command.

```sh

echo "Enter your age:"
read age
echo "Your age is $age"
```

## 5. What does an exit code signify in a shell script?
****Answer:**** It indicates the success (0) or failure (non-zero) of the last executed command.

```sh

ls /nonexistent
echo $?  # Output: non-zero (failure)
```

## 6. How can you make decisions based on conditions?
****Answer:**** Use if, elif, else, and fi.

```sh

if [ -d "/path/to/dir" ]; then
  echo "Directory exists"
else
  echo "Directory does not exist"
fi
```

## 7. What is the role of loops in scripts?
****Answer:**** To repeatedly execute commands.

```sh

for file in *.txt; do
  echo "File: $file"
done
```

## 8. How do you include comments in your script?
****Answer:**** Use the # symbol.

```sh

# This is a comment
echo "Code execution"
```

## 9. How can you access script parameters?
**Answer:** Parameters are accessed using $1, $2, etc.

```sh

echo "First parameter: $1"
```

## 10. When should you use single quotes versus double quotes?
**Answer:** Use single quotes to prevent variable expansion and double quotes to allow it.

```sh

var="world"
echo 'Hello $var'  # Output: Hello $var
echo "Hello $var"  # Output: Hello world
```

## 11. How do you test for file existence?
**Answer:** Use -e in a conditional statement.

```sh

if [ -e "myfile.txt" ]; then
  echo "File exists"
fi
```

## 12. What is the function of the case statement?
**Answer:** To handle multiple conditions.

```sh

case "$1" in
  start) echo "Starting";;
  stop) echo "Stopping";;
  *) echo "Unknown option";;
esac
```

## 13. How can you process a file line by line?
**Answer:** Use a while loop with read.

```sh

while IFS= read -r line; do
  echo "Line: $line"
done < "file.txt"
```

## 14. What is the syntax for redirecting output to a file?
**Answer:** Use > for overwrite and >> for append.

```sh

echo "Hello, World!" > output.txt
```

## 15. How do you search for text within files?
**Answer:** Use the grep command.

```sh

grep "search_term" file.txt
```

## 16. How do you define a reusable block of code?
**Answer:** Use functions.

```sh

greet() {
  echo "Hello, $1"
}
greet "Alice"
```

## 17. How can you make a variable available to sub-processes?
**Answer:** Use the export command.

```sh

export PATH=$PATH:/new/path
```

## 18. How do you check file permissions?
**Answer:** Use ls -l or test flags like -r, -w, and -x.

```sh

if [ -r "file.txt" ]; then
  echo "File is readable"
fi
```

## 19. How do you stop script execution upon encountering an error?
**Answer:** Use exit or set -e.

```sh

set -e
cp nonexistentfile /somewhere
echo "This won't be printed"
```

## 20. What does the shift command do?
**Answer:** It shifts the positional parameters to the left.

```sh

echo "$1"
```shift
echo "$1"
```

## 21. How do you join two strings together?
**Answer:** Concatenate them directly.

```sh

greeting="Hello"
name="Alice"
full_greeting="$greeting, $name"
echo "$full_greeting"
```

## 22. How do you retrieve the directory portion of a file path?
**Answer:** Use the dirname command.

```sh

path="/home/user/file.txt"
echo $(dirname "$path")
```

## 23. How can you perform arithmetic operations?
**Answer:** Use expr or $(( )).

```sh

sum=$((3 + 5))
echo "Sum: $sum"
```

## 24. What is the function of the set command?
**Answer:** To change shell options and positional parameters.

```sh

set -x  # Enable debugging
```

## 25. How do you verify the existence of a directory?
**Answer:** Use the -d flag in a conditional statement.

```sh

if [ -d "/path/to/dir" ]; then
  echo "Directory exists"
fi
```

## 26. How can you extract specific fields from a line of text?
**Answer:** Use the cut command.

```sh

echo "name:age:location" | cut -d ':' -f 2
```

## 27. How do you replace text in a file?
**Answer:** Use the sed command.

```sh

sed -i 's/old_text/new_text/g' file.txt
```

## 28. When would you use an until loop?
**Answer:** To repeat commands until a condition is true.

```sh

counter=1
until [ $counter -gt 5 ]; do
  echo "Counter: $counter"
  counter=$((counter + 1))
done
```

## 29. How do you store the output of a command in a variable?
**Answer:** Use command substitution.

```sh

current_user=$(whoami)
echo "Current user: $current_user"
```

## 30. What does the tee command do?
**Answer:** Reads from standard input and writes to standard output and files.

```sh

echo "Hello, World!" | tee output.txt
```

## 31. How can you check if a string contains another string?
**Answer:** Use a conditional statement with * wildcard.

```sh

string="Hello, World!"
if [[ "$string" == *"World"* ]]; then
  echo "Substring found"
fi
```

## 32. What is the printf command used for?
**Answer:** For formatted output.

```sh

printf "Name: %s, Age: %d\n" "Alice" 30
```

## 33. How can you split a string into an array?
**Answer:** Use the IFS variable.

```sh

string="a,b,c"
IFS=',' read -r -a array <<< "$string"
echo "${array[0]}"
```

## 34. How do you get the filename from a path?
**Answer:** Use the basename command.

```sh

path="/home/user/file.txt"
echo $(basename "$path")
```

## 35. How can you check if a string is empty?
**Answer:** Use -z in a conditional statement.

```sh

if [ -z "$string" ]; then
  echo "String is empty"
fi
```

## 36. What does the pwd command do?
**Answer:** Prints the current working directory.

```sh

echo "Current directory: $(pwd)"
```

## 37. How do you trim whitespace from a string?
**Answer:** Use sed or parameter expansion.

```sh

string="  Hello, World!  "
trimmed=$(echo "$string" | sed 's/^ *//;s/ *$//')
echo "$trimmed"
```

## 38. What is the trap command used for?
**Answer:** To catch signals and execute commands when they occur.

```sh

trap "echo 'Interrupted!'; exit" INT
```

## 39. How do you compare two strings?
**Answer:** Use = or != inside [[ ]] or [ ].

```sh

str1="hello"
str2="world"
if [ "$str1" = "$str2" ]; then
  echo "Strings are equal"
else
  echo "Strings are not equal"
fi
```

## 40. How do you check if a command exists?
**Answer:** Use command -v or which.

```sh

if command -v git >/dev/null 2>&1; then
  echo "Git is installed"
else
  echo "Git is not installed"
fi
```

## 41. How do you find the number of arguments passed to a script?
**Answer:** Use $#.

```sh

echo "Number of arguments: $#"
```

## 42. How do you create a symbolic link?
**Answer:** Use the ln -s command.

```sh

ln -s /path/to/original /path/to/link
```

## 43. How do you read a file into a variable?
**Answer:** Use command substitution with cat.

```sh

file_content=$(cat file.txt)
echo "$file_content"
```

## 44. How do you perform a logical AND in a shell script?
**Answer:** Use &&.

```sh

if [ -f "file1" ] && [ -f "file2" ]; then
  echo "Both files exist"
fi
```

## 45. How do you perform a logical OR in a shell script?
**Answer:** Use ||.

```sh

if [ -f "file1" ] || [ -f "file2" ]; then
  echo "At least one file exists"
fi
```

## 46. How do you check if a variable is set?
**Answer:** Use -z or -n.

```sh

if [ -n "$var" ]; then
  echo "Variable is set"
fi
```

## 47. How do you replace a substring in a variable?
**Answer:** Use parameter expansion.

```sh

str="Hello, World!"
new_str=${str/World/```shell}
echo "$new_str"
```

## 48. How do you convert a string to lowercase?
**Answer:** Use tr.

```sh

str="HELLO"
lower=$(echo "$str" | tr 'A-Z' 'a-z')
echo "$lower"
```

## 49. How do you convert a string to uppercase?
**Answer:** Use tr.

```sh

str="hello"
upper=$(echo "$str" | tr 'a-z' 'A-Z')
echo "$upper"
```

## 50. How do you generate a random number?
**Answer:** Use $RANDOM.

```sh

echo "Random number: $RANDOM"
```

## 51. How do you check if a number is even or odd?
**Answer:** Use arithmetic expansion.

```sh

num=4
if ((num % 2 == 0)); then
  echo "Even"
else
  echo "Odd"
fi
```

## 52. How do you display the first N lines of a file?
**Answer:** Use the head command.

```sh

head -n 10 file.txt
```

## 53. How do you display the last N lines of a file?
**Answer:** Use the tail command.

```sh

tail -n 10 file.txt
```

## 54. How do you count the number of lines in a file?
**Answer:** Use wc -l.

```sh

wc -l < file.txt
```

## 55. How do you count the number of words in a file?
**Answer:** Use wc -w.

```sh

wc -w < file.txt
```

## 56. How do you find files containing specific text?
**Answer:** Use grep -rl.

```sh

grep -rl "search_text" /path/to/dir
```

## 57. How do you list all environment variables?
**Answer:** Use the printenv command.

```sh

printenv
```

## 58. How do you change the current working directory?
**Answer:** Use the cd command.

```sh

cd /path/to/dir
```

## 59. How do you print a sequence of numbers?
**Answer:** Use the seq command.

```sh

seq 1 10
```

## 60. How do you pause the execution of a script for a specific time?
**Answer:** Use the sleep command.

```sh

sleep 5
```

## 61. How do you find the type of a file?
**Answer:** Use the file command.

```sh

file filename
```

## 62. How do you remove duplicate lines from a file?
**Answer:** Use the sort and uniq commands.

```sh

sort file.txt | uniq
```

## 63. How do you sort lines in a file?
**Answer:** Use the sort command.

```sh

sort file.txt
```

## 64. How do you merge multiple files into one?
**Answer:** Use the cat command.

```sh

cat file1.txt file2.txt > merged.txt
```

## 65. How do you display the disk usage of a directory?
**Answer:** Use the du command.

```sh

du -```sh /path/to/dir
```

## 66. How do you check available disk space?
**Answer:** Use the df command.

```sh

df -h
```

## 67. How do you display running processes?
**Answer:** Use the ps command.

```sh

ps aux
```

## 68. How do you kill a process by its name?
**Answer:** Use the pkill command.

```sh

pkill process_name
```

## 69. How do you find the process ID of a running process?
**Answer:** Use the pidof command.

```sh

pidof process_name
```

## 70. How do you check the status of a service?
**Answer:** Use the systemctl command.

```sh

systemctl status service_name
```

## 71. How do you start a service?
**Answer:** Use the systemctl start command.

```sh

systemctl start service_name
```

## 72. How do you stop a service?
**Answer:** Use the systemctl stop command.

```sh

systemctl stop service_name
```

## 73. How do you enable a service to start on boot?
**Answer:** Use the systemctl enable command.

```sh

systemctl enable service_name
```

## 74. How do you disable a service from starting on boot?
**Answer:** Use the systemctl disable command.

```sh

systemctl disable service_name
```

## 75. How do you display the system's hostname?
**Answer:** Use the hostname command.

```sh

hostname
```

## 76. How do you change the system's hostname?
**Answer:** Use the hostnamectl command.

```sh

hostnamectl set-hostname new_hostname
```

## 77. How do you display the current date and time?
**Answer:** Use the date command.

```sh

date
```

## 78. How do you set the system date and time?
**Answer:** Use the date command with appropriate options.

```sh

date MMDDhhmm[[CC]YY][.ss]
```

## 79. How do you add a user to the system?
**Answer:** Use the useradd command.

```sh

useradd username
```

## 80. How do you delete a user from the system?
**Answer:** Use the userdel command.

```sh

userdel username
```

## 81. How do you add a group to the system?
**Answer:** Use the groupadd command.

```sh

groupadd groupname
```

## 82. How do you delete a group from the system?
**Answer:** Use the groupdel command.

```sh

groupdel groupname
```

## 83. How do you add a user to a group?
**Answer:** Use the usermod -aG command.

```sh

usermod -aG groupname username
```

## 84. How do you display the groups a user belongs to?
**Answer:** Use the groups command.

```sh

groups username
```

## 85. How do you change the ownership of a file?
**Answer:** Use the chown command.

```sh

chown user:group file.txt
```

## 86. How do you change the permissions of a file?
**Answer:** Use the chmod command.

```sh

chmod 755 file.txt
```

## 87. How do you recursively change the ownership of a directory?
**Answer:** Use the chown -R command.

```sh

chown -R user:group /path/to/dir
```

## 88. How do you recursively change the permissions of a directory?
**Answer:** Use the chmod -R command.

```sh

chmod -R 755 /path/to/dir
```

## 89. How do you create an archive of a directory?
**Answer:** Use the tar command.

```sh

tar -cvf archive.tar /path/to/dir
```

## 90. How do you extract an archive?
**Answer:** Use the tar command.

```sh

tar -xvf archive.tar
```

## 91. How do you compress a file using gzip?
**Answer:** Use the gzip command.

```sh

gzip file.txt
```

## 92. How do you decompress a gzip file?
**Answer:** Use the gunzip command.

```sh

gunzip file.txt.gz
```

## 93. How do you create a compressed archive?
**Answer:** Use the tar command with compression options.

```sh

tar -czvf archive.tar.gz /path/to/dir
```

## 94. How do you extract a compressed archive?
**Answer:** Use the tar command with decompression options.

```sh

tar -xzvf archive.tar.gz
```

## 95. How do you find the difference between two files?
**Answer:** Use the diff command.

```sh

diff file1.txt file2.txt
```

## 96. How do you display the first few lines of a file?
**Answer:** Use the head command.

```sh

head -n 5 file.txt
```

## 97. How do you display the last few lines of a file?
**Answer:** Use the tail command.

```sh

tail -n 5 file.txt
```

## 98. How do you find the location of an executable?
**Answer:** Use the which command.

```sh

which bash
```

## 99. How do you check the version of a command?
**Answer:** Use the --version option.

```sh

bash --version
```

## 100. How do you display a calendar for a specific month and year?
**Answer:** Use the cal command.

```sh

cal 12 2023
```







