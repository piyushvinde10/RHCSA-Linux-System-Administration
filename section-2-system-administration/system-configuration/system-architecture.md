# 🖥️ System Architecture and SOS Report in Linux

These commands are used to **check system architecture and generate diagnostic reports**.

---

# 📌 1. Check System Architecture

To view system architecture:

arch

### Output Example:
- x86_64

✔ As shown on page 1, it displays system architecture :contentReference[oaicite:0]{index=0}  

---

# 📌 2. Generate SOS Report

To generate system report:

sudo sos report

### What it does:
- Collects system configuration  
- Gathers diagnostic information  
- Useful for troubleshooting  

✔ Page 1 shows command usage and description :contentReference[oaicite:1]{index=1}  

---

# 📌 3. SOS Report Output

After running command:

- Report is generated in:

/var/tmp/

- Example file:

sosreport-workstation03-xxxx.tar.xz

✔ As shown on page 2, report file is created with details :contentReference[oaicite:2]{index=2}  

---

# 📌 4. Verify Report

To verify report file:

ls /var/tmp

✔ Page 3 shows generated SOS report file in directory :contentReference[oaicite:3]{index=3}  

---

# ⚙️ Important Notes

- `arch` → shows system architecture  
- `sos report` → generates diagnostic report  
- Requires **sudo/root access**  
- Used for troubleshooting and support  

---

# 📊 Summary

| Command | Purpose |
|--------|--------|
| arch | System architecture |
| sos report | Generate diagnostic report |
| ls /var/tmp | Verify report file |

---

# 🎯 Key Learning

- Helps identify system architecture  
- Useful for debugging and support  
- Important for system analysis  

---

# 📘 RHCSA Note

These commands are important for:

- Troubleshooting  
- System diagnostics  
- RHCSA exam preparation  

---