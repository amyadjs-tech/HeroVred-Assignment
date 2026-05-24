# Question 2: Interactive Log Script

## Objective

Create a bash script that:

- Takes user input
- Reads configuration from app.conf
- Writes timestamped log entries
- Displays the updated log file

---

# Step 1: Navigate to Scripts Directory

```bash
cd /home/amya/webapp/scripts/
```

---

# Step 2: Create Script Using vim

```bash
vim log_user.sh
```

Press:

```text
i
```

to enter insert mode.

---

# Step 3: Add Script Content

```bash
#!/bin/bash

read -p "Enter your name: " username

cat /home/amya/webapp/config/app.conf

echo "Login: $username Date: $(date)" >> /home/amya/webapp/logs/app.log

cat /home/amya/webapp/logs/app.log
```

---

# Step 4: Save and Exit

Press:

```text
Esc
```

Then type:

```bash
:wq
```

---

# Step 5: Give Execute Permission

```bash
chmod +x /home/amya/webapp/scripts/log_user.sh
```

---

# Step 6: Run the Script

## First Run

```bash
./log_user.sh
```

Input:

```text
Chirag
```

---

## Second Run

```bash
./log_user.sh
```

Input:

```text
Priya
```

---

## Third Run

```bash
./log_user.sh
```

Input:

```text
Ravi
```

---

# Step 7: Verify Log File

```bash
cat /home/amya/webapp/logs/app.log
```

Example Output:

```bash
Login: Chirag Date: Sat May 24 14:30:01 IST 2026
Login: Priya Date: Sat May 24 14:31:12 IST 2026
Login: Ravi Date: Sat May 24 14:32:40 IST 2026
```

---

# Final Script Permission

```bash
ls -l /home/amya/webapp/scripts/log_user.sh
```

Expected:

```bash
-rwxr-xr-x
```

---

# Interview Explanation

> “I created an interactive bash script using read -p to capture user input, displayed configuration values using cat, and appended timestamped entries into a centralized log file using echo >>.”
