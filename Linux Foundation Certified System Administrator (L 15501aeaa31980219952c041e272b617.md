# Linux Foundation Certified System Administrator (LFCS)

[JD for Linux Admin](Linux%20Foundation%20Certified%20System%20Administrator%20(L%2015501aeaa31980219952c041e272b617/JD%20for%20Linux%20Admin%2016201aeaa31980df8edad805b2d57cd1.md)

[https://github.com/ntheanh201/kodekloud-engineer](https://github.com/ntheanh201/kodekloud-engineer)

**From WSL.exe**
**IP address querying**

![Linux incident response.jpg](Linux%20Foundation%20Certified%20System%20Administrator%20(L%2015501aeaa31980219952c041e272b617/Linux_incident_response.jpg)

When working with WSL, you may need to query the IP address of the Linux distribution from the Windows host or vice versa. Here are some scenarios:

- Scenario One: Querying the Linux distribution’s IP address from the Windows host. Use the command `wsl --distribution <distro_name> --ip` (e.g., `wsl --distribution Ubuntu --ip`) to retrieve the IP address.
- Scenario Two: Querying the Windows host’s IP address from the Linux distribution. Use the command `ip route show | grep -i default | awk '{ print $3}'` to retrieve the Windows host’s IP address.

![image.png](Linux%20Foundation%20Certified%20System%20Administrator%20(L%2015501aeaa31980219952c041e272b617/image.png)

In Bash scripting, there are several special variables and characters with unique meanings. Here’s a comprehensive list of these Bash special characters and variables:

---

### **Special Variables**

| Symbol | Description |
| --- | --- |
| `$?` | Exit status of the last executed command. |
| `$@` | All positional parameters as separate quoted strings. Equivalent to `"$1" "$2" ... "$N"`. |
| `$*` | All positional parameters as a single word. Equivalent to `"$1 $2 ... $N"`. |
| `$$` | Process ID (PID) of the current shell. |
| `$!` | Process ID of the last background command. |
| `$0` | The name of the script or command being executed. |
| `$1`, `$2`, ... | Positional parameters representing the arguments passed to the script or function. |
| `$#` | The number of positional parameters passed to the script or function. |
| `$-` | Current options set for the shell (like `-e`, `-x`, etc.). |
| `$_` | The last argument to the last executed command. |

---

### **Special Characters**

| Character | Description |
| --- | --- |
| `#` | Indicates a comment. Anything following `#` on a line is ignored by the shell. |
| `?` | Wildcard matching a single character in file globbing. |
| `*` | Wildcard matching zero or more characters in file globbing. |
| `.` | Current directory or part of a filename. |
| `..` | Parent directory. |
| `~` | User's home directory (e.g., `~user` for another user's home). |
| `$` | Indicates a variable substitution or expansion. |
| `!` | Negation in tests (`if ! command`) or used in history expansion (e.g., `!123` to rerun command 123). |
| ` | ` |
| `>` | Redirects output to a file, overwriting the file. |
| `>>` | Appends output to a file. |
| `<` | Redirects input from a file. |
| `&` | Sends a command to the background (e.g., `command &`). |
| `&&` | Logical AND operator, executes the second command only if the first succeeds. |
| ` |  |
| `;` | Command separator, allows multiple commands on one line. |
| `()` | Groups commands in a subshell. |
| `{}` | Groups commands in the current shell. |
| `[]` | Used for tests, synonymous with `test` command (e.g., `[ -f file ]`). |
| `[[ ]]` | Extended test syntax with more features than `[ ]`. |
| `\` | Escape character to prevent interpretation of the next character. |
| `'` | Single quotes prevent variable expansion and special character interpretation. |
| `"` | Double quotes prevent globbing and word splitting but allow variable expansion. |
| ``` | Command substitution; executes the command and returns its output. |
| `$()` | Preferred syntax for command substitution. |

---

### **Control Flow and Operators**

| Symbol | Description |
| --- | --- |
| `:` | Null command; always returns true. |
| `-` | Indicates options passed to commands (e.g., `ls -l`). |
| `>` | Redirection of standard output to a file. |
| `<` | Redirection of standard input from a file. |
| `<<` | Here-document; allows multiple lines of input directly in the script. |
| `<<<` | Here-string; redirects a string to a command. |
| `=` | Assignment operator for variables. |
| `+=` | Appends a value to a variable. |
| `==` | Comparison operator for strings (in `[[ ]]`). |
| `!=` | String inequality (in `[[ ]]`). |
| `-eq`, `-ne`, `-lt`, `-le`, `-gt`, `-ge` | Numeric comparison operators (equal, not equal, less than, etc.). |

---

### **Advanced Constructs**

| Symbol | Description |
| --- | --- |
| `$(...)` | Command substitution; captures the output of a command. |
| `$((...))` | Arithmetic expansion; performs mathematical operations. |
| `${var}` | Parameter expansion to access or manipulate variables. |
| `${#var}` | Length of a variable’s value. |
| `${var:-default}` | Default value if the variable is unset or null. |
| `${var:=default}` | Assign a default value if the variable is unset or null. |
| `${var:offset:length}` | Substring extraction from a variable. |
| `${var/pattern/replacement}` | Replace a pattern with a replacement in the value of a variable. |
| `>>` | Append output to a file. |
| `2>` | Redirect standard error to a file. |
| `&>` | Redirect both standard output and error to a file. |

---

### **Examples**

1. **Using `$?`**:
    
    ```bash
    ls /nonexistent_directory
    echo "Exit status: $?"  # Prints the exit status (non-zero means failure)
    
    ```
    
2. **Using `$@` and `$*`**:
    
    ```bash
    ./script.sh arg1 arg2
    echo "All args as separate: $@"  # Outputs: arg1 arg2
    echo "All args as single string: $*"  # Outputs: arg1 arg2
    
    ```
    
3. **Arithmetic with `$((...))`**:
    
    ```bash
    a=5
    b=10
    echo "Sum: $((a + b))"
    
    ```
    
4. **String Manipulation**:
    
    ```bash
    var="hello world"
    echo "Length: ${#var}"  # Outputs: 11
    echo "Substring: ${var:0:5}"  # Outputs: hello
    echo "Replace: ${var/world/universe}"  # Outputs: hello universe
    
    ```
    

Let me know if you'd like specific examples or deeper dives into any of these!

[Users and groups](Linux%20Foundation%20Certified%20System%20Administrator%20(L%2015501aeaa31980219952c041e272b617/Users%20and%20groups%2016001aeaa319800386b2d9e09803c804.md)