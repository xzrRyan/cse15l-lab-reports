# CSE 15L lab report 1

## Part 1 VScode
> Blockquote Visual studio Code is a powerful code editor for Windows, Linux and macOS operation systems.

1. go to [Visual Studio Code website](https://code.visualstudio.com/)

2. select the version for your operation system. ![VScode](VScode1.png)

3. open downloaded VScode, it should be like this ![VScode](VS-code.png)

## Part 2 Remote connection
> remote connection is usually done by **SSH** (Secure Shell Protocol) between local computer and server.

1. SSH requires `account` and `password` to remotely access to server account. You can find `acoount` and update `password` in [there](https://sdacs.ucsd.edu/~icc/index.php)

2. Opening a terminal, type `ssh` `Youraccount` and then type `Yourpassword`
as below ![below](ssh.png)

3. If successfully accessing to server, you should see ![this](access.png) 

## Part 3 Linux commands
> linux commands can be convenient to edit files' position, properties, and content without actually seeing/clicking it.

* **Some commands you can put in the terminal**
1. `ls` (lists all files/ directories under current directory)![below](ls.png)
2. `pwd` (print current directory)![below](pwd.png)
3. `cat` `Yourfilename` (print all the content in Yourfilename) ![below](cat.png)

## Part 4 Moving file with scp
> scp is a command to copy your `specified local file` to your server account under `specified directory`.

1. `scp` `Yourfilename` `Youraccount:TargetDirectory` and type `Yourpassword`.
![below](scp.png)
2. after `ssh` to `Youraccount`, change to your target directory, and then type `ls`. You should see your specified file copied to there. ![there](ls-scp.png)

## Part 5 setting SSH key
> Keeping a `public` SSH key on server account while a `private` SSH key on the client saves your time from typing password when `ssh` or `scp` file to access to your server account

1. In client terminal, type `ssh-keygen`. This command generates both `public` and `private` key files on the client. 

2. Continuously pressing `enter` when you see 
```
Generating public/private rsa key pair
```
```
Enter file in which to save the key (/Users/<user-name>/.ssh/id_rsa): /Users/<user-name>/.ssh/id_rsa
```
```
Enter passphrase (empty for no passphrase):
```
```
Enter same passphrase again: 
```
You should see the key's random image like
![random](random-image.png)

3. Now, we need to log into `server account` and create a directory .ssh by `mkdir .ssh`

4. Then, we go back to `local account` and copy your public key file to .ssh file in the `server account` by
`scp YourPublicKeyfile YourAccount:~/.ssh/authorized_keys`

5. You can now log into your `server account` without typing password from your `current local account`. It should be like: ![keygen](sshkeygen.png)


## Part 6 Optimizing remote running
> Here are three tricks for optimizing remote running

1. Using `up-arrow` on your keyboard to show the last command you put in terminal.

2. Put multiple commands on one line in a terminal, but using `;` to separate commands. That terminal will run commands one after another. 
For example: ![separate](separate-commands.png)

3. To perform multiple commands one after another right after logging to server account. We should use `" "` to include command 1; command 2;. Also, there is a `space` but not `;` between `ssh Youraccount` and `"Your commands"`. For exmaple: ![quotation](quotation-marks.png)