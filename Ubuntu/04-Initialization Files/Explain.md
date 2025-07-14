# Explain

## ⚙️ What Are Initialization Files

Initialization (or **startup**) files are scripts that run **automatically** when:

- A user logs in
- A shell session starts
- A desktop environment loads

## 🌍 1. Global Initialization Files (System-wide)

These affect **all users** on the system. Managed by the **system admin** and stored in directories like `/etc`.

| File | Purpose | When It's Used |
| --- | --- | --- |
| `/etc/profile` | Sets environment variables and startup programs for **login shells** | When any user logs in (e.g. via terminal or SSH) |
| `/etc/bash.bashrc` | Applies shell behavior (aliases, functions) for **interactive non-login shells** | Every time a new terminal is opened |
| `/etc/environment` | Defines environment variables **globally** | Used by system-wide services and desktop logins |
| `/etc/profile.d/*.sh` | Extra scripts sourced by `/etc/profile` | Used to modularly set configs for all users |

✅ **Global files apply to all users**, but can be overridden by user files.

## 👤 2. User-Level (Local) Initialization Files

These affect **only the specific user**. Stored in the user's **home directory** (e.g. `~/.bashrc`).

| File | Purpose | When It's Used |
| --- | --- | --- |
| `~/.bashrc` | Sets environment for **interactive non-login** shells | Open a terminal window (GUI or TTY) |
| `~/.profile` | Loaded by **login shells** (if using Bash or sh) | Login via terminal, SSH, or GUI |
| `~/.bash_profile` | Used instead of `~/.profile` by Bash if it exists | Login shell sessions only |
| `~/.bash_login` | Alternative to `.bash_profile`, rarely used | Also login shells |
| `~/.xprofile` | Loads environment for **graphical sessions** | Login via display manager (GUI) |
| `~/.xinitrc` | Used when launching X manually (e.g. `startx`) | GUI setup |
| `~/.logout` | Runs commands at logout (only for login shells) | When user logs out from terminal session |

✅ **Order of priority**:

- `~/.bash_profile` > `~/.bash_login` > `~/.profile`
- Only **one of them** is used (the first found)