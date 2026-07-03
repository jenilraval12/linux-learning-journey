# Notes 01 — `mkdir` Command

## 📖 Introduction

The `mkdir` (**Make Directory**) command is one of the most commonly used Linux commands. It is used to create one or more directories (folders). Whether you're organizing project files, creating nested folder structures, or setting permissions, `mkdir` is an essential command every Linux user should know.

---

# Syntax

```bash
mkdir [OPTIONS] DIRECTORY_NAME
```

---

# Basic Usage

## 1. Create a Single Directory

Creates a single directory in the current working directory.

### Command

```bash
mkdir Linux
```

### Output

```
Linux/
```

---

## 2. Create Multiple Directories

Create multiple directories at once.

### Command

```bash
mkdir docs images videos
```

### Output

```
docs/
images/
videos/
```

---

## 3. Create Nested Directories (`-p`)

The `-p` option creates parent directories automatically if they don't exist.

### Command

```bash
mkdir -p DevOps/Linux/Commands
```

### Output

```
DevOps/
└── Linux/
    └── Commands/
```

Without `-p`, this command would fail if the parent directories don't already exist.

---

## 4. Create a Directory with Specific Permissions (`-m`)

Use the `-m` option to specify permissions while creating the directory.

### Command

```bash
mkdir -m 755 project
```

### Check Permissions

```bash
ls -ld project
```

### Output

```
drwxr-xr-x
```

### Understanding the Output

```
drwxr-xr-x
```

This output can be broken down as follows:

| Part | Meaning |
|------|---------|
| `d` | Indicates that it is a **directory**. (`-` would indicate a regular file.) |
| `rwx` | Permissions for the **Owner (User)** |
| `r-x` | Permissions for the **Group** |
| `r-x` | Permissions for **Others (Everyone else)** |

So,

```
d | rwx | r-x | r-x
    ↑      ↑      ↑
 Owner   Group  Others
```

### Permission Symbols

| Symbol | Meaning |
|--------|---------|
| `r` | Read |
| `w` | Write |
| `x` | Execute (or enter a directory) |
| `-` | Permission not granted |

### What Each Permission Means

| User Type | Permissions | Description |
|-----------|-------------|-------------|
| **Owner** | `rwx` | Can read, write, and enter the directory. |
| **Group** | `r-x` | Can read and enter the directory, but cannot modify its contents. |
| **Others** | `r-x` | Can read and enter the directory, but cannot modify its contents. |

### Permission Symbols

| Symbol | Meaning |
|--------|---------|
| `r` | Read |
| `w` | Write |
| `x` | Execute (or enter a directory) |
| `-` | Permission not granted |

### Numeric Permission Values

| Number | Binary | Permission |
|--------|--------|------------|
| `7` | `111` | `rwx` (Read, Write, Execute) |
| `6` | `110` | `rw-` (Read, Write) |
| `5` | `101` | `r-x` (Read, Execute) |
| `4` | `100` | `r--` (Read only) |
| `3` | `011` | `-wx` (Write, Execute) |
| `2` | `010` | `-w-` (Write only) |
| `1` | `001` | `--x` (Execute only) |
| `0` | `000` | `---` (No permissions) |

### Common Permission Values

| Permission | Meaning |
|------------|---------|
| `777` | Owner, Group, and Others have full permissions (`rwxrwxrwx`). |
| `755` | Owner has full permissions (`rwx`), Group and Others have Read and Execute (`r-xr-x`). |
| `700` | Only the Owner has full permissions (`rwx------`). |
| `644` | Owner has Read and Write, Group and Others have Read only (`rw-r--r--`). *(Common for files)* |
| `600` | Only the Owner can Read and Write (`rw-------`). *(Common for sensitive files)* |

> **Note:** For directories, the **Execute (`x`) permission** means a user can **enter (cd into)** the directory and access its contents. Without `x`, even if `r` is present, users cannot traverse the directory.

## 5. Display Created Directories (`-v`)

The `-v` (verbose) option displays a message for every directory created.

### Command

```bash
mkdir -v test
```

### Output

```
mkdir: created directory 'test'
```

---

## 6. Combine Multiple Options

Options can be combined.

### Command

```bash
mkdir -pvm 755 project/src/assets
```

This command:

- `-p` → Creates missing parent directories
- `-v` → Displays each directory created
- `-m 755` → Sets permissions

### Output

```
mkdir: created directory 'project'
mkdir: created directory 'project/src'
mkdir: created directory 'project/src/assets'
```

---

# Advanced Examples

## 7. Create Multiple Nested Directories

```bash
mkdir -p backend/{api,database,config}
```

Output

```
backend/
├── api/
├── database/
└── config/
```

> **Note:** `{}` is a shell feature called **Brace Expansion**, not a feature of `mkdir`.

---

## 8. Create Numbered Directories

```bash
mkdir Day{1..5}
```

Output

```
Day1/
Day2/
Day3/
Day4/
Day5/
```

Useful for:

- Daily Notes
- Labs
- Exercises

