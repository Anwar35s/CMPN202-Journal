# Week 1 – System Planning & OS Selection

This week focused on preparing the virtualised environment for the Operating Systems coursework. I created two Ubuntu-based virtual machines, configured networking, selected appropriate Linux distributions, and gathered baseline system information. This forms the foundation for all later phases including SSH security, monitoring, scripting, and performance evaluation.

---

# ## 1. System Architecture Diagram

The system consists of two VirtualBox virtual machines:

- **Workstation VM (Ubuntu Desktop 22.04 LTS)**  
  Used to remotely manage the server via SSH, perform monitoring, and capture screenshots.

- **Server VM (Ubuntu Server / Debian Server)**  
  Headless system used for remote administration, security configuration, performance testing, and automation.

Both machines use a Host-Only Adapter for isolated communication and NAT for Internet access.

### Architecture Diagram

```
                         +--------------------------------------+
                         |         Workstation VM               |
                         |      Ubuntu Desktop 22.04 LTS        |
                         |--------------------------------------|
                         | • SSH client                         |
                         | • Monitoring scripts                 |
                         | • Remote administration              |
                         +------------------------+-------------+
                                                  |
                                   Host-Only Network (192.168.56.0/24)
                                                  |
                         +------------------------v-------------+
                         |             Server VM                |
                         |              (Headless)              |
                         |--------------------------------------|
                         | • OpenSSH Server                     |
                         | • Firewall (later configured)        |
                         | • AppArmor / Security Tools          |
                         +--------------------------------------+
```

**Architecture screenshot:**  
`![Architecture Diagram](architecture.png)`

---

# ## 2. Distribution Selection Justification

I selected **Ubuntu Server 22.04 LTS** (or Debian Server, depending on final choice) for the server. This provides a stable, secure, long-term supported environment that works well inside VirtualBox.

### Reasons for choosing Ubuntu/Debian as the server:
- Strong security features  
- Long-term support  
- Compatible with APT package management  
- Lightweight and efficient  
- Excellent documentation  
- Reliable for headless operation  

### Comparison With Alternatives

| Distribution | Pros | Cons |
|--------------|------|------|
| **Ubuntu Server** | Modern kernel, AppArmor, easy setup | Slightly heavier |
| **Debian Server** | Extremely stable, lightweight | Older software versions |
| Rocky Linux | SELinux enforced | Harder for beginners |

---

# ## 3. Workstation Configuration Decision

The workstation is **Ubuntu Desktop 22.04 LTS**, chosen because:

- It includes a full GUI (helpful for documentation)  
- Provides built-in SSH tools  
- Easy to use for remote administration  
- Mirrors real industry workflows  

This VM is used to SSH into the headless server VM.

---

# ## 4. Network Configuration Documentation

Both VMs use **two VirtualBox network adapters**:

### Adapter 1 — NAT  
- Provides Internet access for updates  
- Fully isolated from LAN  

### Adapter 2 — Host-Only Adapter  
- Used for communication between workstation and server  
- Required for SSH  
- Safely isolated for security testing  

### Assigned IP Addresses
Example configuration:
- Workstation: `192.168.56.10`
- Server: `192.168.56.11`

**Network screenshot:**  
`![IP Address](ipaddr.png)`

---

# ## 5. System Specification Evidence (Using Your Real Outputs)

These commands were run on the workstation VM.

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

**Screenshot:**  
`![uname output](uname.png)`

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

**Screenshot:**  
`![free output](free.png)`

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

**Screenshot:**  
`![df output](df.png)`

---

### **5.4 Network Interface Details**
Command:
```
ip addr
```

Your output confirmed the Host-Only Adapter network is active.

**Screenshot:**  
`![ip addr output](ipaddr.png)`

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

**Screenshot:**  
`![lsb release](lsb.png)`

---

# ## 6. Week 1 Reflection

During Week 1, I created and configured a dual-VM environment for my Operating Systems coursework. The workstation VM (Ubuntu Desktop) is fully set up for remote administration, and the server VM environment has been planned for headless SSH-based access. I configured VirtualBox networking with both NAT and Host-Only adapters, allowing isolated communication between the two systems.

I executed key Linux commands to gather baseline system information, including kernel version, memory usage, disk usage, network details, and distribution information. These outputs will be essential for future tasks such as system hardening, monitoring, performance testing, and automation scripting.

With the environment established, I am now ready to progress to Week 2, which focuses on SSH configuration, security planning, and initial system hardening.

---

**End of Week 1**
