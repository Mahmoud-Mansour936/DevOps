# Explain

## 🔐 What are File Permissions?

In Ubuntu (and most Linux systems), **every file and folder** has a set of **permissions** that control:

- **Who can read, write, or execute it**
- For **3 types of users**:
    1. **Owner** (user who owns the file)
    2. **Group** (users in the same group)
    3. **Others** (everyone else)

---

## 🔸 1. Symbolic Notation (e.g., `rwxr-xr--`)

This is the **human-readable** format. It shows **10 characters**, where:

- **1st character** = type:
    - - → regular file
    - `d` → directory
    - `l` → symbolic link
- **Next 9 characters** = permissions:
    - Split into 3 groups of 3:
        
        **[owner] [group] [others]**
        
    - Each group has:
        - `r` = read ( list , copy )
        - `w` = write ( delete , rename )
        - `x` = execute (execute , cd to dir. )
        

## 🔸 2. Octal Notation (e.g., `754`)

This is the **numeric format**. Each digit (0–7) represents permissions for **owner**, **group**, and **others**.

### Each permission has a value:

| Permission | Value |
| --- | --- |
| `r` | 4 |
| `w` | 2 |
| `x` | 1 |
| `-` | 0 |