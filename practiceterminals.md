# Practice in the Terminal

### The Command Line
Terminal (Command Line) is an interface to a system interacts with text 

##### there is not just one way to enter the terminal, but all ways are easy depends on your system:
- *for Mac* : Applications - Utilities you will find your terminal there, other way is:  'command + space'  which shows a Spotlight to start typing
- *for Linux* : Applications -> System or Applications -> Utilities or 'right-click' on the desktop and select 'Open in terminal'
- *for windows* : an SSH client is needed, Putty is a good choice.

- after open the terminal just start typing your commands.

-----------------------------------------------------------------------------------

#### Basic Navigation 
**here is a prief steps to learn how to move between Linux System, you should understand those in order to deal and interact with system.**

#### Commands To learn :
 
 - *Print Working Directory* : it wrote as *pwd*, its function is to print the directory that your in.

 > └─ $~  pwd

 > **manar: path:** /home/manar/reading-notes



 - *list all in current directory*: the command *ls* used to list all files and folders in the current directory.

 > └─ $~  ls

> **manar: path:**   Movies-Library         


- *Change Directories* : the command cd used to move to another directory
> └─ $~  cd folder-name

> **manar: path:** /home/manar/demo | 2 files | size 56Kb 

**don't  forgit to press *Tab* to complete your writing** 

-----------------------------------------------------------------------------------
#### More About Files
**Every thing in Linux considered as a File, (file,directory, your keyboard are files)**
 when we specify a file or directory in command line it is actually *path*

 To obtain information what your file (file or directory is )
> file

 in command Line we can name the file as wordes in space between them, but there is syntax to do that:
 > cd 'my photos'
        
>/home/ryan/Documents/my Photos

or 
>cd my\ Photos

>/home/ryan/Documents/my Photos

*To hide a file in Linux just put '.' before its name
> .photo  // the photo file is hidden

To list your directory contents including hidden files 
>ls -a

 linux is *case sensiteve* be careful when typing your files and directories names.

------------------------------------------------------------------------------------
#### Manual Pages 
In command line there are resources to inform us about all things here *use Manual pages *
they explain each command in the system

>man ls

to explain the *ls* command and what it do and example for you 

------------------------------------------------------------------------------------

#### File Manipulation
Making a new Directory
> mkdir directory-name

Remove or delete  Directory
>rmdir directory-name

Create a blank file
>touch file-name

Move a file or directory
>mv  fileordir-name  source  destination

 Delete a file
 > rm file-name

-------------------------------------------------------------------------------------

#### Cheat Sheet

explains for us how to deal with a directory or a file and tell us the steps to do every thing we need in that project or any directory and the important commands to help us understand it.