*Some Basic Utilities*

There are some basic command line utilities that are used constantly, and it would be impossible to proceed further without using some of them in simple form before we discuss them in more detail. 
A short list has to include:
 - cat: used to type out a file (or combine files).
 - head: used to show the first few lines of a file.
 - tail: used to show the last few lines of a file.
 - man: used to view documentation.

*The Command Line*
Most input lines entered at the shell prompt have three basic elements:
 - Command
 - Options
 - Arguments

*sudo*
 - All the demonstrations created have a user configured with sudo capabilities to provide the user with administrative (admin) privileges when required. 
   sudo allows users to run programs using the security privileges of another user, generally root (superuser).
 - On your own systems, you may need to set up and enable sudo to work correctly. To do this, you need to follow some steps that we will discuss but not explain in much detail right now.
Many distributions, including Ubuntu, configure sudo for you during installation. On other Linux distributions, you will need to configure sudo to work properly after the initial installation.
We will return to discussing the differences and use of both su and sudo later in our security-focused section.

*Steps for Setting Up and Running sudo*
If your system does not already have sudo set up and enabled, you need to do the following steps:
 - You will need to make modifications as the administrative, or superuser, root. While sudo will become the preferred method of doing this,
   we do not have it set up yet, so we will need to use su instead. At the command line prompt, type su and press Enter.
   You will then be prompted for the root password, so enter it and press Enter. You will notice that nothing is printed; this is so others cannot see the password on the screen.
   You should end up with a different looking prompt, often ending with ‘#’. For example:
    - $ su Password:
 - Now, you need to create a configuration file to enable your user account to use sudo.
   Typically, this file is created in the /etc/sudoers.d/ directory with the name of the file the same as your username.
   For example, for this demo, let’s say your username is student.
   After doing step 1, you would then create the configuration file for student by doing this:
    - # echo "student ALL=(ALL) ALL" > /etc/sudoers.d/student
      
 - Finally, some Linux distributions will complain if you do not also change permissions on the file by doing:
    - *chmod 440 /etc/sudoers.d/student*
      
 - That should be it. For the rest of this course, if you use sudo you should be properly set up.
   When using sudo, by default you will be prompted to give a password (your own user password) at least the first time you do it within a specified time interval.
  It is possible (though very insecure) to configure sudo to not require a password or change the time window in which the password does not have to be repeated with every sudo command.

*Rebooting and Shutting Down*
 - The preferred method to shut down or reboot the system is to use the shutdown command. This sends a warning message, and then prevents further users from logging in. 
The init process will then control shutting down or rebooting the system. It is important to always shut down properly; failure to do so can result in damage to the system and/or loss of data.
The halt and poweroff commands issue shutdown -h to halt the system; reboot issues shutdown -r and causes the machine to reboot instead of just shutting down. Both rebooting and shutting down from the command line requires superuser (root) access.
When administering a multi-user system, you have the option of notifying all users prior to shutdown, as in:
 - *$ sudo shutdown -h 10:00 "Shutting down for scheduled maintenance."*

*Locating Applications*
 - Depending on the specifics of your particular distribution's policy, programs and software packages can be installed in various directories. In general, executable programs and scripts should live in the /bin, /usr/bin, /sbin, /usr/sbin directories, or somewhere under /opt. They can also appear in /usr/local/bin and /usr/local/sbin, or in a directory in a user's account space, such as /home/student/bin.

One way to locate programs is to employ the which utility. For example, to find out exactly where the diff program resides on the filesystem:
 - *$ which diff*
   */usr/bin/diff*
   
If which does not find the program, whereis is a good alternative because it looks for packages in a broader range of system directories:
 - *$ whereis diff*
   *diff: /usr/bin/diff /usr/share/man/man1/diff.1.gz /usr/share/man/man1p/diff.1p.gz*

*Accessing Directories*
When you first log into a system or open a terminal, the default directory should be your home directory. You can see the exact location by typing echo $HOME. However, most Linux distributions open new graphical terminals in $HOME/Desktop instead.

<img width="1100" height="242" alt="Screenshot 2025-09-16 at 11 55 53 AM" src="https://github.com/user-attachments/assets/65f64589-bd98-4557-91ef-98f18656b76e" />

*Understanding Absolute and Relative Paths*

 - Absolute pathname - An absolute pathname begins with the root directory (/) and follows the tree, branch by branch, until it reaches the desired directory or file. Absolute paths always start with /.
 - Relative pathname - A relative pathname starts from the present working directory. Relative paths never start with /.

