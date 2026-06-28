# Bash Scripting Basics

## What is Bash?

Bash (Bourne Again Shell) is a command-line interpreter used in Linux systems.

A Bash script is a file containing a series of commands that are executed automatically.

Bash scripting helps automate repetitive tasks.

---

## Creating a Bash Script

Create a file:

```bash
nano script.sh
```

Example script:

```bash
#!/bin/bash

echo "Hello, World!"
```

Save the file and make it executable:

```bash
chmod +x script.sh
```

Run the script:

```bash
./script.sh
```

---

## Variables

Variables store data.

Example:

```bash
#!/bin/bash

name="Zahrah"

echo "Hello $name"
```

Output:

```text
Hello Zahrah
```

---

## User Input

Accept input from the user.

```bash
#!/bin/bash

echo "Enter your name:"
read name

echo "Welcome $name"
```

---

## Conditional Statements

### if Statement

```bash
#!/bin/bash

num=10

if [ $num -gt 5 ]
then
    echo "Number is greater than 5"
fi
```

---

### if-else Statement

```bash
#!/bin/bash

num=3

if [ $num -gt 5 ]
then
    echo "Greater than 5"
else
    echo "Less than or equal to 5"
fi
```

---

## Loops

### for Loop

```bash
#!/bin/bash

for i in 1 2 3 4 5
do
    echo $i
done
```

---

### while Loop

```bash
#!/bin/bash

count=1

while [ $count -le 5 ]
do
    echo $count
    count=$((count + 1))
done
```

---

## Functions

Functions allow code reuse.

```bash
#!/bin/bash

greet() {
    echo "Welcome to Linux"
}

greet
```

---

## Command Line Arguments

Arguments can be passed to scripts.

```bash
#!/bin/bash

echo "First Argument: $1"
echo "Second Argument: $2"
```

Run:

```bash
./script.sh hello world
```

Output:

```text
First Argument: hello
Second Argument: world
```

---

## Exit Status

Every command returns an exit status.

Check the previous command status:

```bash
echo $?
```

Common values:
- 0 = Success
- Non-zero = Error

---

## Useful Bash Script Example

Check if a file exists:

```bash
#!/bin/bash

if [ -f file.txt ]
then
    echo "File exists"
else
    echo "File not found"
fi
```

---

## Best Practices

- Use meaningful variable names
- Add comments where needed
- Test scripts before production use
- Use proper indentation
- Keep scripts simple and readable

---
