# 🖥️ Finding System Information in Linux

System information commands are used to **check OS details, kernel version, and hardware information**.

---

# 📌 1. Check OS Version

To view Red Hat OS version:

cat /etc/redhat-release

### Output Example:
- Red Hat Enterprise Linux release 10.0 (Coughlan)

✔ As shown on page 1, this command displays OS version :contentReference[oaicite:0]{index=0}  

---

# 📌 2. Check Kernel & System Details

To view system and kernel information:

uname -a

### Shows:
- Kernel version  
- System architecture (x86_64)  
- Hostname  
- Build details  

✔ Page 1 shows complete system details using this command :contentReference[oaicite:1]{index=1}  

---

# 📌 3. Check Hardware Information

To view hardware details:

dmidecode

### Shows:
- BIOS information  
- System manufacturer  
- Hardware configuration  
- Memory and processor details  

⚠️ Requires root access:

sudo dmidecode

✔ As shown on page 2, it provides detailed BIOS/system info :contentReference[oaicite:2]{index=2}  

---

# ⚙️ Important Notes

- `cat /etc/redhat-release` → OS version  
- `uname -a` → Kernel & system info  
- `dmidecode` → Hardware details  
- Some commands require **sudo/root privileges**  

---

# 📊 Summary

| Command | Purpose |
|--------|--------|
| cat /etc/redhat-release | OS version |
| uname -a | Kernel & system info |
| dmidecode | Hardware details |

---

# 🎯 Key Learning

- Helps in system troubleshooting  
- Useful for system audits  
- Important for understanding system configuration  

---

# 📘 RHCSA Note

System information commands are important for:

- Troubleshooting  
- System analysis  
- RHCSA exam preparation  

---