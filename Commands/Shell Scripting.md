# Shell Scripting Cheatsheet

## Basics

## Shebang
- #!/bin/bash: Indicates that the script should be run in the Bash shell.

## Variables
- VAR=value: Assign a value to a variable.
- echo $VAR: Access the value of a variable.
- readonly VAR: Make a variable read-only.

## Comments
- `# This is a comment`: Single line comment.
- `<< 'COMMENT' ... COMMENT`: Multi-line comment using a Here document.


# Control Structures

## Conditional Statements

- if Statement:
```
if [ condition ]; then
    # commands
fi
```

- if-else Statement:
```
if [ condition ]; then
    # commands
else
    # other commands
fi
```

- if-elif-else Statement:
```
if [ condition1 ]; then
    # commands
elif [ condition2 ]; then
    # other commands
else
    # other commands
fi
```

# Loops

- for Loop:
```
for var in list; do
    # commands
done
```

- while Loop:
```
while [ condition ]; do
    # commands
done
```

- until Loop:
```
until [ condition ]; do
    # commands
done
```

# Functions

- Define a Function:
```
function_name() {
    # commands
}
```

- Call a Function:
```
function_name
```

# Input/Output

## Reading Input

- read var: Read input from the user and store it in a variable.
```
read var
```

## Output

- echo: Print text to the terminal.
```
echo "Hello, World!"
```

# File Redirection

- `>: Redirect output to a file (overwrite).`
```
echo "Hello" > file.txt
```

- `>>: Redirect output to a file (append).`
```
echo "Hello" >> file.txt
```

- `<: Redirect input from a file.`
```
read var < file.txt
```

# File Tests

## Common File Test Conditions

- -e file: Check if file exists.
- -d file: Check if directory exists.
- -f file: Check if file exists and is a regular file.
- -r file: Check if file is readable.
- -w file: Check if file is writable.
- -x file: Check if file is executable.

## String Tests

- -z string: Check if string is empty.
- -n string: Check if string is not empty.
- string1 = string2: Check if strings are equal.
- string1 != string2: Check if strings are not equal.

# Arithmetic Operations

- Using let:
```
let "a = 5 + 3"
echo $a  # 8
```

- Using (( )):
```
a=$(( 5 + 3 ))
echo $a  # 8
```

# Arrays

- Declare an Array:
```
array=(val1 val2 val3)
```

- Access Array Elements:
```
echo ${array[0]}
```

- All Elements:
```
echo ${array[@]}
```

- Array Length:
```
echo ${#array[@]}
```

# Example Script
```
#!/bin/bash

# Define a variable
NAME="John Doe"

# Function definition
greet() {
    echo "Hello, $NAME"
}

# Conditional statement
if [ -n "$NAME" ]; then
    greet
else
    echo "Name is empty"
fi

# Loop
for i in {1..5}; do
    echo "Number $i"
done
```
