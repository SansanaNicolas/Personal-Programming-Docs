# Windows commands

## Basic commands

With these commands you can access different directories and obtain information about the folders you are in. You can also create and delete folders and even files directly.

### CD
One of the most essential Windows console commands. It is used to change directories, using the formula *cd < DirectoryPath >* to go to the specific directory or folder that you tell it to, or *cd..* (with a colon) to exit a folder and go to the top level or folder where was staying.

### DIR
The command lists the contents of the directory or folder where you are, showing all the subfolders or files it contains. With this command you will be able to know if the file you are looking for is there or to which subfolder to navigate.

### TREE *FOLDER
It shows you the directory tree of a specific folder that you tell it

### CLS
Cleans the Windows console window, erasing everything that has been written in it, both your commands and the responses from the console itself. Everything will remain as if you had just opened it again.

### EXIT
Close the windows console

### HELP
It shows all the commands that are available, putting in each one a brief description in english.

### COPY *FILE DESTINY
Copy one or more files to the address of your choice.

### ROBOCOPY
An improved function that is faster and more efficient, and that allows actions such as canceling or resuming the copy. It also shows a progress indicator, which makes it a good alternative for copying large files.

### MOVE *FILE DESTINY
Moves the specific file you want from the place or folder where it is to another address that you tell it. It's like copying, but without leaving the file in its original location.

### DEL *FILE/ FOLDER
Delete the file or folder that you indicate.

### RENAME FILE
It allows you to change the name of the file that you consider appropiate, and even including its extension you can also change it.

### MD *FOLDERNAME
Create a folder with the name that you assign it in the direction in which you are at that moment.

### TYPE FILE.EXTENSION
It allows you to create a file from the command windows itself. This means that you are not only going to create a file, but you can also write a text you want inside it.

### FORMAT
Formate a drive.


## Basic diagnostic commands.

### SYSTEM INFO
It helps you to obtain information about the computer or system in which you are working. It gives you data such as the name of the system, the processor, the RAM memory, the motherboard or the internal storage you have.

### CHKDSK
When something goes wrong, this is usually one of the first commands to resort to. it performs a surface scan of the hard drive to detect failures such as possible bad sectors, and also checks the logical structure of the file system and repairs any errors (missing files, meaningless names, inaccessible folders, etc.).

### IPCONFIG
It shows you your connection information, including your IP address, subnet mask or default gateway.

### NETSTAT
Analyze and display the statistics of the protocol and the TCP/IP connections in use by your devices. With this, you can solve possible connection problems by looking at the status of the ports and connections of your equipment.

### TRACERT HOSTDIRECTION
It helps you to know the path that your connection follows until it reaches the host that you indicate. For example, typing TRACERT www.tesla.com pod

### GETMAC
This command displays the MAC address of your computer.

### VER
VER stands for version, and when you type it into the console it returns the exact numerical version of your operating system. perfect for when you're waiting for updates or want to check if a certain feature is available.

### CONTROL PANEL
A command that serves as a shortcut, and that opens the Windows Control Panel directly without you having to search for it.

### TIME
This command shows you the exact time that your computer has.

### DRIVERQUERY
It shows you the complete list of all the drivers that you have installed on your computer, with its module name, full name and the type of driver it is.

### TASKLIST
It shows you the complete list of all the processes you have running on your system, as well as the amount of memory each of them is using. Like when you go into the task manager, this allows you to find processes that shouldn't be there or that may have hung.

### TASKKILL /PID PROCESSIDNUMBER
In the list above, each process is assigned a PID or Process Identifier Number. Well, with this command you can close the process whose number you have indicated.

### SFC
Examines the integrity of all files on your system and replaces any found to be corrupted using system cached copies. To be able to use this command you have to have run the Command Prompt as an administrator, since it needs those permissions.

### CLEANMGR
When you type it, a pop-up window will appear asking you to select a drive. What you will have done is launch the windows application to free up space.

### WINSAT FORMAL
The Windows console runs a complete benchmark that analyzes the performance of the computer and all its components. This command, WINSAT, can also be accompanied by other last names beyond FORMAL such as: CPUFORMAL to measure only CPU performance, MEMFORMAL for RAM, GRAPHICSFORMAL for graphics card or DISKFORMAL for storage units.

### DEFRAG
Start the defragmentation of the hard disk that you indicate. Just like the native app that Windows has for it.

### DISKPART
Type this command adding the LIST DISK or LIST VOLUME attributes to obtain a list of disks or volumes on the computer with this function to manage partitions and hard disks.

### SHUTDOWN
It is used to shutdown the computer directly from the Windows command console. You can add the "-s -t" TimeInSeconds attribute to it to schedule the shutdown or simply type SHUTDOWN -R to restart the computer.

### LOGOFF
Close the session of the user with whom you are accessing the computer, while keeping the computer on.
