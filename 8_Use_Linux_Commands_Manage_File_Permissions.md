# **File Permissions in Linux**

## **Project Description**

In this project, I examined and managed file permissions in a Linux environment for the research team of a large organization. The goal was to ensure that only authorized users and groups had the correct access to sensitive research data. Through Linux commands, I reviewed current permissions, removed unnecessary write permissions, and secured both visible and hidden files as well as directories.

---

## **Check File and Directory Details**

To view current file and directory permissions, including hidden files, I used the following command:

```
ls -la /home/researcher2/projects
```

**Explanation:**

* `ls` lists the contents of a directory.
* `-l` shows detailed information, including file permissions.
* `-a` includes hidden files (those that start with a period `.`).

**Example output:**

```
-rw-rw-rw-  1 researcher2 research  5432 Oct 25 09:00 project_k.txt
-rw-r--r--  1 researcher2 research  4321 Oct 25 09:00 project_m.txt
-rw-rw-r--  1 researcher2 research  6521 Oct 25 09:00 project_r.txt
-rw-rw-r--  1 researcher2 research  7142 Oct 25 09:00 project_t.txt
-rw--w----  1 researcher2 research  3220 Oct 25 09:00 .project_x.txt
drwx--x---  2 researcher2 research  4096 Oct 25 09:00 drafts
```

---

## **Describe the Permissions String**

Let’s look at the permissions for `project_k.txt`:

```
-rw-rw-rw-
```

**Explanation of each character:**

| Character | Meaning           | Description                                          |
| --------- | ----------------- | ---------------------------------------------------- |
| `-`       | File type         | A regular file (would be `d` if it were a directory) |
| `rw-`     | User permissions  | The owner can read and write                         |
| `rw-`     | Group permissions | The group can read and write                         |
| `rw-`     | Other permissions | All other users can read and write                   |

**Interpretation:**
This configuration allows everyone to write to the file, which violates the organization’s policy that “others” should not have write permissions.

---

## **Change File Permissions**

To remove write access for “others” on `project_k.txt` while keeping read and write for the user and group, I used this command:

```
chmod o-w /home/researcher2/projects/project_k.txt
```

**Explanation:**

* `chmod` changes file permissions.
* `o-w` removes (`-`) write permission (`w`) from others (`o`).

**Resulting permissions:**

```
-rw-rw-r--
```

This ensures that only the user and group can write to the file, while others can only read it.

---

## **Change File Permissions on a Hidden File**

The hidden file `.project_x.txt` is an archived document. It should only be **readable** by the user and group, and **not writable** by anyone.

To achieve this, I used two commands:

```
chmod u-w /home/researcher2/projects/.project_x.txt
chmod g+r /home/researcher2/projects/.project_x.txt
chmod g-w /home/researcher2/projects/.project_x.txt
chmod o-rwx /home/researcher2/projects/.project_x.txt
```

**Explanation:**

* `u-w` removes write access from the user.
* `g+r` ensures the group can read the file.
* `g-w` removes write access from the group.
* `o-rwx` removes all access (read, write, execute) from others.

**New permissions:**

```
-r--r-----
```

This configuration makes the hidden file readable only by the user and group, with no write or execute permissions.

---

## **Change Directory Permissions**

The `drafts` directory should be accessible only by the `researcher2` user. I restricted access for the group and others using the following commands:

```
chmod g-rwx /home/researcher2/projects/drafts
chmod o-rwx /home/researcher2/projects/drafts
```

**Explanation:**

* `g-rwx` removes all (read, write, execute) permissions from the group.
* `o-rwx` removes all permissions from others.

**Resulting permissions:**

```
drwx------
```

This ensures that only the `researcher2` user can access, modify, or execute within the `drafts` directory.

---

## **Summary**

In this project, I verified and modified file permissions to align with organizational security standards. I used `ls -la` to inspect permissions and `chmod` with symbolic options (`u`, `g`, `o`) to adjust them. I removed unauthorized write permissions, secured hidden files, and restricted directory access to the file owner. These actions strengthened access control, protecting the research team’s files from accidental or malicious modification.

---
