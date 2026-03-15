# Exercise: Linux Command Practice

This exercise focuses on practicing common Linux commands such as file manipulation, permissions, ownership, and text processing.

The tasks include working with directories, managing files, modifying permissions, and processing text using command-line utilities. :contentReference[oaicite:0]{index=0}

---

# Task 1: Practice Linux Command Syntax

Understand the structure of a Linux command:

```
command [options] [arguments]
```

Example:

```bash
ls -l
```

---

# Task 2: List Files by Last Modified Time

List files in the home directory sorted by modification time.

```bash
ls -lt ~
```

---

# Task 3: Move Files into Directories

Create a directory and move files into it.

```bash
mkdir seinfeld
touch jerry george kramer puddy
mv jerry george kramer puddy seinfeld/
```

---

# Task 4: Create Additional Directories

Create directories and move files into them.

### Simpsons

```bash
mkdir simpsons
touch homer bart marge lisa
mv homer bart marge lisa simpsons/
```

### Superman

```bash
mkdir superman
touch clark luther lois
mv clark luther lois superman/
```

---

# Task 5: List Directory Contents by Modification Time

```bash
ls -lt seinfeld/
```

---

# Task 6: Create New Files

Create two new files in the `seinfeld` directory.

```bash
cd seinfeld
touch elaine newman
```

---

# Task 7: Change File Permissions

Remove read permission from everyone for the file `elaine`.

```bash
chmod a-r elaine
```

Add write permission for the group in `newman`.

```bash
chmod g+w newman
```

---

# Task 8: Become Root User

Switch to root user.

```bash
sudo -i
```

Create files in the superman directory.

```bash
cd /home/$USER/superman
touch superman zad
```

---

# Task 9: Change File Ownership

Change ownership of file `zad`.

```bash
chown $USER zad
```

Change group ownership.

```bash
chgrp $USER zad
```

---

# Task 10: Move and Remove Files

Move file to `/tmp`.

```bash
mv superman /tmp/
```

Remove the file.

```bash
rm /tmp/superman
```

---

# Task 11: Add Content to File

Add text to `zad`.

```bash
echo "zad is a bad character in superman movie" >> zad
```

View file contents:

```bash
cat zad
```

---

# Task 12: Create Seinfeld Character File

Create a file and add character names.

```bash
cd ~/seinfeld
touch seinfeld
```

Add text:

```
Jerry Seinfeld
George Costanza
Elaine Benes
Cosmo Kramer
David Puddy
```

---

# Task 13: Work with System Logs

Become root and copy system log output.

```bash
sudo cat /var/log/messages > ~/mesg-new
```

Read file using different commands:

```bash
cat mesg-new
more mesg-new
less mesg-new
```

---

# Task 14: Extract Specific Lines

View first 10 lines.

```bash
head -10 mesg-new > mesg-h10
```

View last 20 lines.

```bash
tail -20 mesg-new > mesg-t20
```

---

# Task 15: Text Processing

Create file containing Seinfeld characters.

```bash
touch seinfeld-characters
```

Add characters using echo.

---

# Task 16: Use Text Processing Commands

Cut first 4 characters from each line.

```bash
cut -c1-4 seinfeld-characters > filter-file
```

Extract second column using awk.

```bash
awk '{print $2}' seinfeld-characters >> filter-file
```

Search for specific text using grep.

```bash
grep "Seinfeld" seinfeld-characters > seinfeld-family
```

---

# Task 17: Practice Sorting and Counting

Use sorting and counting commands.

```bash
sort seinfeld-characters | uniq
```

Count lines.

```bash
wc -l seinfeld-characters
```

---

# Summary

This exercise helps practice key Linux administration tasks:

- File and directory management
- File permissions
- Ownership changes
- Log file processing
- Text processing with `cut`, `awk`, `grep`
- Sorting and counting data

---

# RHCSA Note

Mastering these commands is essential for **Linux system administration and RHCSA certification preparation**.