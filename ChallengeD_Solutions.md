# Pipes, Redirection and REGEXExternal tool

# The final command line is 
cat /etc/services | grep '^[a-zA-Z]' | awk '{print $1}' | sort -u > ~/uniqueservices.txt && wc -l ~/uniqueservices.txt

# Explanations
This is a chain of four Linux commands used to create a file named uniqueservices.txt in your home directory (~).

## cat /etc/services
cat is a command used to display the contents of a file.

/etc/services is a system file that contains a list of well-known services associated with their port numbers and protocols.

## grep '^[a-zA-Z]'
grep is a command used to filter text based on patterns.

' ^[a-zA-Z] ' is a regular expression that matches lines that start with an alphabet character (either uppercase or lowercase). This filters the output of cat /etc/services to only include lines that represent actual service names (excluding comments or blank lines).

## awk '{print $1}'
awk is a powerful text processing tool.

{} is a block of code that gets executed for each line of input passed to awk.

print $1 inside the block instructs awk to print only the first field (service name) of each line.

## sort -u > ~/uniqueservices.txt && wc -l ~/uniqueservices.txt
sort is used to arrange lines in a specific order.

-u option tells sort to remove duplicate lines, resulting in a unique list of service names, and > redirects the output of the previous command (awk) to a new file named

uniqueservices.txt in your home directory (~).

wc is a command used for counting things in a file.

-l option instructs wc to count only the number of lines in the file.

~/uniqueservices.txt specifies the file to be counted.

# Deliverables
![Linux](/Images/ChallengeD_1.png)
![Linux](/Images/ChallengeD_2.png)
