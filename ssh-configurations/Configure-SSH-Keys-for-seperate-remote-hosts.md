# Procedure to configure SSH to use different Identity Files / Keys for different remote hosts.

> Useful when using different SSH Keys for different remote hosts on the same device [Different Keys for GitHub & GitLab for example].

## 1. Procedure for Windows

### SSH Config File

Generally in Widnows machines the SSH Config file is stored in the following location assuming you have already used SSH once before. Otherwise you need to manually create the `.ssh` directory.

```C:\Users\USER_NAME\.ssh```

### Create the config file

If the config file is not present in this location already, you can create it using the Git Bash console.

1. Go to the `.ssh` directory at `C:\Users\USER_NAME\.ssh`.
2. Right Click & choose `Git Bash Here`.
3. Create file named `config` using the `touch` command from the Git Bash terminal by typing `touch config`.
4. Open jthe config file using `nano` by typing `nano config` or use notepad to open the file.
5. Now paste the following in the config file `Change the Identity file names according to your key names`
```
# GITHUB
Host github.com
   HostName github.com
   PreferredAuthentications publickey
   IdentityFile ~/.ssh/id_rsa_hub

# GITLAB
Host gitlab.com
   HostName gitlab.com
   PreferredAuthentications publickey
   IdentityFile ~/.ssh/id_rsa_lab
```
6. Save the file. Use `ctrl+o` to save the file in nano & `ctrl+x` to close nano or save using notepad.

**Your SSH should now be configured to use the specified keys with the specified hosts.**

---

## 2. Procudure for Linux.

### SSH Config File

Generally in Widnows machines the SSH Config file is stored in the following location assuming you have already used SSH once before. Otherwise you need to manually create the `.ssh` directory.

```~/.ssh/```

If not present already create the `.ssh` directory using

`mkdir .ssh`


### Create the config file

If the config file is not present in this location already, you can create it from terminal.

1. Go to the `.ssh` directory at `C:\Users\USER_NAME\.ssh`.
2. Right Click & choose `Open Terminal Here` or Open your terminal normally, it should be in yoour home directory by default.
3. Create file named `config` using the `touch` command from the terminal by typing `touch config`.
4. Open jthe config file using `nano` by typing `nano config`.
5. Now paste the following in the config file `Change the Identity file names according to your key names`
```
# GITHUB
Host github.com
   HostName github.com
   PreferredAuthentications publickey
   IdentityFile ~/.ssh/id_rsa_hub

# GITLAB
Host gitlab.com
   HostName gitlab.com
   PreferredAuthentications publickey
   IdentityFile ~/.ssh/id_rsa_lab
```
1. Save the file. Use `ctrl+o` to save the file in nano & `ctrl+x` to close nano.

**Your SSH should now be configured to use the specified keys with the specified hosts.**
