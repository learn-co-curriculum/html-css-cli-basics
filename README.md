## System Commands

## Overview

Becoming proficient with the CLI (Command Line Interface) is essential to speed up your workflow and allowing you direct access to your computer's file system without needing to use the mouse or a GUI (Graphical User Interface) like Finder. The CLI will also give you super powers like accessing hidden files and folders, connecting to remote servers, and managing versions of your code using `git`. We will be exploring the most high-frequency BASH commands. For more information on the creation and history of Unix and BASH (Born Again Shell) see the [resources](#resources) at the bottom of this lesson.

## Objectives
By the end of this lesson, you'll be able to

1. Print the path to your current working directory.
2. List files and folders in a directory.
3. Change directories.
4. Make new directories.
5. Create new files.
6. Remove files and folders.
7. Open files.
8. Copy files.
9. Rename and move files.

## Command Line Interface Basics

Watch the video below if you are unfamiliar with the command line. It will walk you through basic commands that we will use daily in this course. It will also be helpful later when you start setting up git.

*Note: When practicing the commands, use the terminal in your Learn IDE instead of the Terminal on your computer. The instructions in the video will prompt you to use the Terminal on your computer, but USE the Learn IDE instead. When you open the IDE, the Terminal area is at the bottom half of the IDE interface. All the commands that we cover will work in your IDE.*

<iframe width="640" height="480" src="//www.youtube-nocookie.com/embed/s5S_2BdrMJE?rel=0" frameborder="0" allowfullscreen></iframe>


### Determining Location Within the Filesystem

Once your IDE loads you will be staring at a prompt. This is where we can type in commands to interact with our computer. The first thing we want to know is where the heck we are among all the possible folder locations in our filesystem. Type the command `pwd` which stands for "print working directory". This will display your location on your computer. For example, this command might print something like `/home/JonGrover/code` (except it would probably show your username instead of "JonGrover"). This shows us the absolute path to the current directory we are in in relationship to the root of the computer. What is a directory? A directory is merely a folder location. In the example above, `/` is the root of our system all other files and folders are contained within `/`. From there, we can find the `home/` directory, and then inside of that we are in the `JonGrover/` directory. Going one level deeper, we're in the `code/` directory. So our total path is `/home/JonGrover/code`. Now we will never be lost. Think of your current working directory like an address to your current place.

### List Contents of Current Directory

If we would like to see what files and folders exist within our current location we can use the `ls` list command. This will display any files or folders at our current location. Adding flags (options) such as `ls -a` (`-a` standing for "all") will list including all hidden files as well. We can combine flags such as `ls -la` this will list all files ( including hidden files) in a more detailed format.

### Moving Through the File System

You'll also probably want to be able to move about the file system by changing your location from one to another. To do so, we use the `cd` command which stands for change directory. This command accepts as an argument the location you wish to change to, e.g. `cd foldername`. Let's say we had a folder called `labs` that was right inside our current location. Then we could type `cd labs` to move into that folder. If we wanted to leave a folder and go up to the parent folder we were in previously we can type `cd ..`. Here the ".." represents the location of the parent folder of the one you are currently in.

### Auto-Completion

Pressing the tab key will auto-complete the names of files and folders. For example if you wanted to change directory into the `labs` folder you could type `cd l` then hit the tab key which should complete the name as `cd labs/`. Then you can press the return key to execute the command. If there are multiple files or folders with the same characters you might need to type out a little more of the filename to get it to work. If there is more than one possible file with the same starting characters, hitting tab twice will display a list of possible files or folders that you might be refering to. Simply finish typing a few more of the characters and hit tab again to auto-complete the rest.

### Creating Directories

Another highly used command satisifies the ability to be able to create new directories (folders). To do so you use the command `mkdir` (meaning "make directory") followed by the name of the directory such as `mkdir foldername`. For example if you wanted to create a folder called "my-awesome-project" you would type: `mkdir my-awesome-project`.

### Naming Conventions

It is worth noting that we didn't use any spaces in the filename from the example above. In fact space, will read as the creation of separate directories names in the case of `mkdir my awesome project`. For this reason we always use hyphens `-` or underscores `_` in place of spaces in file and directory names. (You might occasionally see camel-cased names, such as `myAwesomeProject`.) If you absolutely insist on using spaces in filenames you can use the escape character `\` in front of any spaces such as: `mkdir my\ awesome\ project`. It is a best practice however to keep it simple and clean by using `-`, or `_`. Also pick a convention and stick with it. I like hyphens, so I named my folder: `mkdir my-awesome-project`.

