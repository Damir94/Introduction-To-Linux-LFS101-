# Linux Documentation Sources
 - Whether you are an inexperienced user or a veteran, you will not always know (or remember) the proper use of various programs and utilities: what command to use, what options should it take, what results to expect, etc.
   Thus, you will probably need to get help from consult help documentation regularly. Because Linux-based systems draw from a large variety of sources, there are numerous reservoirs of documentation and ways of getting help.
   Distributors consolidate this material and present it in a comprehensive and easy-to-use manner; this is an important function of any Linux distribution.

<img width="775" height="678" alt="Screenshot 2025-09-17 at 12 31 53 PM" src="https://github.com/user-attachments/assets/83ddd239-0174-4a88-939d-af4d7755101b" />

*man*
 - The man program searches, formats, and displays the information contained in the man page system. Because many topics have copious amounts of relevant information, output is piped through a pager program (such as less) to be viewed one page at a time. At the same time, the information is formatted for a good visual display.
 - A given topic may have multiple pages associated with it and there is a default order determining which one is displayed when no options or section number is specified. To list all pages on the topic, use the -f option. To list all pages that discuss a specific topic (even if the specified subject is not present in the name), use the –k option.
 - man –f generates the same result as typing whatis.
 - man –k generates the same result as typing apropos.
 - The default order is specified in /etc/man_db.conf and is roughly (but not exactly) in ascending numerical order by section.

# GNU Info
 - Typing info with no arguments in a terminal window displays an index of available topics. You can browse through the topic list using the regular movement keys: arrows, Page Up, and Page Down.
 - You can view help for a particular topic by typing info <topic name>. The system then searches for the topic in all available info files.
 - Some useful keys are: q to quit, h for help, and Enter to select a menu item.

# info Page Structure
 - The topic which you view in an info page is called a node. The table lists the basic keystrokes for moving between nodes.
 - Nodes are essentially sections and subsections in the documentation. You can move between nodes or view each node sequentially. Each node may contain menus and linked subtopics, or items.
 - Items function like browser links and are identified by an asterisk (*) at the beginning of the item name. Named items (outside a menu) are identified with double-colons (::) at the end of the item name. Items can refer to other nodes within the file or to other files.

<img width="696" height="204" alt="Screenshot 2025-09-17 at 12 37 13 PM" src="https://github.com/user-attachments/assets/26cb0207-2ce1-4a74-ac95-580ccbe43759" />

# The --help Option
 - Another important source of Linux documentation is use of the --help option.
 - Most commands have an available short description which can be viewed using the --help or the -h option along with the command or application. For example, to learn more about the man command, you can type:
 - $ man --help
 - The --help option is useful as a quick reference and it displays information faster than the man or info pages.

# The help Command
 - When run within a bash command shell, some popular commands (such as echo and cd) actually run especially built-in bash versions of the commands rather than the usual binaries found on the file system, say under /bin or /usr/bin.
 - It is more efficient to do so as execution is faster because fewer resources are used (we will discuss command shells later). One should note that there can be some (usually small) differences in the two versions of the command.
   




