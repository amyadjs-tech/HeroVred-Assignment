# Question 3: User Management and Permission Control

## Objective

Create Linux users and groups to control access to the log_user.sh script using ownership and file permissions.

---

# Step 1: Create writers Group

```bash
sudo groupadd writers
```

---

# Step 2: Create Users

```bash
sudo useradd -m devuser1
sudo useradd -m devuser2
sudo useradd -m devuser3
sudo useradd -m devuser4
```

---

# Step 3: Add Users to writers Group

```bash
sudo usermod -aG writers devuser1
sudo usermod -aG writers devuser2
```

Verify:

```bash
groups devuser1
groups devuser2
```

Expected:

```bash
devuser1 : devuser1 writers
devuser2 : devuser2 writers
```

---

# Step 4: Change Group Ownership

```bash
sudo chown root:writers /home/amya/webapp/scripts/log_user.sh
```

---

# Step 5: Set Permissions

```bash
sudo chmod 664 /home/amya/webapp/scripts/log_user.sh
```

---

# Step 6: Verify Permissions

```bash
ls -l /home/amya/webapp/scripts/log_user.sh
```

Expected Output:

```bash
-rw-rw-r-- 1 root writers 220 May 24 14:40 log_user.sh
```

---

# Permission Breakdown

```text
664 = rw-rw-r--
```

| User Type | Permission | Meaning |
|------------|-------------|----------|
| Owner | rw- | Read + Write |
| Group | rw- | Read + Write |
| Others | r-- | Read Only |

---

# Step 7: Test Write Access

Switch to devuser1:

```bash
su - devuser1
```

Append data:

```bash
echo "test by devuser1" >> /home/amya/webapp/scripts/log_user.sh
```

This should work successfully.

---

# Step 8: Test Read-Only Access

Switch to devuser3:

```bash
su - devuser3
```

Read file:

```bash
cat /home/amya/webapp/scripts/log_user.sh
```

Try writing:

```bash
echo "test" >> /home/amya/webapp/scripts/log_user.sh
```

Expected:

```bash
Permission denied
```

---

# Final Permission Layout

```bash
-rw-rw-r--  root writers log_user.sh
```

---

# Interview Explanation

> “I implemented Linux user and group-based permission control using group ownership and chmod 664. Two users were granted write access through the writers group, while the remaining users had read-only access.”