### Creating Files

Another high-use command is the "touch" command for creating files. To remember this one, think of Michelangelo's painting [_The Creation of Adam_](https://en.wikipedia.org/wiki/The_Creation_of_Adam). This famous work shows God outstretching his arm from the heavens and with his fingertip he creates the life of Adam. This command is as follows: "touch" followed by the file name or names such as: `touch adam` or `touch adam eve`.

Previously we created a folder called "my-awesome-project", let's move into that folder `cd my-awesome-project` and create a new file `touch index.html`. Now if we type `ls` we will see our new file `index.html` exists in the current directory.

### Opening

To open a file in its default program we use the "open" command followed by the "filename". so if we wanted to open our index file in the browser we would type: `open index.html`. The open command accepts as its argument the relative path to the file you wish to open. Based on the file extension being ".html" the computer knew to open this particular file in a web browser. If the file extension had been something else like ".txt" it would have opened in a text editor instead.

This `index.html` file is currently empty (there is no code yet) so it displays a blank window in the browser. Go ahead and close this browser window and go back into the terminal in the Learn IDE.

### Removing

A powerful command that you should not take lightly is `rm`, which stands for "remove". This command accepts as its argument the relative path to the file you wish to remove. For example if we wanted to remove our newly created `index.html` file we would type: `rm index.html`. Now when we run the `ls` list command we can see the index file is gone.

Let's `cd ..` to change directory back into our parent folder. Now we will practice removing our "my-awesome-project" folder.

To remove directories we must include the "-r" flag that tells the computer to recursively remove any sub-files or sub-folders within the directory we are removing. The `-f` flag means force which will tell the computer not to ask us permission but to forcefully remove all content within the specified directory. Please note this command is powerful as mentioned prior as it removes the directory you type in as well as all the content within it. This means you could easily delete large portions of your system or the entire system itself. "With great power comes great responsibility"... or something... anyway, this means it is important to carefully make sure when you use the `rm` command to be extra attentive to what files and directories you specify. Once removed you can't get them back; it is in other words **permanent**!

To remove our "my-awesome-project" folder we type: `rm -rf my-awesome-project`. After typing `ls` list command you will note that the "my-awesome-project" folder is now gone.

### Copying

To demonstrate how to copy (duplicate) files and directories let's first create some fresh content. Start by typing `mkdir another-awesome-project`. Then navigate into that folder `cd another-awesome-project`. Then create a new index file `touch index.html`.

Now let's make a copy of our index page. To make a copy we use the `cp` command followed by two arguments the first being the relative path of the file to be copied and the second argument is the relative path of where you would like the file to be copied to. For example if we wanted to simply copy the index file into the same folder we are in now we would type `cp index.html indexcopy.html`. Notice that using a keyboard space indicates a separation of one argument to the next.

### Moving and Renaming

The `mv` command allows us to move files, rename them, or both simultaneously. Let's say we wanted to move our indexcopy.html file into the parent folder and also rename it to index3.html. We can do so by using the mv command. `mv indexcopy.html index3.html`. If however you wanted to keep the name the same and only move the file you could just specify only the relative path of the folder location: `mv indexcopy.html ../`. Now to prove our file has really been moved and renamed we can move into the parent folder `cd ..`. Then `ls` to list out all the files and folders. Here we will see our file `index3.html`.

## Summary

- `pwd` prints the current location you are on your system.
- `ls` lists files and folders in your current directory.
- `cd` allows you to chage directories.
- `mkdir` creates new directories.
- `touch` creates new files.
- `rm` removes files and `rm -rf` removes directories.
- `open` allows you to open files
- `cp` copies files from one location to another.
- `mv` renames and moves files from one location to another.

## Resources

- [ss64 - Mac OSX CLI Commands](http://ss64.com/osx/)
- [Wikipedia - Unix](https://en.wikipedia.org/wiki/Unix)
- [Wikipedia - BASH (Unix Shell)](https://en.wikipedia.org/wiki/Bash_(Unix_shell))

<p class='util--hide'>View <a href='https://learn.co/lessons/html-css-cli-basics'>HTML CSS CLI Basics</a> on Learn.co and start learning to code for free.</p>
