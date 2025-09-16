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
    - #
 - Now, you need to create a configuration file to enable your user account to use sudo.
   Typically, this file is created in the /etc/sudoers.d/ directory with the name of the file the same as your username.
   For example, for this demo, let’s say your username is student.
   After doing step 1, you would then create the configuration file for student by doing this:
    - # echo "student ALL=(ALL) ALL" > /etc/sudoers.d/student
      
 - Finally, some Linux distributions will complain if you do not also change permissions on the file by doing:
    - # chmod 440 /etc/sudoers.d/student
      
 - That should be it. For the rest of this course, if you use sudo you should be properly set up.
   When using sudo, by default you will be prompted to give a password (your own user password) at least the first time you do it within a specified time interval.
  It is possible (though very insecure) to configure sudo to not require a password or change the time window in which the password does not have to be repeated with every sudo command.
