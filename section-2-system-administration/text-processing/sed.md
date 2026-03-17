# sed Command (Linux)

The `sed` command (Stream Editor) is used to **process and modify text in files**.

It is commonly used for:

- Replacing text
- Deleting lines
- Filtering content
- Editing files without opening them

---

## Syntax

```
sed [options] 'command' file
```

---

# 1. Replace String in a File

```
sed 's/old/new/g' file
```

Example:

```
sed 's/Gupta/Vinde/g' demo.txt
```

This replaces all occurrences of **Gupta → Vinde**.

---

## Replace and Save Changes

```
sed -i 's/Gupta/Vinde/g' demo.txt
```

- `-i` → Edit file directly (in-place)

---

# 2. Delete a Line

```
sed '/pattern/d' file
```

Example:

```
sed '/Vinde/d' demo.txt
```

Deletes lines containing **Vinde**.

---

# 3. Remove Empty Lines

```
sed '/^$/d' file
```

Removes all blank lines from the file.

---

# 4. Delete Specific Lines

## Delete first line

```
sed '1d' file
```

## Delete first N lines

```
sed '1,3d' file
```

Deletes lines 1 to 3.

---

# 5. Replace Tabs with Spaces

```
sed 's/\t/ /g' file
```

Replaces tabs with spaces.

---

# 6. Print Specific Lines

## Print specific line

```
sed -n '3p' file
```

## Print range of lines

```
sed -n '1,3p' file
```

## Print last line

```
sed -n '$p' file
```

---

# 7. Multiple Commands

```
sed -n -e '1p' -e '3p' file
```

Prints line 1 and line 3.

---

# 8. Substitute Inside vi Editor

Inside `vi/vim`, you can use:

```
:%s/old/new/g
```

Example:

```
:%s/joshi/vinde/g
```

Replaces all occurrences in the file.

---

# Summary

The `sed` command is useful for:

- Editing files without opening them
- Automating text changes
- Cleaning data
- Filtering logs

---

# RHCSA Note

The `sed` command is an important tool for:

- Log file processing
- Configuration file editing
- Automation in shell scripts

It is widely used in **Linux system administration and RHCSA preparation**. :contentReference[oaicite:0]{index=0}