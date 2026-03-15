# Lab: Create a Text Filtering and Search Workflow

This lab demonstrates how to create a workflow in Linux for **filtering and searching text using command-line tools**.

Commands used in this lab include:

- mkdir
- echo
- cp
- ls
- cat
- tail
- head
- less
- grep
- egrep
- cut
- wc

This workflow helps understand how Linux tools can be combined to process and analyze text efficiently. :contentReference[oaicite:0]{index=0}

---

# Task 1: Set Up Files to Process

Create a directory and files for testing.

## Create a directory

```bash
mkdir text_lab
cd text_lab
```

## Add text to a file

```bash
echo "Piyush Vinde" > text.txt
echo "Rohan Gupta" >> text.txt
```

## Create a duplicate file

```bash
cp text.txt text2.txt
```

## List files

```bash
ls
```

---

# Task 2: View File Contents

Different commands can be used to read and navigate through files.

## Show entire file

```bash
cat myfile.csv
```

## View the last lines of a file

```bash
tail myfile.csv
```

## View the beginning of a file

```bash
head myfile.csv
```

## Scroll through the file

```bash
less myfile.csv
```

These commands help analyze large text files efficiently.

---

# Task 3: Filter and Extract Text

Linux commands can filter specific data from text files.

## Search for a word

```bash
grep -i gupta myfile.csv
```

This command searches for the word **gupta** in the file.

---

## Search multiple patterns

```bash
egrep -i "gupta|sharma" myfile.csv
```

This command searches for multiple patterns in a file.

---

## Extract specific fields

```bash
cut -d "," -f2 myfile.csv
```

Explanation:

- `-d ","` specifies the delimiter
- `-f2` selects the second field

---

# Task 4: Create a Workflow

Linux commands can be combined using pipes (`|`) to create powerful workflows.

Example:

```bash
cat myfile.csv | grep -i sharma | wc -l
```

Explanation:

| Command | Purpose |
|--------|--------|
| cat | Display file contents |
| grep | Search for a word |
| wc -l | Count matching lines |

Output shows the number of lines containing the word **sharma**.

---

# Summary

This lab demonstrates how to combine multiple Linux commands to create a **text filtering and search workflow**.

Key concepts:

- Creating test files
- Viewing file contents
- Filtering data using grep
- Extracting fields with cut
- Combining commands using pipes

---

# RHCSA Note

Understanding text filtering and command pipelines is an important skill for **Linux system administrators and RHCSA certification preparation**.