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

# Step 4: 

INSTALLING OPENCV 3.3.0 AND PYTHON 3 ON RASPBERRY PI 3

The first thing you should do is expand your filesystem to include all available space on your micro-SD card:

'$ sudo raspi-config'

Select the advanced options then select expand file system and then select the Finish Button!

Next is enable your camera.

'$ sudo raspi-config'
Select the Localisation Options and then select camera and enable then select finish button!
Next Reboot your raspberry pi

'$ sudo reboot'
Next free up some space by deleting some applications inside the raspberry pi.


'$ sudo apt-get purge wolfram-engine'
'$ sudo apt-get purge libreoffice*'
'$ sudo apt-get purge scratch'
'$ sudo apt-get purge scratch2'
'$ sudo apt-get purge minecraft'
'$ sudo apt-get purge sonic-pi'
'$ sudo apt-get purge greenfoot'
'$ sudo apt-get clean'
'$ sudo apt-get auto remove'

Next Step is to update and upgrade any existing packages
'$ sudo apt-get update && sudo apt-get upgrade'

Install some developer tools, including CMake, which helps us configure the OpenCV build process:
'$ sudo apt-get install build-essential cmake pkg-config'

Install some image I/O packages that allow us to load various image file formats from disk. Examples of such file formats include JPEG, PNG, TIFF, etc.:
'$ sudo apt-get install libjpeg-dev libtiffs-dev libjasper-dev libpng12-dev'

Install libraries that allow us to read various video file format from disk as well as work directly with video streams.
'$ sudo apt-get install libavcodec-dev libavformat-dev libswscale-dev libv4l-dev'
'$ sudo apt-get install libxvidcore-dev libx264-dev'

Install GTK development library
'$ sudo apt-get install libgtk.0-dev libgtk-3-dev'

To optimized further the various operation inside opencv we need to install few extra dependencies.
'$ sudo apt-get install libatlas-base-dev gfortran'

Install Python 2.7 and Python 3 header files so we can compile opencv with python bindings.
'$ sudo apt-get install python2.7-dev python3-dev'

Next Step is grab the 3.3.0 archive of opencv from official opencv repository.
'$ cd ~'
'$ wget -0 opencv.zip https://github.com/Itseez/opencv/archive/3.3.0.zip'
'$ unzip opencv.zip'

To have access to features such SIFT and SUFT we need grab the opencv_contrib repository.
'$ wget -0 opencv_contrib.zip https://github.com/Itseez/opencv_contrib/archive/3.3.0'
'$ unzip opencv_contrib.zip'

Install PIP python package manager
'$ wget https://bootstrap.pypa.io/get-pip.py'
'$ sudo python get-pip.py'
'$ sudo python3 get-pip.py'

Next Install virtualenv and virtualenwrapper. This virtual environment is a special  tool used to keep the dependencies required by different projects in separate places by creating isolated, independent python environments for each of them.
'$ sudo pip install virtualen virtualenwrapper'
'$ sudo rm -rf ~/.cache/pip'

After the installation open ~/.profile
'$ nano ~/.profile'
and add this lines to the bottom of the file.
# virtualenv and virtualenwrapper
export WORKON_HOME=$HOME/.virtualenvs
export VIRTUALENWRAPPER_PYTHON=/usr/bin/python3
source /usr/local/bin/virtualenwrapper.sh

Next reload it to make sure the changes take affect.
'$ source ~/.profile'

Let us now create python virtual environment that we will use for computer vision development.
'$ mkvirtualenv cv -p python3'

After the creation of the python virtual environment you should see the text (cv) preceding your prompt., just like the example below:
(cv) pi@raspberrypi: ~ $

Everytime you open a new terminal always run the ff. line command to ensure that you are working in the virtual environment.
'$ source ~/.profile'
'$ workoncv'

Next Install the python dependency NumPy, Python package used for numerical processing
'$ pip install numpy'

Double check that you are on the cv virtual environment.
Afterwards, we can now setup our build using cmake.
'$ cd ~/opencv-3.3.0'
'$ mkdir build'
'$ cd build'
'$ cmake -D CMAKE_BUILD_TYPE=RELEASE \'
-D CMAKE_INSTALL_PREFIX=usr/LOCAL \
-D OPENCV_EXTRA_MODULES_PATH=~/opencv_contrib-3.3.0/module \
-D ENABLE_NEON=ON \
-D ENABLE_VFPV3=ON \
-D BUILD_TESTS=OFF \
-D INSTALL_PYTHON_EXAMPLES=OFF \
-D BUILD_EXAMPLES=OFF ..

Before you start the compile project increase your swap face size to enable opencv to compile with all 4 cores to the raspberry pi.

'$ sudo nano /etc/dphys-swapfile'
Then edit your CONF_SWAPSIZE variable.
# set size to absolute value, leaving empty (default) then uses computed value
# you most likely don't want this, unless you have a special disk situation
# CONF_SWAPSIZE=100
CONF_SWAPSIZE=2048

Activate the new swap space by restarting the swap service.
'$ sudo /etc/init.d/dphys-swapfile stop'
'$ sudo /etc/init.d/dphys-swapfile start'


Compile opencv 
'$ make -j4' 
if there is an error just run: 
'$ make clean'
'$ make -j4'

if there is no error, install opencv 3 on your raspberry pi.
'$ sudo make install'
'$ sudo ldconfig'

Next issue the ff. commands to sym-link the cv2.so bindings into your cv environment.
'$ cd /usr/local/lib/python3.5/site-packages/'
'$ sudo mv cv2.cpython-35m-arm-linux-gnueabihf.so cv2.so'
'$ cd ~/.virtualens/cv/lib/python3.5/site-packages/'
'$ ln -s /usr/local/lib/python3.5/site-packages/cv2.so cv2.so'

Open up a new terminal execute the source and work on commands and then finally attempt to import the python + opencv bindings.
'$ source ~/.profile'
'$ workon cv'
'$ pyhton'
>>> import cv2
>>> cv2.__version__
'3.3.0'
>>>

And now change the swap size back!
'$ sudo nano /etc/dphys-swapfile'

Then edit the CONF_SWAPSIZE
# set size to absolute value, leaving empty (default) then uses computed value
# you most likely don't want this, unless you have a special disk situation
CONF_SWAPSIZE=100
#CONF_SWAPSIZE=2048

'$ sudo /etc/init.d/dphys-swapfile stop'
'$ sudo /etc/init.d/dphys-swapfile start'

Finally, you have successfully installed opencv 3 and python on your raspberry pi.







