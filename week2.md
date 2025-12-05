WEEK 2 — SSH Configuration, Hardening & Remote Access (FULL REPORT)

Paste everything below into week2.md.

# Week 2 – SSH Configuration, Security Hardening & Remote Access

This week focused on enabling remote access to the server VM using SSH, securing the SSH configuration, validating connectivity from the workstation, and documenting system behaviour using terminal commands and screenshots.

SSH is a fundamental component of secure system administration, allowing encrypted access to remote machines. Configuring SSH properly ensures both usability and protection against unauthorized access.

## 1. Enabling SSH on the Server

SSH is installed on Ubuntu-based systems using:

sudo apt update
sudo apt install openssh-server -y


After installation, the SSH service should automatically start.

## 2. Verifying SSH Service Status

To confirm that the SSH server is running:

sudo systemctl status ssh


Expected output includes:

Active: active (running)

Shows process ID (sshd)

Indicates that the service is enabled and running on boot

Screenshot to upload:
ssh_status.png

## 3. Checking SSH Port Listening

SSH listens by default on port 22. To verify:

sudo ss -tulnp | grep ssh


Expected output:

tcp   LISTEN  0  4096  0.0.0.0:22   0.0.0.0:* 
tcp   LISTEN  0  4096  [::]:22      [::]:*


This confirms SSH is reachable on all interfaces.

Screenshot to upload:
ssh_port.png

## 4. Viewing the SSH Configuration File

The SSH server settings are located in:

/etc/ssh/sshd_config


To display the configuration:

sudo cat /etc/ssh/sshd_config


Important default settings:

#Port 22 (default SSH port)

PermitRootLogin prohibit-password

PasswordAuthentication yes (enabled by default)

PubkeyAuthentication yes

Screenshot to upload:
sshd_config.png

## 5. Checking the Server’s IP Address

To determine the network interface and IP address:

ip addr


From your real output:

Interface: enp0s2

IP Address: 192.168.64.13
(This is the address used to SSH into the server)

Screenshot to upload:
server_ip.png

## 6. SSH Login From Your Host Machine (Mac)

You successfully logged into the server from macOS using:

ssh anwar35s@192.168.64.13


Your actual successful login output included:

Host authenticity prompt

Password entry

Ubuntu welcome message

System info (load, memory, users)

Display of last login

This confirms the server is reachable and SSH is functioning correctly.

Screenshot to upload:
ssh_login.png

## 7. Security Hardening (Basic)
7.1 Disable Root Login

Edit configuration:

sudo nano /etc/ssh/sshd_config


Ensure:

PermitRootLogin no

7.2 Change SSH Port (Optional)

Example:

Port 2222

7.3 Restart SSH to Apply Changes
sudo systemctl restart ssh

## 8. Reflection – Week 2

In Week 2, I enabled and configured SSH on my server VM and ensured secure remote access using my workstation. I verified that SSH was installed, running, and listening on the correct port. Using ip addr, I located the server’s IP address, then successfully connected from my macOS host using the SSH client.

I also examined the sshd_config file to understand how authentication, root login, ports, and encryption settings are managed. This week’s work forms the foundation for secure remote administration, which will be essential in future weeks when configuring firewalls, automating tasks, and running monitoring tools.
