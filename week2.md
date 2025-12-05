Week 2 – SSH Installation, Configuration & Remote Access

This week focused on enabling secure remote administration on the server VM by installing and configuring OpenSSH. I verified the service status, ensured that SSH was listening on the correct network interface, reviewed the SSH daemon configuration, and successfully connected from my macOS workstation. These steps establish a secure foundation for future tasks including system hardening and automation.

1. Installing and Enabling OpenSSH Server

To allow remote access, I began by installing the OpenSSH server package:

sudo apt update
sudo apt install openssh-server -y


After installation, I checked whether the SSH service was active and running.

SSH Service Status

The SSH service showed as active (running), confirming that it started successfully.

2. Identifying the Server’s Network Address

To connect to the server over the network, I retrieved its IP address using:

ip addr


The interface enp0s2 was assigned the IP 192.168.64.13, which I used to initiate the SSH connection.

Server IP Address

3. Verifying SSH Port and Listening State

Next, I checked that SSH was listening correctly on port 22 — the default port for secure shell access:

sudo ss -tulnp | grep ssh


The output confirmed that sshd was listening on both IPv4 and IPv6:

0.0.0.0:22

[::]:22

This means SSH is accessible from any network interface allowed by the VM’s network configuration.

SSH Listening on Port 22

4. Reviewing the SSH Daemon Configuration

The SSH daemon configuration file contains important security-related settings. I viewed the file using:

sudo cat /etc/ssh/sshd_config


This allowed me to verify:

Default port (22)

Authentication settings

Key exchange & ciphers

Logging configuration

No changes were made this week, but reviewing the defaults helps prepare for security hardening in upcoming weeks.

SSHD Configuration File

5. Testing SSH Login from macOS Workstation

Finally, I tested the complete setup by attempting a remote login from my Mac terminal using the command:

ssh anwar35s@192.168.64.13


The connection succeeded after confirming the host fingerprint. This demonstrated that the server was reachable and authentication was functioning properly.

Successful SSH Login

6. Week 2 Reflection

During Week 2, I completed the setup of secure remote access to the server VM. I installed and enabled the OpenSSH server, confirmed its operational status, checked the network configuration, and verified that port 22 was listening correctly. A successful SSH login from my macOS workstation confirmed that the system is now ready for remote administration.

These steps provide an essential foundation for future activities, including:

SSH hardening

User access control

Firewall configuration

System monitoring and scripting

With remote access established, the server is now prepared for the more advanced security and automation tasks in the upcoming weeks.