Multiple slashes (/) between directories and files are allowed, but all but one slash between elements in the pathname is ignored by the system. While ////usr//bin is valid, it is seen as just /usr/bin by the system. 
Most of the time, it is most convenient to use relative paths, which require less typing. Usually, you take advantage of the shortcuts provided by: . (present directory), .. (parent directory) and ~ (your home directory).
For example, suppose you are currently working in your home directory and wish to move to the /usr/bin directory. The following two ways will bring you to the same directory from your home directory:
 - *Absolute pathname method - $ cd /usr/bin*
 - *Relative pathname method - $ cd ../../usr/bin*
   
<img width="770" height="534" alt="Screenshot 2025-09-16 at 11 59 26 AM" src="https://github.com/user-attachments/assets/62910ff1-9fc9-4b78-9760-6b14164407e7" />

*Exploring the Filesystem*
 - Traversing up and down the filesystem tree can get tedious. The tree command is a good way to get a bird’s-eye view of the filesystem tree. Use tree -d to view just the directories and to suppress listing file names.

<img width="1170" height="262" alt="Screenshot 2025-09-16 at 12 00 24 PM" src="https://github.com/user-attachments/assets/3bad110e-16f0-439d-9fdb-05d86ab9c092" />

*Hard Links*
 - The ln utility is used to create hard links and (with the -s option) soft links, also known as symbolic links or symlinks. These two kinds of links are very useful in UNIX-based operating systems.
Suppose that file1 already exists. A hard link, called file2, is created with the command:
 - *$ ln file1 file2*
   
Note that two files now appear to exist. However, a closer inspection of the file listing shows that this is not quite true.
 - *$ ls -li file1 file2*

The -i option to ls prints out in the first column the inode number, which is a unique quantity for each file object. This field is the same for both of these files; what is really going on here is that it is only one file, but it has more than one name associated with it, as is indicated by the 2 that appears in the ls output. Thus, there was already another object linked to file1 before the command was executed.

<img width="638" height="143" alt="Screenshot 2025-09-16 at 12 03 07 PM" src="https://github.com/user-attachments/assets/5e9d8535-1a66-4354-a993-07098abe3c75" />

Hard links are very useful and they save space, but you have to be careful with their use, sometimes in subtle ways. For one thing, if you remove either file1 or file2 in the example, the inode object (and the remaining file name) will remain, which might be undesirable, as it may lead to subtle errors later if you recreate a file of that name.
If you edit one of the files, exactly what happens depends on your editor; most editors, including vi and gedit, will retain the link by default, but it is possible that modifying one of the names may break the link and result in the creation of two objects.

*Soft (Symbolic) Links*
- Soft (or Symbolic) links are created with the -s option, as in:
  - *$ ln -s file1 file3*
  - *$ ls -li file1 file3*
Notice file3 no longer appears to be a regular file, and it clearly points to file1 and has a different inode number.
<img width="670" height="242" alt="Screenshot 2025-09-16 at 12 09 36 PM" src="https://github.com/user-attachments/assets/e81de8f9-3cd0-4936-b099-5fd4c891a66b" />
Symbolic links take no extra space on the filesystem (unless their names are very long). They are extremely convenient, as they can easily be modified to point to different places. An easy way to create a shortcut from your home directory to long pathnames is to create a symbolic link.
Unlike hard links, soft links can point to objects even on different filesystems, partitions, and/or disks and other media, which may or may not be currently available or even exist. In the case where the link does not point to a currently available or existing object, you obtain a dangling link.

*Navigating Through Directory History (1)*
 - The cd command remembers where you were last, and lets you get back there with cd -. For remembering more than just the last directory visited, use pushd to change the directory instead of cd; this pushes your starting directory onto a list. Using popd will then send you back to those directories, walking in reverse order (the most recent directory will be the first one retrieved with popd). The list of directories is displayed with the dirs command.

<img width="587" height="265" alt="Screenshot 2025-09-16 at 12 11 13 PM" src="https://github.com/user-attachments/assets/c58f0fa6-efda-4141-be9e-53fb0270b1c2" />

*Viewing Files*

<img width="1101" height="368" alt="Screenshot 2025-09-16 at 12 12 17 PM" src="https://github.com/user-attachments/assets/ad88a0b2-8514-4b92-8ab1-11add6081e9e" />

*touch*
 - touch is often used to set or update the access, change, and modify times of files. By default, it resets a file's timestamp to match the current time.
 - However, you can also create an empty file using touch: *$ touch <filename>*
 - touch provides several useful options. For example, the -t option allows you to set the date and timestamp of the file to a specific value, as in: *$ touch -t 12091600 myfile*.
 - This sets the myfile file's timestamp to 4 p.m., December 9th (12 09 1600).

