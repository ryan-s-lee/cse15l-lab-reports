UCSD CSE 15L Lab 1 Report: How to Remotely Access UCSD Servers
=================================================
## Why this Article?
This article was written as part of an assignment for UCSD's CSE 15L class. However, I also intend for this to be a simple guide for myself and others about how I can run the command line on a server.  

## Installing VS Code
As I already had VS Code installed long before the assignment even began, this will be a recount of how I probably would have done it if it wasn't installed.  
First, I would go to [Link]https://code.visualstudio.com/ (or just look up vscode on Google). I would see a big blue button in the center of the screen saying "Download for Windows," which I would click (Mac users, I would presume would see "Download for Mac").  
![Placeholder](/cse15l-lab-reports/assets/images/img01-vscode.png)  
The setup wizard should be installed when I do.  
I would work through the setup wizard. Under "Other," I would check all of the options like so:  
![Placeholder](/cse15l-lab-reports/assets/images/img02-optionalapps.png)  
This is because I actually like to use code to edit my files. It's somehow aestheically pleasing to use, compared to things like Notepad++. Checking all items allows me to access VS Code more easily for different file types.  
Then I would click Install, and I should be able to open the VS Code application, whether it be via Desktop shortcut or Start Menu shortcut.  
## Remotely Connecting
We will start by making sure SSH is actually installed on our computer. The instructions can be found at [this website](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse#install-openssh-using-windows-settings), but I will summarize the steps for Windows here.  
First, open your computer's Settings and select Apps and Features (or open it from the Start Menu). There is an Apps & Features section under the Apps & Features Page. Right under the header, there is an _Optional Features_ link you should click.  
![Placeholder](/cse15l-lab-reports/assets/images/img02-optionalapps.png)  
Search the _Installed Features_ for OpenSSH and check if you have the client installed. If not, click _Add a Feature,_ search and select _OpenSSH Client_, and install it.  
![Placeholder](/cse15l-lab-reports/assets/images/img03-sshclient.png)  
I usually use an external terminal to remotely connect to a server. However, CSE 15L recommends that you open a Terminal within VS Code, which you can do by selecting View -> Terminal, or by pressing CTRL+\`. Once you have a terminal open, our goal is to log into your account on the ieng6 server (essentially a folder that you have permission to use on a remote computer). You can do so by typing `ssh [username]@ieng6.ucsd.edu`. To find out your username, go to the [UCSD Account Lookup page](https://sdacs.ucsd.edu/~icc/index.php) and log in. You should see under additional accounts the names of your accounts. If you are in CSE 15L, your account username should start with "cs15l." Use this username to log in using ssh.  
![Placeholder](/cse15l-lab-reports/assets/images/img04-username)  
You will probably have to type in your UCSD account password to log in. It is possible that you may have to change your password to activate your account, which you can also do through the UCSD Account Lookup tool. 
## Trying Some Commands
Here are some commands to try:
* `cd [path]` (Change Directory. To backtrack, type cse15l-lab-reports)
* `ls` (LiSt files in output)
* `pwd` (prints the Present Working Directory, or the directory you're currently opening, to output)
* `touch [filename]` (make a file)
* `echo [option]` (ECHO what you typed as output)
* `mkdir [name]` (make directory, or make folder)
* `rm [name]` (ReMove file or empty directory)
* `cp [name] \[destination\]` (CoPy file to destination)

What's interesting is that these commands don't work by default on Windows. The Windows command prompt and Powershell uses a different set of commands. The reason that you are able to use these commands (if you have a windows computer) is because you are actually working on a Linux machine through your remote connection, and Linux shells (and by extension, Mac shells) have access to these commands. There are ways to make Windows mimic Linux commands, however, which will probably be explained later in the course.
## Moving Files with scp
Secure Contain Protect lmao  
`scp` essentially allows you to copy files from your computer to a server. The command goes  
``` 
scp [file] [username]@ieng6.ucsd.edu]:[destination-path]
```  
[destination-path] should be replaced with the path of the directory that you want to place your file in. The "~" (tilda) character represents the home directory (and can be used as part of a path, as in `~\mydirectory`). You can also type a new name for the copied file as part of the `[destination-path]` (e.g. `~\mydirectory\newfilename`). 
You will also have to type in your password. to use this service. 
## Setting an SSH Key
The more complex your password, the more annoying it is to have to type it in. Wouldn't it be nice if the server could automatically detect that the computer you're logging in with is _yours,_ and automatically let you in? While apparently not the most secure method of logging in (according to the CSE 15L teacher), it is possible.  
Open a terminal on your client (nothing needs to be done on the server yet). Run `ssh-keygen`. Use the default keygen location by pressing Enter/Return when prompted for a location to save the generated key (of course, you could type in whatever location want if you know what you're doing). For convenience, do not enter a password, or enter a simpler one than your default UCSD account password. In your home directory (usually C:/Users/username) you should now see a .ssh file. Within it should be a file called id\_rsa.pub, which is the "public" key generated by `ssh-keygen`. We will want to copy this file to the server, but to a particular location.  
Log into the server and create a directory called .ssh. Once it is created, you may not see it using `ls` because the period in front of the file name makes labels it as "hidden." However, you will be able to view it using `ls -a`.  
Log out. go to the .ssh folder on your computer and run scp on id\_rsa.pub, copying it to `~\.ssh\authorized_keys`. Since `authorized_keys` is not a directory in .ssh, it will be generated as a file.  
You're done! from now on you can log onto the server without a password. 
## Optimizing Remote Running
Generally, compiling and running java files on a remote server utilizes similar commands in similar order. You can speed up the remote running workflow by copying those commands to a file and pasting them whenever you need to. A better way to speed up the process is to create a batch file (at least, on Windows) that does the work for you simply by running the file. We will probably end up learning about this later. 
