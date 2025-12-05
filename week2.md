Week 2 – SSH Installation, Configuration & Remote Access

This week focused on installing and configuring SSH on the server VM, verifying service status, network connectivity, and successful remote login from the workstation. This establishes a secure remote administration environment for the rest of the coursework.

1. Installing & Enabling OpenSSH Server

Installed with:

sudo apt update
sudo apt install openssh-server -y


After installation, checked service status:

sudo systemctl status ssh


Screenshot – SSH Service Status
![SSH Status](/mnt/data/Screenshot 2025-12-05 at 14.22.23.png)

2. Checking the Server’s IP Address

Used:

ip addr


to find the server IP (on UTM VM’s network interface).

Screenshot – Server IP Address
![Server IP](/mnt/data/Screenshot 2025-12-05 at 14.24.05.png)

3. Verifying SSH Port Listening State

Check command:

sudo ss -tulnp | grep ssh


Ensures SSHD is listening on default port 22.

Screenshot – SSH Port Listening
![SSH Port](/mnt/data/Screenshot 2025-12-05 at 14.23.09.png)

4. Reviewing SSH Daemon Configuration File

Displayed configuration via:

sudo cat /etc/ssh/sshd_config


To verify default settings before further hardening.

Screenshot – SSHD Configuration
![SSHD Config](/mnt/data/Screenshot 2025-12-05 at 14.27.35.png)

5. Testing SSH Login from Mac Workstation

From macOS terminal, logged into server using:

ssh anwar35s@192.168.x.x


Login succeeded after fingerprint acceptance and password entry.

Screenshot – Successful SSH Login
![SSH Login](/mnt/data/Screenshot 2025-12-05 at 14.40.43.png)

6. Week 2 Reflection

This week established a fully functioning SSH remote administration setup. I installed and verified OpenSSH, confirmed SSHD status and port listening, validated network configuration, and performed a successful remote login from the workstation. This remote system access is critical for forthcoming tasks such as security hardening, firewall setup, monitoring, and automation. The server is now prepared and functioning as a remote-managed, secure VM.

End of Week 2
