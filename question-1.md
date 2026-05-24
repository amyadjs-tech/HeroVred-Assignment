# HeroVred-Assignment
All assignment README files are created here

# DevOps Project Structure Setup

## Objective
Create a complete Linux project directory structure with proper permissions and ownership.

---

# Step 1: Check Current Working Directory

```bash
pwd
````

Current path from your system:

```bash
/home/amya
```

Since you do not have permission to create directories inside `/home/ec2-user/`, create the project inside your own home directory.

---

# Step 2: Create Project Directory Structure

```bash
mkdir -p /home/amya/webapp/{scripts,logs,config}
```

This creates:

* scripts/
* logs/
* config/

inside `/home/amya/webapp/`

---

# Step 3: Create Configuration File

Run:

```bash
cat > /home/amya/webapp/config/app.conf
```

Type the following content:

```bash
APP_NAME=WebApp
PORT=8080
```

Save the file using:

```bash
Ctrl + D
```

The above 1, 2 and 3 steps are shown in below picture

<img width="1917" height="1025" alt="image" src="https://github.com/user-attachments/assets/a489cef4-0170-47b1-9a61-fbb95127f170" />



---

# Step 4: Create Empty Log File

```bash
touch /home/amya/webapp/logs/app.log
```

Verify the file size:

```bash
ls -l /home/amya/webapp/logs/app.log
```

Expected Output:

```bash
-rw-r--r-- 1 amya amya 0 May 24 14:00 app.log
```

`0` means the file is empty.

---

# Step 5: Set Permissions

## Set scripts directory permission

```bash
chmod 755 /home/amya/webapp/scripts
```

## Set configuration file permission

```bash
chmod 644 /home/amya/webapp/config/app.conf
```

---

# Permission Explanation

## 755 Permission

```text
rwxr-xr-x
```

| User   | Permission | Meaning              |
| ------ | ---------- | -------------------- |
| Owner  | rwx        | Read, Write, Execute |
| Group  | r-x        | Read and Execute     |
| Others | r-x        | Read and Execute     |

### Simple Explanation

* Owner has full control.
* Group and others can only view and execute.
* No one except owner can modify files.

---

## 644 Permission

```text
rw-r--r--
```

| User   | Permission | Meaning        |
| ------ | ---------- | -------------- |
| Owner  | rw-        | Read and Write |
| Group  | r--        | Read Only      |
| Others | r--        | Read Only      |

### Simple Explanation

* Owner can read and edit the file.
* Group and others can only read the file.

---

# Step 6: Change Ownership

Run:

```bash
sudo chown -R root:root /home/amya/webapp/
```

Explanation:

* `sudo` → Run command as administrator
* `chown` → Change ownership
* `-R` → Apply recursively
* `root:root` → Owner = root, Group = root

---

# Step 7: Verify Structure

```bash
ls -lR /home/amya/webapp/
```

Expected Output:

```bash
/home/amya/webapp/:
total 0
drwxr-xr-x 2 root root 22 May 24 14:00 config
drwxr-xr-x 2 root root 21 May 24 14:00 logs
drwxr-xr-x 2 root root  6 May 24 14:00 scripts

/home/amya/webapp/config:
total 4
-rw-r--r-- 1 root root 30 May 24 14:00 app.conf

/home/amya/webapp/logs:
total 0
-rw-r--r-- 1 root root 0 May 24 14:00 app.log

/home/amya/webapp/scripts:
total 0
```
The above 4, 5, 6 and 6 steps are shown in below picture

<img width="1917" height="1015" alt="image" src="https://github.com/user-attachments/assets/52d59e61-4bfa-49a3-b67c-1d1720163f5c" />


---

# Final Project Structure

```text
webapp/
├── scripts/
├── logs/
│   └── app.log
└── config/
    └── app.conf
```

---

# Interview Style Explanation

> “I created the required project directory structure using `mkdir -p`. Then I created the configuration and log files using `cat` and `touch`. I applied Linux permissions using `chmod`, where `755` provides full access to the owner and read-execute access to others, while `644` provides read-write access only to the owner and read-only access to others. Finally, I changed ownership recursively using `chown -R` and verified the structure using `ls -lR`.”

```
```

