Week 2 – SSH Installation, Configuration & Remote Access

This week focused on installing, enabling, and testing secure remote access using OpenSSH on the server VM. I confirmed service status, verified SSH port listening, inspected configuration files, and successfully logged in remotely from my macOS workstation. This sets up the foundation for secure administration in future weeks.

1. Installing & Enabling OpenSSH Server

I first installed OpenSSH Server on the VM:

sudo apt update
sudo apt install openssh-server -y


Then confirmed the service was running:

sudo systemctl status ssh

Screenshot – SSH Service Status

2. Checking the Server’s IP Address

To connect remotely, I checked the server's IP address:

ip addr


The active address was on the 192.168.64.x subnet.

Screenshot – Server IP Address

3. Verifying SSH Port Listening State

I confirmed that SSH was listening on port 22:

sudo ss -tulnp | grep ssh


SSH was correctly accepting connections over IPv4 and IPv6.

Screenshot – SSH Port Listening

4. Reviewing SSH Daemon Configuration

I reviewed the SSH configuration file to identify authentication settings, port configuration, and general server policies:

sudo cat /etc/ssh/sshd_config

Screenshot – SSHD Configuration File

5. Testing SSH Login from macOS Workstation

From my macOS terminal, I initiated an SSH login to the server:

ssh anwar35s@192.168.64.13


I accepted the host key and authenticated successfully.

Screenshot – Successful SSH Login

6. Week 2 Reflection

During Week 2, I successfully established secure remote access to the server VM. I verified:

SSH service installation and status

Correct network configuration

SSH port listening functionality

SSHD configuration defaults

Successful remote login from macOS

This confirms the server is now ready for advanced tasks like SSH hardening, firewall configuration, automation, and system monitoring in later weeks.

End of Week 2
