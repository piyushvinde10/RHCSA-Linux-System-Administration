# 🧪 Linux Practice Exercise (User, File & System Commands)

This exercise covers **file handling, vi editor, user management, groups, and system commands**.

---

# 📂 1. Directory & File Creation

Go to home directory and create folder:

cd ~  
mkdir superman  
cd superman  

Create file using vi:

vi first4movies  

Add at least:
- 20 lines  
- Each line with 5–6 words  

✔ As shown on page 1 :contentReference[oaicite:0]{index=0}  

---

# ✍️ 2. vi Editor Practice

Perform operations:

- Navigate inside file  
- Delete lines → `dd`  
- Undo changes → `u`  

✔ Page 2 shows delete and undo :contentReference[oaicite:1]{index=1}  

---

# 👥 3. Group & User Creation

Create group:

groupadd superheros  

Create user:

useradd -g superheros -u 2000 hulk  

✔ Page 3 shows group and user creation :contentReference[oaicite:2]{index=2}  

---

# 🔐 4. User Setup

Set password:

passwd hulk  

Login as user:

su - hulk  

✔ Page 4 shows password and login :contentReference[oaicite:3]{index=3}  

---

# 📄 5. File & Permission Task

Create file:

touch Skaar  

Change group ownership:

chown :root Skaar  

✔ Page 4–5 shows file and ownership change :contentReference[oaicite:4]{index=4}  

---

# 🌍 6. Multiple Users & Groups

Create group:

groupadd continents  

Create users:

useradd -g continents namerica  
useradd -g continents samerica  
useradd -g continents asia  
useradd -g continents europe  
useradd -g continents australia  
useradd -g continents africa  
useradd -g continents antartica  

✔ Page 5 shows user creation :contentReference[oaicite:5]{index=5}  

---

# 🔑 7. Password & File Creation

Set password for each user:

passwd username  

Switch user:

su - username  

Create file:

touch filename  

✔ Page 6–7 shows file creation for each user :contentReference[oaicite:6]{index=6}  

---

# ⚙️ 8. Admin Privileges

Add user to wheel group:

usermod -aG wheel namerica  

✔ Page 8 shows adding to sudo group :contentReference[oaicite:7]{index=7}  

---

# 📊 9. System Commands Practice

Check logged users:

last | awk '{print $1}' | sort | uniq  

Check user ID:

id africa  
id australia  

✔ Page 8–9 shows verification commands :contentReference[oaicite:8]{index=8}  

---

# 🕒 10. Date & Time

Set date:

date -s "1998-08-22 13:00:00"  

Check uptime:

uptime  

✔ Page 9 shows date and uptime :contentReference[oaicite:9]{index=9}  

---

# 📅 11. Calendar & System Info

View calendar:

cal 1999  

Check system info:

uname -a  

✔ Page 10 shows calendar and uname :contentReference[oaicite:10]{index=10}  

---

# 💾 12. Disk Info & File Editing

Save disk info:

df -h > systemdiskinfo  

Edit file:

vi systemdiskinfo  

- Remove first 2 lines  
- Save file  

✔ Page 11 shows editing file :contentReference[oaicite:11]{index=11}  

---

# 📜 13. Kernel Logs Practice

Save logs:

dmesg > dm-file  

Edit file:

vi dm-file  

- Remove last 5–7 lines  
- Add text at end:

This is the end of the file.  

✔ Page 12 shows editing logs :contentReference[oaicite:12]{index=12}  

---

# 🔄 14. Reboot System

Reboot using init:

init 6  

✔ Page 13 shows reboot command :contentReference[oaicite:13]{index=13}  

---

# 🎯 Key Learning

- File and directory management  
- vi editor usage  
- User & group management  
- System commands practice  

---

# 📘 RHCSA Note

This exercise covers:

- Real-world Linux tasks  
- Important RHCSA concepts  
- Hands-on practice for exam  

---