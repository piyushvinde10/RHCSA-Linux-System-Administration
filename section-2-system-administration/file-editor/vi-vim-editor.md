# vi and vim Editor (Linux)

The `vi` and `vim` editors are powerful text editors used in Linux systems for editing files directly from the terminal.

- `vi` → Basic text editor
- `vim` → Advanced version of `vi` (Vi Improved)

---

# What is vi?

The `vi` editor is a standard text editor available in almost all Linux systems.

It works in different modes:

- Command Mode
- Insert Mode

---

# What is vim?

`vim` (Vi Improved) is an enhanced version of `vi` with additional features such as:

- Syntax highlighting
- Undo/Redo support
- Better navigation
- Plugins and customization

---

# Open File

```
vi filename
```

or

```
vim filename
```

Example:

```
vi demo.txt
```

---

# Modes in vi/vim

## 1. Command Mode

Default mode when opening a file.

Used for:

- Navigation
- Deleting text
- Copying and pasting

---

## 2. Insert Mode

Used for writing text.

Enter insert mode using:

- `i` → Insert before cursor  
- `I` → Insert at beginning of line  
- `a` → Insert after cursor  
- `A` → Insert at end of line  
- `o` → New line below  
- `O` → New line above  

Press `Esc` to return to command mode. :contentReference[oaicite:0]{index=0}

---

# Delete Commands

| Command | Description |
|--------|-------------|
| `x` | Delete character under cursor |
| `X` | Delete character before cursor |
| `dd` | Delete entire line |
| `dw` | Delete a word |
| `d$` | Delete to end of line |
| `d0` | Delete to beginning of line |

---

# Replace Command

```
r
```

Replace character under the cursor.

---

# Save and Exit

| Command | Description |
|--------|-------------|
| `:w` | Save file |
| `:q` | Quit |
| `:wq` | Save and quit |
| `:q!` | Quit without saving |

---

# Difference Between vi and vim

| Feature | vi | vim |
|--------|----|-----|
| Full form | Visual Editor | Vi Improved |
| Features | Basic | Advanced |
| Syntax Highlighting | ❌ No | ✅ Yes |
| Undo/Redo | Limited | Advanced |
| User Friendly | Less | More |
| Plugins Support | ❌ No | ✅ Yes |

---

# Summary

- `vi` is a basic text editor
- `vim` is an advanced and improved version
- Both are essential for Linux system administration
- Used to edit configuration files and scripts

---

# RHCSA Note

Learning `vi`/`vim` is very important for:

- Editing system configuration files
- Writing scripts
- Working in terminal-only environments

It is a must-know skill for **RHCSA certification**.