# Linux vs Windows Commands

Linux and Windows have different command-line tools to perform similar tasks.  
This document shows the equivalent commands used in both operating systems.

---

## 1. List Directory Contents

| Windows | Linux |
|--------|------|
| `dir` | `ls -l` |

Example:

```bash
ls -l
```

Displays detailed information about files and directories.

---

## 2. Rename a File

| Windows | Linux |
|--------|------|
| `ren` | `mv` |

Example:

```bash
mv oldfile.txt newfile.txt
```

---

## 3. Copy a File

| Windows | Linux |
|--------|------|
| `copy` | `cp` |

Example:

```bash
cp file1.txt backup.txt
```

---

## 4. Move a File

| Windows | Linux |
|--------|------|
| `move` | `mv` |

Example:

```bash
mv file1.txt /home/user/Documents
```

---

## 5. Clear the Screen

| Windows | Linux |
|--------|------|
| `cls` | `clear` |

Example:

```bash
clear
```

---

## 6. Delete a File

| Windows | Linux |
|--------|------|
| `del` | `rm` |

Example:

```bash
rm file.txt
```

---

## 7. Compare Files

| Windows | Linux |
|--------|------|
| `fc` | `diff` |

Example:

```bash
diff file1 file2
```

---

## 8. Search Text in File

| Windows | Linux |
|--------|------|
| `find` | `grep` |

Example:

```bash
grep "hello" file1.txt
```

---

## 9. Display Command Help

| Windows | Linux |
|--------|------|
| `command /?` | `man command` |

Example:

```bash
man ls
```

---

## 10. Show Current Directory

| Windows | Linux |
|--------|------|
| `chdir` | `pwd` |

Example:

```bash
pwd
```

---

## 11. Display Time

| Windows | Linux |
|--------|------|
| `time` | `date` |

Example:

```bash
date
```

---

# Summary

Understanding the differences between Linux and Windows commands helps users transition easily between operating systems.

Linux commands are widely used in:

- System administration
- DevOps
- Cloud environments
- Server management

---

# RHCSA Note

Learning Linux command-line tools is an essential skill for the **Red Hat Certified System Administrator (RHCSA)** certification.