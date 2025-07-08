# Project: Securing a Directory with Linux File Permissions

### Project Description
This project demonstrates how to secure a directory by setting proper file and directory permissions in Linux. It covers checking existing permissions and then using the `chmod` command to make specific security changes.

---
### 1. Checking Initial File and Directory Details

First, I used `ls -la` to list the contents of the directory, including hidden files and their permissions.

```bash
jehuty-v1@Analyst-Machine:~/Desktop/researcher2/Projects$ ls -la
total 12
drwxr-xr-x 3 root root 4096 Nov 1 14:05 .
drwxr-xr-x 3 root root 4096 Nov 1 00:04 ..
drwx--x--- 2 root root 4096 Nov 1 14:05 drafts
-rw-rw-rw- 1 root root 0 Nov 1 00:05 project_k.txt
-rw-rw-rw- 1 root root 0 Nov 1 00:05 project_m.txt
...
-rw-r--r-- 1 root root 0 Nov 1 00:28 .project_x.txt
```
This command revealed a directory named `drafts`, a hidden file `.project_x.txt`, and four other text files. The 10-character string in the first column represents the permissions for each item.

---

### 2. Understanding the Permissions String
The 10-character permission string is broken down as follows:

* **1st character:** Indicates the type, where `d` is a directory and `-` is a regular file.
* **2nd-4th characters:** Show the owner's permissions for read (`r`), write (`w`), and execute (`x`).
* **5th-7th characters:** Show the group's permissions.
* **8th-10th characters:** Show permissions for all other users.

For example, a permission string of `-rwxr-xr--` means it's a file where the owner has read/write/execute permissions, the group has read/execute permissions, and others can only read the file.

---

### 3. Changing File and Directory Permissions

#### Task 1: Secure a Hidden File
The first task was to modify the permissions for the `.project_x.txt` file by removing write permissions for the owner and group and adding read permission for the group.

**Command Used:**
```bash
sudo chmod u-w,g-w,g+r .project_x.txt
```
#### Task 2: Restrict Directory Access
The final task was to make the `drafts` directory accessible only to the owner. This was achieved by removing the execute permission for the group, which prevents them from entering the directory.

**Command Used:**
```bash
sudo chmod g-x drafts
```

After running this command, the permissions for the `drafts` directory were updated to `drwx------`, confirming that only the owner has access.

---
### Summary
In this project, I used `ls -la` to audit file and directory permissions and then used the `chmod` command to enforce a more secure configuration, demonstrating a key Linux administration skill.
