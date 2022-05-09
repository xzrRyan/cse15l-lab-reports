# CSE 15L lab report 3

## Streamlining ssh Configuration

1. First using `command + shift + .` to show hidden `.ssh directory` on Mac system
2. Editing `.ssh/config` by Visual Studio Code with
    ```
    Host ieng6
        HostName ieng6.ucsd.edu
        User cs15lsp22ahn
    ```
    ![config](sshkeyhost.png)

3. Logging to the `cs15lsp22ahn server account` with alias `ieng6`![ssh](sshAlias.png)

4. `scp sshStreamlineFile.txt` to the server account with alias `ieng6` 
![scpFile](scpAlias.png)
![success](sucessfulSCP.png)

## Github Access from ieng6

1. Using `gen-key` on `ieng6 server account` to create both public and private ssh key files
> Public key's absolute path on server account is `/home/linux/ieng6/cs15lsp22/cs15lsp22ahn/.ssh/id_rsa.pub`
![ieng6publickey](publicSSHKey.png)

> Public key located in Github in `profile > setting > SSH and GPG keys > New SSH key` 
![ieng6gitkey](Githubkey.png)

2. Private key's absolute path is also under `.ssh` directory on server account
> `/home/linux/ieng6/cs15lsp22/cs15lsp22ahn/.ssh/id_rsa`
![privateKey](privatekey.png)

3. Adding two new files `hola.txt` and `vanikkam.txt` into `test repository` on `ieng6 server account` and `commit` changes
![commit](GitCommit.png)

4. `Push` commits from `ieng6 server account` to `test repository on GitHub`
![push](PushCommit.png)

5. Link of `commit` history is attached [here](https://github.com/xzrRyan/test/commit/9211ef7c37a15e228a6451e66ebb4e69bbc651b9)

## Copy Whole Directory to GitHub
1. `scp` whole `markdown-parse directory` to server account by `scp -r . ieng6:~/markdown-parse`
![markdown](scpMarkdown.png)

2. `markdown-parse directory` now in server account
![server](MarkdownServer.png)
Compiling `MarkdownParse.java` and `MarkdownPaseTest.java` and running `MarkdownPaseTest`
![test](RunningTest.png)

3. Combining `scp`,`ssh`, `javac`, and `java` in one command line
    ```
    scp -r . ieng6:~/markdown-parse; ssh ieng6 "cd markdown-parse; /software/CSE/oracle-java-17/jdk-17.0.1/bin/javac -cp lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar MarkdownParse.java MarkdownParseTest.java; /software/CSE/oracle-java-17/jdk-17.0.1/bin/java -cp lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar:. org.junit.runner.JUnitCore MarkdownParseTest"
    ```
    `scp command` running first in `local computer`
    ![oneline](javacVersion.png)

    Then `ssh command` running followed by `cd` with `javac` and `java` in correct versions on `server account`
    ![success](success.png)
