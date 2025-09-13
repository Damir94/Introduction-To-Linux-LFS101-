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

**GUI Startup**
 - When you install a desktop environment, the display manager starts at the end of the boot process. It is responsible for starting the graphics system, logging in the user, and starting the user’s desktop environment. You can often select from a choice of desktop environments when logging in to the system. The default display manager for GNOME is called gdm. Another popular display manager is kdm, associated with KDE.

**GNOME Desktop Environment**
 -  GNOME is a popular desktop environment with an easy-to-use graphical user interface. It is bundled as the default desktop environment for most Linux distributions, including Red Hat Enterprise Linux (RHEL), Fedora, CentOS, SUSE Linux Enterprise, Ubuntu, and Debian. GNOME has menu-based navigation and is sometimes an easy transition to accomplish for Windows users. However, the look and feel can be quite different across distributions, even if they are all using GNOME.
 -  Another common desktop environment very important in the history of Linux and also widely used is KDE, which has often been used in conjunction with SUSE and openSUSE. Other alternatives for a desktop environment include Unity (present on older Ubuntu but still based on GNOME), XFCE, and LXDE. As previously mentioned, most desktop environments follow a similar structure to GNOME, and we will restrict ourselves mostly to it to keep things less complex.

**Graphical Desktop Background**
 - Each Linux distribution comes with its own set of desktop backgrounds. You can change the default by choosing a new wallpaper or selecting a custom picture to be set as the desktop background. If you do not want to use an image as the background, you can select a color to be displayed on the desktop instead. 