<img width="558" height="220" alt="Screenshot 2025-09-16 at 12 14 22 PM" src="https://github.com/user-attachments/assets/97160cb1-05e0-4125-8466-e99c1955f377" />

*mkdir and rmdir*
 - mkdir is used to create a directory:
    - *mkdir sampdir* - It creates a sample directory named sampdir under the current directory.
    - *mkdir /usr/sampdir* - It creates a sample directory called sampdir under /usr.
    - Removing a directory is done with rmdir. The directory must be empty or the command will fail. To remove a directory and all of its contents you have to do rm -rf.

 <img width="1920" height="1080" alt="Screenshot 2025-09-16 at 10 57 50 AM" src="https://github.com/user-attachments/assets/97317e7e-e900-4d5b-857a-bc3f671ac64f" />

*Moving, Renaming or Removing a File*
 - Note that mv does double duty, in that it can:
    - Simply rename a file
    - Move a file to another location, while possibly changing its name at the same time.
 - If you are not certain about removing files that match a pattern you supply, it is always good to run rm interactively (rm –i) to prompt before every removal.
   
<img width="1108" height="250" alt="Screenshot 2025-09-16 at 12 22 51 PM" src="https://github.com/user-attachments/assets/9e38a55e-2f80-466b-97f5-a7a03323f157" />

<img width="1112" height="208" alt="Screenshot 2025-09-16 at 12 24 32 PM" src="https://github.com/user-attachments/assets/5d39446a-cefb-4d42-ae01-3b444d43d97a" />

<img width="1146" height="573" alt="Screenshot 2025-09-16 at 12 25 18 PM" src="https://github.com/user-attachments/assets/d0a472b5-7875-403c-9bf2-0bbc1143c105" />

<img width="1156" height="644" alt="Screenshot 2025-09-16 at 12 25 53 PM" src="https://github.com/user-attachments/assets/b5a47c19-3ecf-4dc1-877f-1526443ac0c6" />

<img width="1149" height="776" alt="Screenshot 2025-09-16 at 12 26 21 PM" src="https://github.com/user-attachments/assets/916d62fe-7ae8-42f9-a85d-5333582d3110" />

<img width="1192" height="675" alt="Screenshot 2025-09-16 at 12 26 44 PM" src="https://github.com/user-attachments/assets/e8e2aa56-e74d-4583-9129-3eef8eacccf6" />

<img width="1138" height="397" alt="Screenshot 2025-09-16 at 12 27 20 PM" src="https://github.com/user-attachments/assets/f8b97f3b-c9d2-4691-8d32-330c0178d0af" />

<img width="1172" height="576" alt="Screenshot 2025-09-16 at 12 27 46 PM" src="https://github.com/user-attachments/assets/2b331cf5-17b2-45d6-8e29-abbf9a148b54" />

<img width="1132" height="337" alt="Screenshot 2025-09-16 at 12 28 25 PM" src="https://github.com/user-attachments/assets/42da243d-622a-42cb-bb84-bd25820b0a5e" />

<img width="1161" height="720" alt="Screenshot 2025-09-16 at 12 28 52 PM" src="https://github.com/user-attachments/assets/ae8be44d-c1e5-4578-9c97-a549bb6bb02c" />

<img width="1164" height="603" alt="Screenshot 2025-09-16 at 12 29 18 PM" src="https://github.com/user-attachments/assets/64c13ef5-06bb-48c2-96cc-4f0b3d011d4d" />

<img width="1163" height="577" alt="Screenshot 2025-09-16 at 12 29 41 PM" src="https://github.com/user-attachments/assets/da638842-7282-42df-a325-83cd8826c8c6" />

<img width="1152" height="367" alt="Screenshot 2025-09-16 at 12 30 15 PM" src="https://github.com/user-attachments/assets/d8e9837f-e34e-4b36-86db-071abb78d9c4" />

<img width="1135" height="744" alt="Screenshot 2025-09-16 at 12 30 39 PM" src="https://github.com/user-attachments/assets/681bf8f1-49f3-4b15-b391-1cd95d6f2b1e" />

<img width="1177" height="693" alt="Screenshot 2025-09-16 at 12 31 10 PM" src="https://github.com/user-attachments/assets/7d796ace-b03e-41b8-9626-42dbaf2bd34e" />

<img width="1201" height="593" alt="Screenshot 2025-09-16 at 12 31 30 PM" src="https://github.com/user-attachments/assets/26e71179-20dd-4b82-9ee1-3d399d98c04d" />




