# 🌍 Environment Variables in Linux

Environment variables are used to **store system and user-specific information** that can be used by programs and processes.

---

# 📌 1. View All Environment Variables

To display all environment variables:

printenv

### Output:
- Shows all variables like `PATH`, `HOME`, `SHELL`, etc.

✔ As shown on page 1, it lists all environment variables :contentReference[oaicite:0]{index=0}  

---

# 📌 2. View a Specific Environment Variable

To display a single variable:

echo $VARIABLE_NAME

### Examples:

echo $SHELL  
echo $PWD  

### Output:
- `$SHELL` → shows default shell  
- `$PWD` → shows current directory  

✔ Page 1 shows examples of viewing specific variables :contentReference[oaicite:1]{index=1}  

---

# 📌 3. Create Environment Variable (Temporary)

To create a variable:

VARIABLE_NAME="value"

### Example:

TEST="123"

To make it available to child processes:

export TEST

### Verify:

echo $TEST  

✔ Page 2 shows creating and exporting variable :contentReference[oaicite:2]{index=2}  

---

# 📌 4. Set Environment Variable Permanently

Edit `.bashrc` file:

vi ~/.bashrc

Add:

TEST="Piyush"  
export TEST  

### Apply changes:

source ~/.bashrc  

### Verify:

echo $TEST  

✔ Page 2 shows permanent variable setup :contentReference[oaicite:3]{index=3}  

---

# ⚙️ Important Notes

- `printenv` → view all variables  
- `echo $VAR` → view specific variable  
- `export` → make variable global  
- `.bashrc` → store permanent variables  

---

# 📊 Summary

| Command | Purpose |
|--------|--------|
| printenv | View all variables |
| echo $VAR | View specific variable |
| export VAR | Make variable global |
| .bashrc | Permanent variable storage |

---

# 🎯 Key Learning

- Environment variables control system behavior  
- Useful for scripting and configuration  
- Can be temporary or permanent  

---

# 📘 RHCSA Note

Environment variables are important for:

- System configuration  
- Shell scripting  
- Application behavior  

It is a **core concept for RHCSA**.

---