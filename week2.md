Week 2 – SSH Configuration & Remote Access Setup

This week focused on configuring secure remote access to the server VM, enabling SSH, verifying service status, confirming network availability, and testing an SSH login from my Mac workstation. These steps prepare the system for upcoming security and automation tasks.

2.1 Installing & Enabling SSH

To enable remote access, I installed the OpenSSH server:

sudo apt update
sudo apt install openssh-server -y


Then I checked that SSH was running correctly.

SSH Service Status

2.2 Checking Server IP Address

I used the following command to identify the server’s active IP address:

ip addr


This IP is required for the SSH connection.

Server IP Output

2.3 Verifying SSH Port Listening (Port 22)

I ensured SSH was listening on port 22 using:

sudo ss -tulnp | grep ssh

SSH Port Listening

2.4 Reviewing SSHD Configuration File

I checked the SSH daemon’s configuration to confirm default security settings:

sudo cat /etc/ssh/sshd_config

SSHD Configuration File

2.5 Testing SSH Login from My Mac

From macOS, I connected using:

ssh anwar35s@192.168.64.13


The connection was successful, confirming SSH setup works.

SSH Login Screenshot

Week 2 Reflection

This week I successfully set up and validated SSH remote access. I confirmed service status, verified network connectivity, checked SSH configuration, and logged in remotely from my Mac. The server is now ready for further security hardening and automation tasks in the coming weeks.
