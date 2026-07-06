# Day 04 — `pwd` Command

## 📖 Introduction

The `pwd` (**Print Working Directory**) command is used to display the **absolute path** of the current working directory. It is one of the first commands every Linux user learns because it helps you know exactly where you are in the filesystem.

Whenever you're unsure of your current location in the terminal, simply use `pwd`.

---

# Syntax

```bash
pwd [OPTION]
```

---

# Basic Usage

## 1. Display the Current Working Directory

Shows the complete (absolute) path of your current directory.

### Command

```bash
pwd
```

### Example

Current directory:

```
/home/jenil/Linux
```

Command:

```bash
pwd
```

Output:

```
/home/jenil/Linux
```

---

# Understanding the Output

Suppose the output is:

```text
/home/jenil/Documents/Linux
```

It can be broken down as follows:

| Part | Meaning |
|------|---------|
| `/` | Root directory (starting point of the Linux filesystem) |
| `home` | Home directory containing user accounts |
| `jenil` | Username |
| `Documents` | Folder inside the user's home directory |
| `Linux` | Current working directory |

This means you are currently inside the **Linux** directory.

---

# Absolute Path vs Relative Path

## Absolute Path

An absolute path always starts from the root directory (`/`).

Example:

```bash
/home/jenil/Documents/Linux
```

No matter where you are in the filesystem, this path always points to the same location.

---

## Relative Path

A relative path starts from your current directory.

Suppose your current directory is:

```text
/home/jenil/Documents
```

Then:

```bash
cd Linux
```

works because `Linux` is inside the current directory.

---

# Common Options

## 2. Physical Directory (`-P`)

Displays the physical directory by resolving symbolic links.

### Command

```bash
pwd -P
```

### Example

Suppose:

```
shortcut -> /home/jenil/Documents
```

If you're inside `shortcut`:

```bash
pwd
```

Output:

```
/home/jenil/shortcut
```

Using:

```bash
pwd -P
```

Output:

```
/home/jenil/Documents
```

---

## 3. Logical Directory (`-L`)

Displays the logical path (default behavior).

```bash
pwd -L
```

If you're using symbolic links, it displays the path you navigated through instead of resolving it.

> `pwd` without any options behaves the same as `pwd -L` on most Linux systems.

---

# Helpful Commands

## Show Help

```bash
pwd --help
```

Displays usage information and available options.

---

## Show Version

```bash
pwd --version
```

Displays the installed GNU Coreutils version.

---

# Common Flags

| Flag | Description |
|------|-------------|
| `-L` | Show logical working directory (default) |
| `-P` | Show physical directory by resolving symbolic links |
| `--help` | Display help information |
| `--version` | Display installed version |

---

# Real-World Examples

## Example 1: Check Your Current Location

```bash
pwd
```

Output

```
/home/jenil
```

---

## Example 2: Before Creating a Project

```bash
pwd
mkdir Linux-Notes
```

Verifying your location first helps ensure the directory is created in the correct place.

---

## Example 3: While Navigating

```bash
cd Documents
pwd
```

Output

```
/home/jenil/Documents
```

---

## Example 4: After Changing Directories

```bash
cd Downloads
pwd
```

Output

```
/home/jenil/Downloads
```

---

## Example 5: Verify Before Deleting Files

```bash
pwd
rm notes.txt
```

Checking your location helps avoid deleting files from the wrong directory.

---

# Common Errors

Unlike many Linux commands, `pwd` rarely produces errors.

## Example

If the current directory has been deleted unexpectedly, some shells may display:

```
pwd: error retrieving current directory
```

This is uncommon during normal usage.

---

# Exit Status

| Exit Code | Meaning |
|-----------|---------|
| `0` | Command executed successfully |
| Non-zero | An error occurred |

Example

```bash
pwd
echo $?
```

Output

```
0
```

---

# Difference Between `pwd` and `cd`

| Command | Purpose |
|---------|---------|
| `pwd` | Displays your current location |
| `cd` | Changes your current directory |

Example:

```bash
pwd
```

Output:

```
/home/jenil
```

Now change directory:

```bash
cd Documents
pwd
```

Output:

```
/home/jenil/Documents
```

---

# Best Practices

- Use `pwd` whenever you're unsure of your current location.
- Check your current directory before creating, moving, or deleting files.
- Learn the difference between absolute and relative paths.
- Use `pwd -P` when working with symbolic links.

---

# Practice Exercises

## Exercise 1

Display your current working directory.

<details>
<summary>Solution</summary>

```bash
pwd
```

</details>

---

## Exercise 2

Navigate to your `Documents` directory and verify your location.

<details>
<summary>Solution</summary>

```bash
cd Documents
pwd
```

</details>

---

## Exercise 3

Create a folder named `Linux`, enter it, and verify your location.

<details>
<summary>Solution</summary>

```bash
mkdir Linux
cd Linux
pwd
```

</details>

---

## Exercise 4

Navigate back to your home directory and display its path.

<details>
<summary>Solution</summary>

```bash
cd
pwd
```

</details>

---

# Cheat Sheet

| Command | Description |
|---------|-------------|
| `pwd` | Display current working directory |
| `pwd -L` | Show logical path (default) |
| `pwd -P` | Show physical path |
| `pwd --help` | Show help page |
| `pwd --version` | Show installed version |

---

# Key Takeaways

- `pwd` stands for **Print Working Directory**.
- It displays the **absolute path** of your current location.
- It is useful before creating, moving, copying, or deleting files.
- `pwd -L` shows the logical path.
- `pwd -P` resolves symbolic links and shows the physical path.
- `pwd` is one of the most frequently used Linux commands.

---

## References

- GNU Coreutils Documentation: https://www.gnu.org/software/coreutils/manual/html_node/pwd-invocation.html
- `man pwd`
- `pwd --help`

---

**Repository:** Linux Learning Journey  
**Day:** 04  
**Command:** `pwd`
