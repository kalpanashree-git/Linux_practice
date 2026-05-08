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
