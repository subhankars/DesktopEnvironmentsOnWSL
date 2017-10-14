# DesktopEnvironmentsOnWSL
A guide to successfully setting up Bash on Ubuntu on Windows to run a full desktop environment such as Unity on Windows 10.

"The Windows Subsystem for Linux lets developers run Linux environments -- including most command-line tools, utilities, and applications - directly on Windows, unmodified, without the overhead of a virtual machine." - Microsoft Developer Network

The Windows Subsystem for Linux is meant for command-line utilities and running the occasional linux program. It runs a ubuntu-based Bash shell atop the subsystem. There are limitations though: It won't work with server software and it'll crash often and just spam errors. But we can make it work to run an entire desktop environment!

What we want to do first is install WSL if you have not done so. Some requirements:
- Windows 10 Anniversary Update or greater
- Developer Mode: head to Update & Security > For Developers. Activate the “Developer Mode” switch here to enable Developer Mode.
- Have it enabled: Next, open the Control Panel, click “Programs,” and click “Turn Windows Features On or Off” under Programs and Features. Enable the “Windows Subsystem for Linux (Beta)” option in the list here and click “OK.”

Run <code>lxrun /install</code> or <code>bash</code> to download the application from the Windows Store.

![Install Image](/images/bashshellinstall.png?raw=true)

Ubuntu should download, its File System should be extracted and it should prompt you to create a UNIX account.
Note: Ubuntu is very reliant on fast storage; It will be extremely useful to have an SSD because massive read/write will occur and many small files will be accessed simultaneously. Extracting file system and installing anything later on ubuntu will be much faster with a SSD. The maximum "extracting filesystem" should take is 45 minutes.

![Install Image](/images/new-user.png?raw=true)


Once you have created a new UNIX username and password we will need to update and upgrade the system. Run <code>sudo apt-get update && sudo apt-get upgrade</code>.
![Install Image](/images/new-user.png?raw=true)
![Install Image](/images/new-user.png?raw=true)

