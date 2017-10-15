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


Once you have created a new UNIX username and password we will need to update and upgrade the system. Run <code>sudo apt-get update && sudo apt-get upgrade</code>. This is just because we only installed a bare "skin and bones" system, we will need to tidy things up a bit. This is neccessary for a good system.
![Install Image](/images/Capture.PNG?raw=true)
![Install Image](/images/Capture1.PNG?raw=true)

WSL does not have access to graphical aspects of Windows, which we will need to remedy. To do this we will need to install a compatible Xserver for windows. I recommend <code>VcXsrv</code> or <code>Xming</code>. I recommend VxXsrv because it is much more stable. Xming commonly crashes and freezes up, but VxXsrv is much more flexible. Download VcXsrv from the sourceforge site and install it.

![Install Image](/images/X.PNG?raw=true)

To launch VcXsrv, run Xlaunch, which is installed automatically with VcXsrv. Choose "One windows without titlebar" and set the Display number to 0. Don't chnage any of the rest, just leave it to the defaults. Click Next 3 times and click Finish.

![Install Image](/images/X-setup.PNG?raw=true)

After you finish, VcXsrv should start as a dark window without a panel. It should be more or less fullscreen. The Windows taskbar should still be visible. Now that we have installed and started a compatible Xserver, we need to tell WSL to use it for graphical access. Open bash on windows on ubuntu and run <code>sudo apt-get install x11-apps</code>. After this is complete, run <code>xeyes</code>. This should give an error that it cannot open display. This is correct. run this code: <code>export DISPLAY=:0.0</code>. This number is what we set in Xlaunch. After runing that, retry <code>xeyes</code>, and it <b>should</b> work.

![Install Image](/images/X-setupSuccess.PNG?raw=true)

Now, any graphical Linux program will display on Windows 10. Better still, if you're going to keep working with graphical Linux software on WSL, have WSL automatically ready itself for graphical programs by placing the command in Bash's configuration file: ".bashrc". An easy way to do this is to use the echo command to write it with the following shell command.

<code>echo "export DISPLAY=:0.0" >> ~/.bashrc</code>

Now you can run graphical linux programs without having to set the display manually. We will now install core components to make a desktop enironment function properly. We will have to install:
- <code>sudo apt-get install ubuntu-desktop</code>
- <code>sudo apt-get install unity</code>
- <code>sudo apt-get install compiz-core</code>
- <code>sudo apt-get install compizconfig-settings-manager</code>
This might take a while (30 min+), so take a break while its executing and go outside or something.

Ok, so when it's done.
