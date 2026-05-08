# 🚨 Incident Response: Rapid Disk Exhaustion
**DevOps Case Study: Log Flooding Analysis**

> [!IMPORTANT]
> **Status:** Resolved & Documented
> **Incident Overview:** Detected critical disk space depletion in the `/var/log` partition. Identified a rogue process generating excessive log data and captured forensic evidence in a tool-restricted environment.

---

## 1. Crisis Detection
The `/var/log/messages` file was observed growing at an unsustainable rate of **~15 GB per hour**. Disk utilization reached **92%**, risking a total system hang.

| Constraint | Detail |
| :--- | :--- |
| **Environment** | Minimalistic Linux installation |
| **Unavailable Tools** | `lsof`, `fuser`, `iotop` |
| **Challenge** | Real-time identification of a high-frequency write process |

---

## 2. Forensic Investigation
Utilized the `top` utility to monitor process states and resource consumption. The culprit was identified by its high **%CPU** and frequent transitions into the **D (Uninterruptible Sleep)** state.

**Identified Process:** `log_generator` (PID 62)


---

## 3. Evidence Collection & Action
The requirement was to isolate the process details and extract the specific log pattern to the `/home/devops/excessive_log_process.txt` repository.

### Execution:
```bash
# 1. Capturing process forensics
ps -p 62 -f > /home/devops/excessive_log_process.txt

# 2. Extracting log signatures for debugging
tail -n 50 /var/log/messages >> /home/devops/excessive_log_process.txt
