## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/DICT-FOOVC2-Cebu/Security-System/edit/master/README.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/DICT-FOOVC2-Cebu/Security-System/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.

# STEP 1 - Installing Rasbian OS ----------------

Requirements:	
	At least 16 GB sd card
	Rasbian Stretch OS
	Disk Imager or you can use CMD
	
1. Go to raspberrypi.org to download the OS
2. Donwload Disk Imager from this site or any other will do
	https://osdn.net/projects/sfnet_win32diskimager/downloads/Archive/Win32DiskImager-0.9.5-install.exe/
3. Connect your sd card to the computer and format.
4. Open DiskImager
5. At the interface window select the letter of your sd card
6. Browse the Image file of your rasbian OS to select.
7. Click write and wait until done...
8. To enable ssh go to command prompt and type:
	echo.>e:/ssh and press enter
		note: "e" varies depending on the drive letter of your sd card.
9. Safely remove the device...
"Congrats you successfully intalled the Raspbian OS"

# Step 2: Access Raspberry Pi 3----------------

** GETTING STARTED
	Requirements available:	
		Monitor
		Keyboard
		Mouse	
		Rasberry Pi 3 Model B
		32gb SD card
		Connectors (HDMI or VGA as needed)
		Power supply with output 5v 2A
//Insert the sd card on the raspberry pi  and setup the connections as if treating the pi like a computer with monitor, keyboard and mouse.

//Connect to the internet through WI-FI.

//Now let's setup the rasberry pi environment:
	- for the keyboard goto applications menu > preferences > raspberry pi configuration > localization > set keyboard
		then set the layout to US
	- under interfaces enable the following: Camera, SSH, VNC, SERIAL PORT, SERIAL CONSOLE
	- you can change the resolution under "system" tab and set resolution.	
 
//In the Raspberry pi command prompt, 
	type: sudo apt-get upgrade && sudo apt-get update
		if a question appears that is answerable by yes or no, answer: y and enter
// to check the network connection details e.g. IP address of your rasp pi or the default gateway
	type: ifconfig 
// to check for your default gateway
	type: netstat -nr 
// type sudo nano /etc/network/interfaces
	sudo nano /etc/dhcpcd.conf then press enter
	when you are in the /etc/dhcpcd.conf environment, type
	interface wlan0
	static ip_address=192.168.0.144/24
	static router=192.168.0.1/24
	static domain_name_servers=192.168.0.1 8.8.8.8
	(to provide static IP address to your rasppi)
	to exit, press ctrl+X
//type sudo reboot then after 
//check for network connection, goto CLI type
	ping 8.8.8.8
//to change the password of your pi
	type: passwd and enter (you can set then whatever you want)
 	(change current password)
	raspberry (current)
	usccaraga (new password)

# Step 3: Access Raspberry UI from VNC Viewer---------------------

---Virtual Network Computing (VNC) is a graphical desktop sharing system that uses the Remote Frame Buffer protocol to remotely control another computer.
*be sure that the raspberry pi and the computer you're using must be connected to the same network.
	1. On your laptop feel free to downlod the vnc viewer to this site: https://www.realvnc.com/en/connect/download/viewer/
	2. Run and open the application.
	3. Enter the static ip adddress in the search bar and enter.
In this project we have the following configuration:
		ip address: 192.168.0.110
	4. Type the username as "pi" and the password you changed.

""that's it..welcome to the raspberry pi user interface!
