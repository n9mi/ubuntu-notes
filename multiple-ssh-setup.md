## Create new ssh key for Account 1
```
$ ssh-keygen 
```
Save to path /home/$USER/.ssh/id_rsa_account_1

## Create new ssh key for Account 2
```
$ ssh-keygen 
```
Save to path /home/$USER/.ssh/id_rsa_account_2

## Add gitconfig for Account 1
```
$ sudo mousepad .gitconfig_account_1

[user]
name = Account 1
email = account1@your.company

[core]
sshCommand = ssh -i ~/.ssh/id_rsa_account_1
```

## Add gitconfig for Account 2
```
$ sudo mousepad .gitconfig_account_2

[user]
name = Account 2
email = account2@your.company

[core]
sshCommand = ssh -i ~/.ssh/id_rsa_account_2

```

## Make working directory for both account
```
$ cd ~
$ mkdir account1
$ mkdir account2
```

## Add gitconfig to define the previous specific gitconfig
```
$ sudo mousepad .gitconfig

[includeIf "gitdir:~/account1/"]
  path = .gitconfig_account_1
[includeIf "gitdir:~/account2/"]
  path = .gitconfig_account_2
```
