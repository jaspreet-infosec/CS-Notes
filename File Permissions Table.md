
In Linux, file and directory permissions are represented both **numerically** and **alphabetically**. The permission system defines who can **read**, **write**, and **execute** a file or directory for three different categories of users:

1. **Owner (User)**: The person who owns the file.
2. **Group**: Users who are part of the file’s group.
3. **Others**: All other users.

#### 1. **Alphabetical Representation (rwx)**

Each file has three types of permissions:

- **r** (read): Allows reading the file (view contents).
- **w** (write): Allows modifying the file (edit contents).
- **x** (execute): Allows executing the file (run it as a program or script).

Each permission is assigned for three user categories:
1. **Owner (User)**.
2. **Group**.
3. **Others**.

For example, if you list a file with `ls -l`, you'll see something like:
```
-rwxr-xr--
```
This string of characters can be broken down as:
- The first character (`-` in this case) indicates the type of file (`-` for regular files, `d` for directories).
- The next three characters represent the **Owner's** permissions: `rwx` (read, write, execute).
- The next three characters represent the **Group's** permissions: `r-x` (read, no write, execute).
- The final three characters represent **Others'** permissions: `r--` (read-only).

#### 2. **Numerical Representation**

Permissions can also be represented by **numbers** using the following values:

| Permission | Number |
|------------|--------|
| No permission | 0 |
| Execute (x)   | 1 |
| Write (w)     | 2 |
| Write & Execute (wx) | 3 |
| Read (r)      | 4 |
| Read & Execute (rx)  | 5 |
| Read & Write (rw)    | 6 |
| Read, Write, & Execute (rwx) | 7 |

Each set of permissions (Owner, Group, Others) is represented by a digit in a **three-digit number**.

#### 3. **Permission Table**

| Permissions | Alphabetic | Numeric | Description               |
| ----------- | ---------- | ------- | ------------------------- |
| ---         | `---`      | 0       | No permissions.           |
| --x         | `--x`      | 1       | Execute only.             |
| -w-         | `-w-`      | 2       | Write only.               |
| -wx         | `-wx`      | 3       | Write and execute.        |
| r--         | `r--`      | 4       | Read only.                |
| r-x         | `r-x`      | 5       | Read and execute.         |
| rw-         | `rw-`      | 6       | Read and write.           |
| rwx         | `rwx`      | 7       | Read, write, and execute. |

#### 4. **Examples of Common Permissions**

1. **`rwxr-xr-x` (755)**:
   - Owner: `rwx` (read, write, execute) → 7
   - Group: `r-x` (read, execute) → 5
   - Others: `r-x` (read, execute) → 5
   - **755** = Owner can read, write, and execute; Group and Others can read and execute.

2. **`rw-r--r--` (644)**:
   - Owner: `rw-` (read, write) → 6
   - Group: `r--` (read-only) → 4
   - Others: `r--` (read-only) → 4
   - **644** = Owner can read and write; Group and Others can read only.

3. **`rwxrwxrwx` (777)**:
   - Owner: `rwx` (read, write, execute) → 7
   - Group: `rwx` (read, write, execute) → 7
   - Others: `rwx` (read, write, execute) → 7
   - **777** = Everyone has full permissions.

4. **`r-xr-xr-x` (555)**:
   - Owner: `r-x` (read, execute) → 5
   - Group: `r-x` (read, execute) → 5
   - Others: `r-x` (read, execute) → 5
   - **555** = Read and execute for all users (no write access).

5. **`rw-rw-r--` (664)**:
   - Owner: `rw-` (read, write) → 6
   - Group: `rw-` (read, write) → 6
   - Others: `r--` (read-only) → 4
   - **664** = Read and write for Owner and Group; read-only for Others.

#### 5. **Changing File Permissions (`chmod`)**

To change file permissions, the `chmod` command is used, followed by either the numeric or alphabetic permission.

1. **Using Numeric Values:**
   ```bash
   chmod 755 filename
   ```
   This sets the permissions of `filename` to `rwxr-xr-x`.

2. **Using Alphabetic Representation:**
   ```bash
   chmod u+rwx,g+rx,o+rx filename
   ```
   This gives the same result as `chmod 755`, but using the `u`, `g`, and `o` options to modify permissions for the **user (u)**, **group (g)**, and **others (o)**.

#### 6. **Special Permissions**

- **Setuid (Set User ID)**: Allows a file to be executed with the permissions of its owner.
  - Represented by an `s` in the owner's execute bit.
  - Example: `chmod 4755 filename`.
- **Setgid (Set Group ID)**: Allows a file to be executed with the permissions of its group.
  - Represented by an `s` in the group’s execute bit.
  - Example: `chmod 2755 filename`.
- **Sticky Bit**: Used on directories to restrict file deletion so that only the file's owner can delete their files.
  - Represented by a `t` in the execute bit of "others".
  - Example: `chmod 1777 /tmp` (common for `/tmp`).

#### 7. **Summary of Symbols**

| Character | Description                           |
|-----------|---------------------------------------|
| `r`       | Read permission                       |
| `w`       | Write permission                      |
| `x`       | Execute permission                    |
| `-`       | No permission                         |
| `s`       | Setuid/setgid bit                     |
| `t`       | Sticky bit                            |

