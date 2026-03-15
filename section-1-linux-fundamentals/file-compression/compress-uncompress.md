# Compress and Uncompress Files in Linux

Linux provides several commands to compress and extract files.  
These commands help reduce file size and make file transfer easier.

Common compression tools:

- `tar`
- `gzip`
- `zip`
- `unzip`

---

# 1. tar Command

The `tar` command is used to **archive multiple files into a single file**.

### Create a tar archive

```
tar -cvf files.tar file1 file2
```

Explanation:

| Option | Meaning |
|------|------|
| `-c` | Create archive |
| `-v` | Show progress |
| `-f` | Specify archive file name |

Example:

```
tar -cvf files.tar file1 file2
```

This creates an archive called:

```
files.tar
```

---

# 2. Extract Files Using tar

```
tar -xvf files.tar
```

Explanation:

| Option | Meaning |
|------|------|
| `-x` | Extract files |
| `-v` | Show progress |
| `-f` | Archive file name |

This extracts all files from `files.tar`.

---

# 3. gzip Command

The `gzip` command compresses a file.

```
gzip file1
```

After compression:

```
file1.gz
```

---

# 4. Decompress gzip File

```
gzip -d file1.gz
```

This command restores the original file:

```
file1
```

---

# 5. zip Command

The `zip` command compresses files into a `.zip` archive.

```
zip zipfolder.zip file1 file2
```

Example:

```
zip zipfolder.zip file1 file2
```

This creates:

```
zipfolder.zip
```

---

# 6. unzip Command

The `unzip` command extracts files from a zip archive.

```
unzip zipfolder.zip
```

This extracts all files from the archive.

---

# Summary

| Command | Purpose |
|------|------|
| `tar` | Create archive |
| `tar -xvf` | Extract archive |
| `gzip` | Compress file |
| `gzip -d` | Decompress file |
| `zip` | Create zip archive |
| `unzip` | Extract zip archive |

---

# RHCSA Note

Compression commands are useful for:

- Reducing file size
- Transferring files
- Archiving system data
- Creating backups