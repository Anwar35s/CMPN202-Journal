Week 2 – SSH Configuration & Secure Remote Access

This week focused on installing, configuring, and validating secure SSH access to the server virtual machine. I also confirmed networking, checked SSH daemon status, and performed a remote login from my macOS host machine.

1. Server Network Configuration

I first confirmed the server's network interfaces using:

ip addr


This showed the server’s assigned IP address on interface enp0s2.

Screenshot – Server IP Address

2. Installing & Enabling OpenSSH Server

To allow remote access, I installed the OpenSSH server package:

sudo apt update
sudo apt install openssh-server -y


Then I checked if SSH was running:

sudo systemctl status ssh

Screenshot – SSH Service Status

3. Verifying SSH Port Listening (Port 22)

To confirm that SSH is accepting network connections, I ran:

sudo ss -tulnp | grep ssh


This output shows SSH listening on:

0.0.0.0:22 (IPv4)

[::]:22 (IPv6)

Screenshot – SSH Port Listening

4. Reviewing SSH Daemon Configuration

To verify server-wide SSH settings, I examined:

sudo cat /etc/ssh/sshd_config


This file controls options such as allowed authentication methods, listening port, and security recommendations.

Screenshot – SSHD Config File

5. Successful SSH Login From macOS Host

Finally, I tested remote access from my Mac terminal:

ssh anwar35s@192.168.xx.xx


I successfully logged in, confirming:

Network communication works

SSH keys and passwords are accepted

The server is remotely manageable

Screenshot – Successful SSH Login

6. Reflection

In Week 2, I successfully configured SSH access for my Linux server VM and validated connectivity from my macOS workstation. I reviewed SSH configuration files, confirmed port listening status, and performed an external login test. This prepares the environment for future work involving secure authentication, firewall rules, automation, and system monitoring.
