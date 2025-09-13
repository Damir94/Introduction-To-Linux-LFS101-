**Learning Objectives**

By the end of this chapter, you should be able to:

 - Manage graphical interface sessions.
 - Perform basic operations using the graphical interface.
 - Change the graphical desktop to suit your needs.

**Graphical Desktop**
 - You can use either a Command Line Interface (CLI) or a Graphical User Interface (GUI) when using Linux. To work at the CLI, you have to remember which programs and commands are used to perform tasks, and how to quickly and accurately obtain more information about their use and options. On the other hand, using the GUI is often quick and easy. It allows you to interact with your system through graphical icons and screens. For repetitive tasks, the CLI is often more efficient, while the GUI is easier to navigate if you do not remember all the details or do something only rarely.

 - We will learn how to manage sessions using the GUI for the three Linux distribution families that we cover the most in this course: Red Hat (CentOS, Fedora), SUSE (openSUSE), 
and Debian (Ubuntu, Mint). 
Since we are using the GNOME-based variant of openSUSE rather than the KDE-based one, all are actually quite similar. If you are using KDE (or other Linux desktops such as XFCE), 
your experience will vary somewhat from what is shown, 
but not in any intrinsically difficult way, as user interfaces have converged to certain well-known behaviors on modern operating systems. 
In subsequent sections of this course we will concentrate in great detail on the command line interface, which is pretty much the same on all distributions.

**X Window System**


 - Loading the graphical desktop is one of the final steps in the boot process of a Linux desktop. Historically, this was known as the X Windows System, often just called X.

 - A service called the Display Manager keeps track of the displays being provided and loads the X server (so-called, because it provides graphical services to applications, sometimes called X clients). The display manager also handles graphical logins and starts the appropriate desktop environment after a user logs in.

 - X is rather old software; it dates back to the mid-1980s and, as such, has certain deficiencies on modern systems (for example, with security), as it has been stretched rather far from its original purposes. A newer system, known as Wayland, is gradually superseding it and is the default display system for Fedora, RHEL, and other recent distributions.  For the most part, it looks just like X to the user, although under the hood it is quite different.

<img width="1011" height="367" alt="Screenshot 2025-09-13 at 1 11 06 PM" src="https://github.com/user-attachments/assets/7d1c0e52-c635-489d-9f82-8696add88801" />

**More About the Graphical Desktop**

 - A desktop environment consists of a session manager, which starts and maintains the components of the graphical session, and the window manager, which controls the placement and movement of windows, window title-bars, and controls.
 - Although these can be mixed, generally a set of utilities, session manager, and window manager are used together as a unit, and together provide a seamless desktop environment.
 - If the display manager is not started by default in the default runlevel, you can start the graphical desktop different way, after logging on to a text-mode console, by running startx from the command line. Or, you can start the display manager (gdm, kdm, xdm, etc.) manually from the command line. This differs from running startx as the display managers will project a sign in screen. We discuss them next.

<img width="1021" height="387" alt="Screenshot 2025-09-13 at 1 14 09 PM" src="https://github.com/user-attachments/assets/4825127d-f257-4c48-bb44-b56a409d64af" />

