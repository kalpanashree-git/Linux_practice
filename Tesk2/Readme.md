What do you do when lsof and fuser are missing?
#linux #lsof #fuser #top #ps


Back-to-basics Linux troubleshooting.

---The Scenario---
A log file (/var/log/messages) was growing by gigabytes per hour.
I needed to find the process ID (PID) responsible and capture the evidence.

---The Challenge---
The environment was a "minimal" install. Standard diagnostic tools like iotop, lsof, and fuser were not installed.

---The Investigation---
The Kernel Source:
    I looked into the /proc filesystem. Since everything in Linux is a file, I tried searching /proc/*/fd to see who had the log file open.

Resource Monitoring:
    Because the writer was so fast (opening/closing the file in a loop), I switched to top.

The Discovery: 
    Found log_generator (PID 62) with high CPU usage and an "S" status, indicating it was heavily active.


---The Evidence Capture---
I had to save the process details and the last 50 lines of the log to a single file:

ps -p 62 -f > excessive_log_process.txt
tail -n 50 /var/log/messages >> excessive_log_process.txt


--Key Takeaway--: 

You don't always need fancy tools. Understanding the /proc filesystem and the power of tail and ps is enough to solve most "invisible" problems.
