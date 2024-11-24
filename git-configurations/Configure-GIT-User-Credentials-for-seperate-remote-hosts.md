# Procedure to configure GIT to use different user credentials for different remote hosts.

> **Problem Statement** : I have 2 different emails registred with GitHub & GitLab. I want Git to use the email registred with GitHub to commit to repos on GitHub & the email regisred with GitLab to commit to repos on GitLab.

> **Solution** : Create 2 different folders for GitHub & GitLab & 2 sepereate .gitconfig files for GitHub & GitLab. Then setup the original .gitconfig to use the different .gitconfig files depending on the repo location.

## 1. Procedure for Windows

### I. Seperate Folders

Create 2 seperate folders for GitHub & GitLab.

### II. Edit main `.gitconfig` file

Edit the main `.gitconfig` file at your user directory `c:\Users\UNSERNAME\.gitconfig` as -

```
[includeIf "gitdir/i:c:\Users\USERNAME\Documents\Development\GitHub\"]
  path=.gitconfig-GitHub
[includeIf "gitdir/i:c:\Users\USERNAME\Documents\Development\GitLab\"]
  path=.gitconfig-GitLab
```

### III. Create the seperate `.gitconfig` files

Create 2 different `.gitconfig` files in the same directory as the main `.gitconfig` file called `.gitconfig-GitHub` & `.gitconfig-GitLab`.

### IV. Edit the seperate `.gitconfig` files

Edit the seperate `.gitconfig` files as -

**.gitconfig-GitHub** :

```
[user]
name=username-for-github
email=email-for-github
```
**.gitconfig-GitLab**
```
[user]
name=username-for-gitlab
email=email-for-gitlab
```


## 1. Procedure for Linux

### I. Seperate Folders

Create 2 seperate folders for GitHub & GitLab.

### II. Edit main `.gitconfig` file

Edit the main `.gitconfig` file at your user directory `~/.gitconfig` as -

```
[includeIf "gitdir/i:~/Documents/Development/GitHub/"]
  path=.gitconfig-GitHub
[includeIf "gitdir/i:~/Documents/Development/GitLab/"]
  path=.gitconfig-GitLab
```

### III. Create the seperate `.gitconfig` files

Create 2 different `.gitconfig` files in the same directory as the main `.gitconfig` file called `.gitconfig-GitHub` & `.gitconfig-GitLab`.

### IV. Edit the seperate `.gitconfig` files

Edit the seperate `.gitconfig` files as -

**.gitconfig-GitHub** :

```
[user]
name=username-for-github
email=email-for-github
```
**.gitconfig-GitLab**
```
[user]
name=username-for-gitlab
email=email-for-gitlab
```

*It is essential that the `includeIf` starts with `gitdir/i:` to turn off case-sensitive. If you don't do this step your config will not be loaded when you use VSCode.*
