# 🖥️ tmux (Terminal Multiplexer) in Linux

`tmux` is a tool used to **run multiple terminal sessions in a single window**.

---

# 📌 1. Verify tmux Installation

To check if tmux is installed:

rpm -qa | grep tmux

✔ As shown on page 1, it verifies tmux installation :contentReference[oaicite:0]{index=0}  

---

# 📌 2. Start tmux Session

To start tmux:

tmux

✔ Activates a new tmux session (page 1) :contentReference[oaicite:1]{index=1}  

---

# 📌 3. Split Window Horizontally

Shortcut:

Ctrl + B then Shift + %

✔ Splits window into left and right panes (page 1) :contentReference[oaicite:2]{index=2}  

---

# 📌 4. Switch Between Panes

Shortcut:

Ctrl + B then Arrow keys

✔ Move between different panes (page 1) :contentReference[oaicite:3]{index=3}  

---

# 📌 5. Split Window Vertically

Shortcut:

Ctrl + B then "

✔ Splits window into top and bottom panes (page 1) :contentReference[oaicite:4]{index=4}  

---

# 📌 6. Detach tmux Session

Shortcut:

Ctrl + B then D

✔ Detaches session and keeps it running in background (page 2) :contentReference[oaicite:5]{index=5}  

---

# ⚙️ Important Notes

- `tmux` allows multiple sessions in one terminal  
- Useful for remote servers and multitasking  
- Sessions continue running even after disconnect  

---

# 📊 Summary

| Action | Command / Shortcut |
|--------|-------------------|
| Verify tmux | rpm -qa | grep tmux |
| Start session | tmux |
| Split horizontal | Ctrl+B → Shift+% |
| Split vertical | Ctrl+B → " |
| Switch panes | Ctrl+B → Arrow |
| Detach session | Ctrl+B → D |

---

# 🎯 Key Learning

- Improves productivity in terminal  
- Allows multitasking in one window  
- Keeps processes running in background  

---

# 📘 RHCSA Note

tmux is important for:

- Remote server management  
- Multitasking in terminal  
- Session persistence  

It is a **useful tool for RHCSA and real-world Linux administration**.

---