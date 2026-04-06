# 🖥️ Changing System Hostname in Linux

Changing the hostname allows you to **identify your system on a network**.

---

# 📌 1. Check Current Hostname

To view current hostname:

hostname

### Output Example:
- workstation

---

# 📌 2. Change Hostname (Temporary & Permanent)

To change hostname using command:

hostnamectl set-hostname newhostname

### Example:
hostnamectl set-hostname workstation02

✔ Changes hostname immediately (as shown in terminal on page 1) :contentReference[oaicite:0]{index=0}  

---

# 📌 3. Verify Hostname File

To check hostname stored in system file:

cat /etc/hostname

### Output:
- Shows current hostname saved in system

---

# 📌 4. Edit Hostname Manually

To change hostname manually:

vi /etc/hostname

### Steps:
- Open file using editor  
- Replace old hostname with new one  
- Save and exit  

### Apply Changes:
reboot

✔ As shown on page 2, system needs reboot for full update :contentReference[oaicite:1]{index=1}  

---

# ⚙️ Important Notes

- Requires **sudo/root access** for changes  
- `hostnamectl` is preferred method  
- Manual edit is alternative method  

---

# 📊 Summary

| Method | Command |
|--------|--------|
| Check hostname | hostname |
| Change hostname | hostnamectl set-hostname newhostname |
| View file | cat /etc/hostname |
| Edit manually | vi /etc/hostname |

---

# 🎯 Key Learning

- Hostname identifies system in network  
- Can be changed using command or file  
- Important for server management  

---

# 📘 RHCSA Note

Hostname configuration is important for:

- Network identification  
- System administration  
- RHCSA exam preparation  

---