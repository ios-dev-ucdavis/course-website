---
layout: page
title: Access Mac on Campus
description: >
  Direction for accessing Macintosh machines physically on campus & remotely
hide_description: false
permalink: /mac/
---

### Who is This Guide For?
If you are intersted in iOS/macOS development but don't have access to a Macintosh Computer, this guide is for you!
If you have a mac, and it is running **macOS Big Sur 11.3 and later**, you probably don't need this guide.
[How to find out which macOS version I'm using?](https://support.apple.com/en-us/HT201260)

### Access Macintosh Machines on Campus Physically
There are multiple places on campus where you can access a Machintosh computer (e.g, Olson, SCC and Shields Library). However, for our course, you need a mac running at least **macOS Big Sur (11.3 and later)**. Thus, you need to go to the basement of Kemper Hall *(545 Bainer Hall Dr, Davis, CA 95616)*.

There are total **4** mac computers located there. **Mac-1 and Mac-2** is located at CSIF Room #71. However, this computer lab is currently closed for maintenance *(Last Updated: March 30th)*. We will monitor the situation and update on its status continuously.

Therefore, the only two options we have is **Mac-3 and Mac-4**. They are located in **CSIF Room #75**. They are both iMacs running macOS Big Sur, so you will be able to use Xcode and create iOS/macOS apps on them.

### Access Macintosh Machines remotely (with GUI support!)
> Note: You need to be connected to UC Davis Library VPN when following the  instructions. [Guide on how to use UC Davis Libarary VPN](https://www.library.ucdavis.edu/service/connect-from-off-campus/)

If you want to remotely connect to these macs and use graphical user interface(GUI), you should follow these steps.

- Step 1: Create an account on the mac computer you want to use.
	
  First, you may want to go to CSIF room #75, and create an account on the mac computer you want to use. Differnt from Ubuntu Virtual Machines in CSIF, you'll not be able to remotely connect to mac computers if you don't physically go to CSIF and create an account.

- Step 2: Establish a SSH (Secure Shell) tunnel
	
  In this step, you need to establish a SSH tunnel so you can use VNCViewer later.
	
	*If you are using a Mac/Linux machine:*
			1. Open the terminal app, and type in the following command:
				`ssh -L 5902:localhost:5900 <your_account>@mac#.cs.ucdavis.edu`
			This command moves port 5900, which is the default port for VNC, from mac#.cs.ucdavis.edu to a local port of 5902. So if you then connect a vnc viewer to port 5902 on the local port system you will be connecting port 5900 on mac#.

	*If you are using a Windows machine:*
			1. Open up putty and go to connection **Connection > SSH > Tunnels**
			2. Under *Add new forwarded port*, enter the following information:
				 `Source port: 5902`
				 `Destination: mac#.cs.ucdavis.edu:5900`
			3. Click Add
			4. Then go back to Session, and login to mac#.cs.ucdavis.edu as normal

- Step 3: Download and Install VNCViewer on your machine
	
  Go to VNCViewer [website](https://www.realvnc.com/en/connect/download/viewer/) and download the appropriate version.

<!---
- Step 4: Configure VNC Server through terminal
	
  Come back to the SSH session, and type in:
		`vncserver`
	Or 
		`vncserver -geometry <Resolution: Horizontal>x<Resolution: Vertical>`
		
	You should see this message displayed after a few seconds.
	> New 'mac#:1 [your username]' desktop is mac#:1
	Starting applications specified in /home/[your username]/.vnc/xstartup
	Log file is /home/[your username]/.vnc/mac#:1.log
	
	The `:1` may be a different number. Just make sure to use the number it gives when logging in.

	If you get this prompt:
	> You will require a password to access your desktops.

	Then you should enter a password you can remember. You will use this when you login to the server. Then run vncserver as described above.
-->

- Step 4: Open VNCViewer and Connect!
	Open VNCViewer, and connect to
		`localhost:5902`
	Follow the prompt, and you are good to go!

> Some caveats:
> 1. Account infomation **will not be synced across these mac machines**. If you've created an account on Mac-3, you will encounter an error when trying to remotely login to another mac (for example, Mac-2). Thus, be sure to stick with one machine, it will save you time.
> 2. All data on the mac computer **will not be backed up** automatically. Thus, we recommend backing up your data constantly, or use a version control system like Git **(strongly recommend)**.