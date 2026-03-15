# awk Command (Linux)

The `awk` command is a powerful text processing tool used for **pattern scanning and processing data** in Linux.  
It is commonly used to **extract fields, search patterns, and modify text output**.

---

## Syntax

```
awk 'pattern {action}' file
```

---

## 1. Check awk Version

```
awk --version
```

This command displays the installed version of `awk`. :contentReference[oaicite:0]{index=0}

---

## 2. Print First Field of a File

```
awk '{print $1}' file1
```

This command prints the **first field (column)** from each line of `file1`. :contentReference[oaicite:1]{index=1}

Example:

Input

```
Arav Sharma
Vivaan Patel
Aditya Singh
```

Output

```
Arav
Vivaan
Aditya
```

---

## 3. Print Multiple Fields

```
ls -l | awk '{print $1,$2}'
```

This command prints the **first and second fields** from the output of `ls -l`. :contentReference[oaicite:2]{index=2}

---

## 4. Print Last Field

```
ls -l | awk '{print $NF}'
```

`NF` represents the **last field** of a line. :contentReference[oaicite:3]{index=3}

---

## 5. Search for a Specific Word

```
awk '/Arjun/ {print}' file1
```

This command searches for the word **"Arjun"** and prints the matching lines. :contentReference[oaicite:4]{index=4}

---

## 6. Use Custom Delimiter

```
awk -F ":" '{print $1}' /etc/passwd
```

Explanation:

- `-F ":"` sets the delimiter to **colon**
- `$1` prints the **first field**

This command displays the **username list from `/etc/passwd`**. :contentReference[oaicite:5]{index=5}

---

## 7. Replace a Word in Text

```
echo "hello Tom" | awk '{$2="Imran"; print $0}'
```

Output

```
hello Imran
```

This command replaces the **second word** in the sentence. :contentReference[oaicite:6]{index=6}

---

## 8. Replace Word from File

```
cat file1 | awk '{$2="Imran"; print $0}'
```

This replaces the **second field in each line** of `file1`. :contentReference[oaicite:7]{index=7}

---

## 9. Print Lines with Length Greater Than 10

```
awk 'length($0)>10' file1
```

This command prints lines whose **length is greater than 10 characters**. :contentReference[oaicite:8]{index=8}

---

## 10. Count Number of Fields

```
ls -l | awk '{print NF}'
```

`NF` shows the **number of fields in each line**. :contentReference[oaicite:9]{index=9}

---

## Summary

The `awk` command is useful for:

- Extracting columns from text
- Searching patterns in files
- Processing structured data
- Modifying command output

It is commonly used with commands such as:

- `grep`
- `cut`
- `sed`
- `sort`

---

## RHCSA Note

The `awk` command is an important tool for **text processing and system administration tasks** in Linux and is frequently used in scripts and log analysis.