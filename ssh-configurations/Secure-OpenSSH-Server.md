# Detailed Procedure to secure OpenSSH Server.

## Introduction

Linux servers are often administered remotely using SSH by connecting to an OpenSSH server, which is the default SSH server software used within Ubuntu, Debian, CentOS, FreeBSD, and most other Linux/BSD-based systems.

OpenSSH server is the server side of SSH, also known as SSH daemon or `sshd`. You can connect to an OpenSSH server using the OpenSSH client, specifically by running the ssh command. You can learn more about the SSH client-server model in SSH Essentials: Working with SSH Servers, Clients, and Keys. Properly securing your OpenSSH server is very important, as it acts as the front door or entry-point into your server.

## Prerequisites

1. Complete the initial setup & updates on the system.
2. Create a non-root user & secure the user.
3. Log-in to your server as the non-root user.

## Step 1 - General Hardening

Most of the edits will be made on the OpenSSH configuration file at `/etc/ssh/sshd_config`.

Before continuing it is a good idea create a backup of your existing configuration file so that you can restore it in the unlikely event that something goes wrong.

1. Create a backup of the file using the following `cp` command:

    ```
    sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.bak
    ```

    This will save a backup copy of the file to /etc/ssh/sshd_config.bak

2. Next, review the current default OpenSSH configuration options that correspond to the settings in `/etc/ssh/sshd_config`. To do this, run the following command:
    ```
    sudo sshd -T
    ```

    This will run OpenSSH server in extended test mode, which will validate the full configuration file and print out the effective configuration values.

3. You can now open the configuration file using `nano` or your favorite text editor to begin implementing the initial hardening measures:
