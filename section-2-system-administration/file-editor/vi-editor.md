# Linux vi File Editor

The **vi editor** is a powerful text editor available in almost all Linux systems.  
It is commonly used for editing configuration files, scripts, and system files.

The `vi` editor works in different modes such as **Insert Mode** and **Command Mode**.

---

# Opening a File in vi

```
vi filename
```

Example:

```
vi demo.txt
```

---

# Insert Text

The following commands are used to insert text in the `vi` editor.

| Command | Description |
|--------|-------------|
| `i` | Insert text before the cursor |
| `I` | Insert text at the beginning of the line |
| `a` | Insert text after the cursor |
| `A` | Insert text at the end of the line |
| `o` | Open a new line below and insert text |
| `O` | Open a new line above and insert text |

These commands switch the editor to **Insert Mode**. :contentReference[oaicite:0]{index=0}

---

# Deleting Text

The following commands are used to delete text.

| Command | Description |
|--------|-------------|
| `x` | Delete character under the cursor |
| `X` | Delete character before the cursor |
| `dd` | Delete the entire line |
| `dw` | Delete a word |
| `d$` | Delete from cursor to end of line |
| `d0` | Delete from cursor to beginning of line |

These commands work in **Command Mode**. :contentReference[oaicite:1]{index=1}

---

# Replace Text

```
r
```

This command replaces the character under the cursor. :contentReference[oaicite:2]{index=2}

---

# Escape from Insert Mode

```
Esc
```

Press **Esc** to return from Insert Mode to Command Mode. :contentReference[oaicite:3]{index=3}

---

# Save and Exit

| Command | Description |
|--------|-------------|
| `:q!` | Quit without saving |
| `:wq` | Save and quit |

Example:

```
:wq
```

This saves the file and exits the editor. :contentReference[oaicite:4]{index=4}

---

# Summary

The `vi` editor is essential for Linux system administration because it allows administrators to:

- Edit configuration files
- Modify scripts
- Manage system files
- Work directly from the terminal

---

# RHCSA Note

Understanding the **vi editor** is an important skill for **Linux system administration and RHCSA certification preparation**.