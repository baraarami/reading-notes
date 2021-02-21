 # Git intro 

### In order to explain Git, we have to first explain various aspects of Version Control.

Version Control is a system that allows you to revisit various versions of a file or set of files by recording changes. Through version control, one can revert a file or project to a previous version, track modifications and modifying individuals, and compare changes. By utilizing a Version Control System (VCS), mistakes with files can easily be rectified.
there is three type of it :
#### 1. Local Version Control :
Many years ago, programmers created Local Version Control systems. A Local VCS entails one database on your hard disk that stores changes to files.

#### 2. Centralized Version Control :
The need for collaboration within a developer team on a single file or set of files led to the advent of the Centralized Version Control System (CVCS). This system entails a single server storing all changes and file versions, which can be accessed by various clients. This streamlined the collaboration process (by eliminating the need to involve all local databases), allowed programmers to have more knowledge of team members’ activities with certain files, and gave administrators much more control over divvying up revision privileges.

#### 3. Distributed Version Control :
A Distributed Version Control systems (DVCS) addresses the major vulnerability of the CVS: the server as a single point of failure. If a CVS goes down, collaborators cannot work with each other on a file or save changes and new versions. Also, in the event of corruption of a central database’s hard disk — with the absence of backups — all work will be lost, except for any portions on local machines.
To prevent this type of catastrophic loss, a DVCS allows clients to create mirrored repositories. These data backups can be easily be placed on the server to replace any lost information.
Because the DVCS allows for multiple mirrored repositories, programmers working in teams can collaborate with each other in various ways to complete a joint project, which enables the use of various simultaneous workflows.

# Getting Started
first of all you have to **download Git** , If you already have Git on your computer, you should make sure you have the latest version.

# Graphical Clients
Git includes inherent Graphical User Interface (GUI) tools. However, users can also utilize third-party tools created for particular platforms.

GUI Clients
You can access a variety of GUI clients for Mac, Windows, and Linux via the following link:

[GUI downloding tolls](https://git-scm.com/downloads/guis) .

# Initial Customization
After making sure Git has been installed, you should perform some customization steps, which should only need to be completed once on any machine.
##### *Configuration of Variables* : An inherent Git tool called git config allows the setting of configuration variables that control aspects of Git’s operation and look.
##### *Identity Setting* :Type the following into Terminal or Command Line:
git config --global user.name "Jane Smith"
git config --global user.email "example@email.com"
To confirm that you have the correct settings, enter the following command:
git config --global user.name (should return Jane Smith)
git config --global user.email (should return example@email.com)
##### *Default Text Editor* : $ git config --global core.editor emacs.
##### *Check Settings* : git config --list .
##### *Getting Help* : git help command , git command --help ,man git-command .


# **Setting up a Git Repository**

### *Importing* 
To import an existing project or directory into Git, follow these steps using the Terminal or Command Line:
Switch to the target project’s directory
Example: 

1. $ cd test (cd = change directory)
Use the git init command
2. $ git init
3. To start tracking these repository files, perform an initial commit by typing the following:
* $ git add *.c
* $ git add LICENSE
* $ git commit -m “any message here”

### *Cloning*
You can also create a copy of an existing Git repository from a particular server by using the clone command with a repository’s URL:
$ git clone https://github.com/test

### *The Life Cycle of File Status*
1. After you edit a file, Git flags it as modified because of changes made after the previous commit.
2. You stage the modified file.
3. Then, you commit staged changes.
![lfofs](https://blog.udemy.com/wp-content/uploads/2015/08/image006.png)


### *Check File Status* 
To determine the state of files, utilize the git status command:
$ git status

### *Tracking and Staging a New File*
##### Single File
Track one file only by using the following format:

git add filename

##### All Files
Track all files in a repository by using the following command:
$ git add *


### *Committing a File*
After staging one or multiple files, you should commit the changes and record what you did within the commit message:
$ git commit -m “made change x,y,z”. 


### *Committing All Changes*
$ git commit -a

### *Pushing Changes*
$ git push origin master

### *Stashing Changes*
When you are not ready to commit changes but do not want to lose them either, git stash is a great option. This command temporarily removes changes and hides them, giving you a clean working directory. When you are ready to continue working on the changes, simply use the git stash apply command to retrieve the hidden changes.








