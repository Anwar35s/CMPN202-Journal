# Week 1 – System Planning & OS Selection

This week focused on preparing the virtualised environment for the Operating Systems coursework. I created two Ubuntu-based virtual machines, configured VirtualBox networking, selected appropriate distributions, and gathered baseline system information. This setup will support all later phases including security hardening, performance testing, monitoring, and scripting.

---

# ## 1. System Architecture Diagram

The coursework requires two separate virtual machines:  
1. A **headless Ubuntu Server VM**  
2. A **Ubuntu Desktop workstation VM** used for SSH-based administration

Both machines communicate via a private **Host-Only Adapter (192.168.56.0/24)** while still having Internet access via NAT.

### Architecture Diagram

```
                         +--------------------------------------+
                         |         Workstation VM               |
                         |      Ubuntu Desktop 22.04 LTS        |
                         |--------------------------------------|
                         | • SSH client                         |
                         | • Monitoring scripts                 |
                         | • Used for remote admin              |
                         +------------------------+-------------+
                                                  |
                                   Host-Only Network (192.168.56.0/24)
                                                  |
                         +------------------------v-------------+
                         |             Server VM                |
                         |       Ubuntu Server 22.04 LTS        |
                         |--------------------------------------|
                         | • Headless system                    |
                         | • OpenSSH enabled                    |
                         | • AppArmor active                    |
                         | • Firewall later configured          |
                         +--------------------------------------+
```

*(Insert your diagram)*  
`![Architecture Diagram](architecture.png)`

---

# ## 2. Distribution Selection Justification

I chose **Ubuntu Server 22.04 LTS** as the server OS.

### Reasons:
- Excellent long-term security support  
- Built-in **AppArmor** mandatory access control  
- Reliable, modern kernel  
- Compatible with VirtualBox  
- Uses APT, making administration simple  
- Well documented, widely used in real systems

### Comparison With Alternatives

| Distribution | Pros | Cons |
|--------------|------|------|
| **Ubuntu Server 22.04** | Secure, modern, AppArmor, best documentation | Slightly larger size |
| Debian | Very stable | Older packages |
| Rocky Linux | SELinux enforced | More complex for beginners |

**Conclusion: Ubuntu Server 22.04 LTS is ideal for this coursework.**

---

# ## 3. Workstation Configuration Decision

I selected **Ubuntu Desktop 22.04 LTS** for the workstation VM.

### Benefits:
- GUI makes screenshot capture and documentation easier  
- Includes built-in SSH tools  
- Allows full remote administration of the server  
- Mirrors real-world DevOps workflow (client → server via SSH)  
- Keeps the server completely headless as required  

---

# ## 4. Network Configuration Documentation

Both VMs use **two network adapters** in VirtualBox:

### Adapter 1 — NAT
- Provides internet access  
- Used only for updates and installing packages  

### Adapter 2 — Host-Only (vboxnet0)
- Provides isolated communication between the workstation and server  
- Required for SSH and monitoring  
- Ensures safe security testing  

### Assigned IP Addresses
After configuring the Host-Only network:

- **Workstation:** `192.168.56.10`  
- **Server:** `192.168.56.11`

*(Insert your screenshots here after uploading)*  
`![IP Address](ipaddr.png)`

---

# ## 5. System Specification Evidence (Using Your Real Outputs)

This section captures baseline system information collected using Linux CLI tools.

---

### **5.1 Kernel Information**
Command:
```
uname -a
```

Your output:
```
Linux anwar35s 6.8.0-87-generic #88-Ubuntu SMP PREEMPT_DYNAMIC Sat Oct 11 09:16:38 UTC 2025 aarch64 aarch64 aarch64 GNU/Linux
```

*(Insert screenshot)*  
`![uname](uname.png)`

---

### **5.2 Memory Information**
Command:
```
free -h
```

Your output:
```
Mem:  3.8Gi total, 1.4Gi used, 675Mi free, 58Mi shared, 2.0Gi buff/cache, 2.4Gi available
Swap: 3.8Gi total, 268Ki used
```

*(Insert screenshot)*  
`![free](free.png)`

---

### **5.3 Disk Usage**
Command:
```
df -h
```

Your output:
```
Filesystem                      Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-ubuntu   30G   13G  16G   45%  /
/dev/vda2                        2.0G 203M 1.6G   12% /boot
/dev/vda1                        1.1G  6.4M 1.1G   1% /boot/efi
```

*(Insert screenshot)*  
`![df](df.png)`

---

### **5.4 Network Interface Details**
Command:
```
ip addr
```

Your output (summarised):
```
inet 192.168.56.xx  (correct host-only IP)
```

*(Insert screenshot)*  
`![ip addr](ipaddr.png)`

---

### **5.5 Distribution Information**
Command:
```
lsb_release -a
```

Your output:
```
Distributor ID: Ubuntu
Description: Ubuntu 24.04.2 LTS
Release: 24.04
Codename: noble
```

*(Insert screenshot)*  
`![lsb release](lsb.png)`

---

# ## 6. Week 1 Reflection

During Week 1, I set up the complete virtualised environment required for the coursework. I created two Ubuntu virtual machines, configured both NAT and Host-Only networking, and selected Ubuntu Server 22.04 LTS as the most appropriate server distribution. I then collected baseline system specifications using standard Linux commands such as `uname`, `free`, `df -h`, `ip addr`, and `lsb_release`.

This initial setup ensures a secure and realistic remote administration environment. It will support the later phases involving SSH security, firewalls, performance testing, automation scripts, and security auditing. The system is now ready to progress to Week 2.

---

**End of Week 1**

