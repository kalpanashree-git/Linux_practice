# 👤 Task 1: Basic User Management
**DevOps Fundamentals: User Creation, Security, and Privilege Escalation**

> [!TIP]
> **Objective:** Securely provision a new server user, enforce an immediate password reset policy for security compliance, and grant administrative (sudo) privileges.

---

## 🛠️ Task Overview
- **User Creation:** Provision a new user account with a dedicated home directory.
- **Security Policy:** Force the user to update their password upon the first login.
- **Privilege Management:** Manually assign root-level (sudo) access.

---

## 1. User Provisioning
In Linux, while `useradd` exists, we utilize `adduser` for a more streamlined, automated setup.

| Command | Action | Recommended? |
| :--- | :--- | :--- |
| `useradd` | Creates a raw user; requires manual home directory setup. | ❌ No |
| `adduser` | Creates user, home directory, and prompts for password/details. | ✅ Yes |

**Execution:**
```bash
# Creating a user named 'Developer'
sudo adduser Developer

---

## 2. Giving access for the user to Change their own password
For this, we want the password to get "deleted" or expire the second the user logs in so they have to pick a new one immediately.



**The command:**
```bash
sudo chage -d 0 Developer

## 3. Giving sudo access to a user
> [!CAUTION]
> **CAUTION:** Should be given only to authorised persons. And can be done only by the Root user.

Sudo access means giving root level access like they can install new things to the server and they can delete or view root level files. There are multiple ways to do this, but I did it manually for a specific user.

**Steps I followed:**
1. Run the command `sudo visudo`
2. Inside the file, I added this line:

```bash
Developer ALL=(ALL:ALL) ALL
