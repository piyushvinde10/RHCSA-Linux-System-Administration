# cut Command (Linux)

The `cut` command is used to extract specific parts of each line from a file.  
It works with **characters, bytes, or fields** and is commonly used for **text processing in Linux**.

---

## Syntax

```
cut OPTION [FILE]
```

### Common Options

- `-c` → Select specific characters
- `-b` → Select bytes
- `-d` → Specify delimiter
- `-f` → Select fields

---

## 1. Running cut Without Options

```
cut file1
```

This command will not work because the `cut` command requires options such as `-c`, `-b`, or `-f`.

---

## 2. Check cut Version

```
cut --version
```

Displays the installed version of the `cut` command.

---

## 3. Extract First Character

```
cut -c1 file1
```

Displays the **first character of each line**.

Example:

Input file (`file1`)

```
Arun
Vivek
Amit
```

Output

```
A
V
A
```

---

## 4. Extract Specific Characters

```
cut -c1,2,4 file1
```

Displays **character positions 1, 2, and 4** from each line.

Example:

Input

```
Arun
Vivek
```

Output

```
Arn
Vve
```

---

## 5. Extract Range of Characters

```
cut -c1-3 file1
```

Displays characters **from position 1 to 3**.

Example

Input

```
Arjun
Rohit
```

Output

```
Arj
Roh
```

---

## 6. Extract by Byte Position

```
cut -b1-3 file1
```

Displays the first **3 bytes** of each line.

---

## 7. Extract Fields Using Delimiter

```
cut -d ":" -f6 /etc/passwd
```

Explanation:

- `-d ":"` → Colon is used as the delimiter  
- `-f6` → Selects the **6th field**

This command displays the **home directory of users** from `/etc/passwd`.

Example output

```
/root
/bin
/var/spool/lpd
```

---

## 8. Extract Multiple Fields

```
cut -d ":" -f6-7 /etc/passwd
```

Displays **field 6 and field 7** from `/etc/passwd`.

Example output

```
/root:/bin/bash
/bin:/usr/sbin/nologin
```

---

## 9. Using cut with Pipe

```
ls -l | cut -c2-4
```

This command extracts **user permission bits** from the output of `ls -l`.

Example output

```
rw-
rw-
r--
```

---

## Summary

The `cut` command is useful for:

- Extracting characters from text
- Extracting fields from structured files
- Processing system files like `/etc/passwd`
- Filtering command output using pipes

It is commonly used with commands such as:

- `grep`
- `awk`
- `sed`
- `sort`