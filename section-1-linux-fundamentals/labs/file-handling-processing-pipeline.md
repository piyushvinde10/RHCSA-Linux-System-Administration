# Lab 2: Develop a File Handling and Processing Pipeline

This lab demonstrates how to build a **file handling and data processing pipeline in Linux** using common command-line tools.

Commands used in this lab include:

- mkdir
- cp
- mv
- cat
- grep
- sort
- uniq

These commands help automate file processing tasks and build efficient workflows. :contentReference[oaicite:0]{index=0}

---

# Task 1: Create Workspace and Seed Data

First, create a working directory and sample files.

## Create workspace

```bash
mkdir pipeline_lab
cd pipeline_lab
mkdir raw
cd raw
```

## Create sample files

```bash
echo "Piyush Vinde" > data1.txt
echo "Ramesh Vinde" > data2.txt
```

Check files:

```bash
ls
```

---

# Task 2: Manage and Organize Files

Combine and organize your input files.

## Combine files

```bash
cat data1.txt data2.txt > merged.txt
```

View merged file:

```bash
cat merged.txt
```

---

## Create a backup

```bash
cp merged.txt merged_backup.txt
```

Rename backup file:

```bash
mv merged_backup.txt backup_merged.txt
```

---

## Rename a file

```bash
mv data2.txt data_2.txt
```

Check the updated files:

```bash
ls
```

---

# Task 3: Review System Logs

Extract and filter useful information from files.

## Extract lines containing a word

```bash
grep -i apple merged.txt > apple.txt
```

This saves all lines containing the word **apple**.

---

## Extract only fruit names

```bash
grep "[A-Za-z]" merged.txt > items.txt
```

Display results:

```bash
cat items.txt
```

---

## Sort and count unique values

```bash
sort items.txt | uniq -c > item_counts.txt
```

View result:

```bash
cat item_counts.txt
```

---

# Task 4: Build End-to-End Processing Pipeline

Combine multiple commands into one pipeline.

Example pipeline:

```bash
grep "[A-Za-z]" merged.txt | sort | uniq -c | sort -nr > summary.txt
```

Explanation:

| Command | Purpose |
|--------|--------|
| grep | Filter valid rows |
| sort | Sort the data |
| uniq -c | Count occurrences |
| sort -nr | Sort results in descending order |
| > | Save output to a file |

View summary:

```bash
cat summary.txt
```

---

# Summary

This lab demonstrates how to create a **complete file handling and processing pipeline** in Linux.

Key concepts:

- Creating and organizing files
- Combining and renaming files
- Extracting data using grep
- Sorting and counting values
- Building pipelines using multiple commands

---

# RHCSA Note

Understanding pipelines and file processing is essential for **Linux system administration and RHCSA certification preparation**.