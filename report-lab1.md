UCSD CSE 15L Lab 1 Report: How to Remotely Access UCSD Servers
=================================================
## Why this Article?
This article was written as part of an assignment for UCSD's CSE 15L class. However, I also intend for this to be a simple guide for myself and others about how I can run the command line on a server.  

## Installing VS Code
As I already had VS Code installed long before the assignment even began, this will be a recount of how I probably would have done it if it wasn't installed.  
First, I would go to [Link]https://code.visualstudio.com/ (or just look up vscode on Google). I would see a big blue button in the center of the screen saying "Download for Windows," which I would click (Mac users, I would presume would see "Download for Mac"). The setup wizard should be installed when I do.  
I would work through the setup wizard. Under "Other," I would check all of the options like so:  
![Placeholder](https://via.placeholder.com/150)  
This is because I actually like to use code to edit my files. It's somehow aestheically pleasing to use, compared to things like Notepad++. Checking all items allows me to access VS Code more easily for different file types.  
Then I would click Install, and I should be able to open the VS Code application, whether it be via Desktop shortcut or Start Menu shortcut.  
## Remotely Connecting
We will start by making sure SSH is actually installed on our computer. The instructions can be found at [here](https://google.com); I will summarize the steps for Windows here. First, open your computer's Settings and select Apps and Features (or open it from the Start Menu). There is an Apps & Features section under the Apps & Features Page; right under the header, there is an _Optional Features_ link you should click. Search the _Installed Features_ for OpenSSH and check if you have the client installed. If not, click _Add a Feature,_ search and select _OpenSSH Client_, and install it.  
I usually use an external terminal to remotely connect to a server. However, CSE 15L recommends that you open a Terminal within VS Code, which you can do by selecting View -> Terminal, or by pressing CTRL+``. Once you have a terminal open, our goal is to log into your account on the ieng6 server (essentially a folder that you have permission to use on a remote computer). You can do so by typing `ssh username`. To find out your username,  
## Trying Some Commands
Here are some commands to try:
*cd [path] (Change Directory. To backtrack, type ..)
*ls (LiSt files in output)
*pwd (prints the Present Working Directory, or the directory you're currently opening, to output)
*touch (make a file)
*echo [option] (ECHO what you typed as output)
*mkdir [name] (make directory, or make folder)
*rm [name] (ReMove file or empty directory)
*cp [name] [destination] (CoPy file to destination)

What's interesting is that these commands don't work by default on Windows. The Windows command prompt and Powershell uses a different set of commands. The reason that you are able to use these commands (if you have a windows computer) is because you are actually working on a Linux machine through your remote connection, and Linux shells (and by extension, Mac shells) have access to these commands. There are ways to make Windows mimic Linux commands, however, which will probably be explained later in the course.
## Moving Files with scp
Secure Contain Protect lmao  

## Setting an SSH Key
The more complex your password, the more annoying it is to have to type it in. Wouldn't it be nice if the server could automatically detect that the computer you're logging in with is _yours,_ and automatically let you in? While apparently not the most secure method of logging in (according to the CSE 15L teacher), it is possible.  
## Optimizing Remote Running
Generally, compiling and running java files on a remote server utilizes similar commands in similar order. You can speed up the remote running workflow by copying those commands to a file and pasting them whenever you need to.  