---

## 9. Create Alphabetical Directories

```bash
mkdir Section{A..E}
```

Output

```
SectionA/
SectionB/
SectionC/
SectionD/
SectionE/
```

---

## 10. Create Directories with Spaces

```bash
mkdir "My Folder"
```

or

```bash
mkdir My\ Folder
```

Output

```
My Folder/
```

---

## 11. Create a Hidden Directory

Hidden directories start with a dot (`.`).

```bash
mkdir .config
```

Output

```
.config/
```

Hidden directories are commonly used to store application configuration files.

---

# Helpful Commands

## Show Help

```bash
mkdir --help
```

Displays all available options and usage information.

---

## Check Installed Version

```bash
mkdir --version
```

Displays the installed GNU Coreutils version.

---

# Common Flags

| Flag | Description |
|------|-------------|
| `-p` | Create parent directories if they don't exist |
| `-m MODE` | Set directory permissions |
| `-v` | Show each created directory |
| `--help` | Display help page |
| `--version` | Show installed version |

---

# Real-World Examples

## Example 1: Create a Project Structure

```bash
mkdir -p MyProject/{src,docs,tests,assets}
```

Output

```
MyProject/
├── assets/
├── docs/
├── src/
└── tests/
```

---

## Example 2: Organize Study Notes

```bash
mkdir -p Linux/{Commands,Shell,Permissions,Scripting}
```

Output

```
Linux/
├── Commands/
├── Permissions/
├── Shell/
└── Scripting/
```

---

## Example 3: Create Semester Folders

```bash
mkdir Semester{1..8}
```

Output

```
Semester1/
Semester2/
Semester3/
Semester4/
Semester5/
Semester6/
Semester7/
Semester8/
```

---

# Common Errors

## Error: Directory Already Exists

```bash
mkdir test
mkdir test
```

Output

```
mkdir: cannot create directory 'test': File exists
```

### Solution

```bash
mkdir -p test
```

The `-p` option prevents this error if the directory already exists.

---

## Error: No Such File or Directory

```bash
mkdir project/src
```

Output

```
mkdir: cannot create directory 'project/src': No such file or directory
```

### Solution

```bash
mkdir -p project/src
```

---

## Error: Permission Denied

```bash
mkdir /root/demo
```

Output

```
mkdir: cannot create directory '/root/demo': Permission denied
```

### Solution

```bash
sudo mkdir /root/demo
```

---

# Exit Status

| Exit Code | Meaning |
|-----------|---------|
| `0` | Command executed successfully |
| Non-zero | An error occurred |

Example:

```bash
mkdir test
echo $?
```

Output

```
0
```

---

# Best Practices

- Use meaningful directory names.
- Use lowercase letters and hyphens (`-`) for better readability.
- Use `-p` when creating nested directories.
- Avoid spaces in directory names unless necessary.
- Verify permissions using `ls -ld`.

---

# Practice Exercises

### Exercise 1

Create the following structure:

```
Cloud/
├── AWS/
├── Azure/
└── GCP/
```

<details>
<summary>Solution</summary>

```bash
mkdir -p Cloud/{AWS,Azure,GCP}
```

</details>

---

### Exercise 2

Create five directories named:

```
Lab1
Lab2
Lab3
Lab4
Lab5
```

<details>
<summary>Solution</summary>

```bash
mkdir Lab{1..5}
```

</details>

---

### Exercise 3

Create the following structure:

```
Portfolio/
├── Projects/
├── Certificates/
└── Resume/
```

<details>
<summary>Solution</summary>

```bash
mkdir -p Portfolio/{Projects,Certificates,Resume}
```

</details>

---

# Cheat Sheet

| Command | Description |
|---------|-------------|
| `mkdir folder` | Create a single directory |
| `mkdir dir1 dir2` | Create multiple directories |
| `mkdir -p a/b/c` | Create nested directories |
| `mkdir -m 755 folder` | Create directory with permissions |
| `mkdir -v folder` | Show created directory |
| `mkdir -pvm 755 project/src` | Combine multiple options |
| `mkdir backend/{api,db}` | Create multiple subdirectories |
| `mkdir Day{1..5}` | Create numbered directories |
| `mkdir Section{A..E}` | Create alphabetical directories |
| `mkdir "My Folder"` | Create a directory with spaces |
| `mkdir .hidden` | Create a hidden directory |
| `mkdir --help` | Show help page |
| `mkdir --version` | Show installed version |

---

# Key Takeaways

- `mkdir` stands for **Make Directory**.
- It creates one or more directories.
- `-p` is the most commonly used option for creating nested directories.
- `-m` sets permissions during creation.
- `-v` provides verbose output.
- Multiple options can be combined (e.g., `-pvm`).
- Brace expansion (`{}`) can quickly create multiple directories.
- Always use meaningful directory names and organize projects into a clear hierarchy.

---

## References

- `man mkdir`
- `mkdir --help`

---

**Repository:** Linux Learning Journey  
**Notes:** 01  
**Command:** `mkdir`
