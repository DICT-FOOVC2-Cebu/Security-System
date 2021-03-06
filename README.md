# STEP 1 - Installing Raspbian OS
```
Requirements:	
At least 16 GB sd card
Rasbian Stretch OS
Disk Imager or you can use CMD
```
1. Go to raspberrypi.org to download the OS
2. Donwload Disk Imager from this site or any other will do
	https://osdn.net/projects/sfnet_win32diskimager/downloads/Archive/Win32DiskImager-0.9.5-install.exe/
3. Connect your sd card to the computer and format.
4. Open DiskImager
5. At the interface window select the letter of your sd card
6. Browse the Image file of your rasbian OS to select.
7. Click write and wait until done...
8. To enable ssh go to command prompt and type:
```
echo.>e:/ssh
``` 
note: "e" varies depending on the drive letter of your sd card.
9. Safely remove the device...
###### Congrats you successfully intalled the Raspbian OS

# Step 2: Access Raspberry Pi 3

**GETTING STARTED**
```
Requirements Needed:	
Monitor
Keyboard
Mouse	
Rasberry Pi 3 Model B
32gb SD card
Connectors (HDMI or VGA as needed)
Power supply with output 5v 2A
```
1. Insert the sd card on the raspberry pi  and setup the connections as if treating the pi like a computer with monitor, keyboard and 		mouse.
2. Connect to the internet through WI-FI.
3. Now let's setup the rasberry pi environment:
i. for the keyboard goto applications menu > preferences > raspberry pi configuration > localization > set keyboard
		then set the layout to US
ii. under interfaces enable the following: Camera, SSH, VNC, SERIAL PORT, SERIAL CONSOLE
iii. you can change the resolution under "system" tab and set resolution.	
 
##### In the Raspberry pi command prompt, type: 
```
sudo apt-get upgrade && sudo apt-get update
```
##### if a question appears that is answerable by yes or no, answer: y and enter
##### to check the network connection details e.g. IP address of your rasp pi or the default gateway type: 
```
ifconfig
``` 
##### to check for your default gateway type: 
```
netstat -nr
``` 
##### to provide static IP address to your rasppi type 
```
sudo nano /etc/network/interfaces
sudo nano /etc/dhcpcd.conf
```
##### when you are in the /etc/dhcpcd.conf environment, type:
```
interface wlan0
static ip_address=192.168.0.144/24
static router=192.168.0.1/24
static domain_name_servers=192.168.0.1 8.8.8.8
```
##### to exit, press `ctrl+X` then type: 
```
sudo reboot
```
##### After the rasp pi boot up, check for network connection, goto CLI type:
```
ping 8.8.8.8
```
##### to change the password of your pi type:
```
passwd
```
you can the set the password whatever you want
- (change current password)
- raspberry (current)
- usccaraga (new password)

# Step 3: Access Raspberry UI from VNC Viewer

###### Virtual Network Computing (VNC) is a graphical desktop sharing system that uses the Remote Frame Buffer protocol to remotely control another computer.
###### be sure that the raspberry pi and the computer you're using must be connected to the same network.
1. On your laptop feel free to downlod the vnc viewer to this site: https://www.realvnc.com/en/connect/download/viewer/
2. Run and open the application.
3. Enter the static ip adddress in the search bar and enter.
- In this project we have the following configuration:
```
ip address: 192.168.0.110
```
4. Type the username as "pi" and the password you changed.
###### that's it..welcome to the raspberry pi user interface!

### Here is how to Connect the Raspberry pi GPIO Extension and the door sensor.
![connecting door magnetic sensor](https://github.com/DICT-FOOVC2-Cebu/Security-System/blob/master/Security%20system%20physical%20connection/SCHEMATIC%20RASPBERRY%20PI.png)
![connecting gpio cable](https://github.com/DICT-FOOVC2-Cebu/Security-System/blob/master/Security%20system%20physical%20connection/gpio%20expansion%2040%20pins.jpg)
### Please check carefully, any misleading connection will cause a serious damage to the Raspberry Pi Components which is possibly irreversible!
 
# Step 4

INSTALLING OPENCV 3.3.0 AND PYTHON 3 ON RASPBERRY PI 3

1. The first thing you should do is expand your filesystem to include all available space on your micro-SD card:
```
$ sudo raspi-config

2. Select the advanced options then select expand file system and then select the Finish Button!

3. Next is enable your camera.
```
$ sudo raspi-config
```
4. Select the Localisation Options and then select camera and enable then select finish button!
```
5. Next Reboot your raspberry pi
```
`$ sudo reboot`
```
6. Next free up some space by deleting some applications inside the raspberry pi.
```

`$ sudo apt-get purge wolfram-engine`
`$ sudo apt-get purge libreoffice*`
`$ sudo apt-get purge scratch`
`$ sudo apt-get purge scratch2`
`$ sudo apt-get purge minecraft`
`$ sudo apt-get purge sonic-pi`
`$ sudo apt-get purge greenfoot`
`$ sudo apt-get clean`
`$ sudo apt-get auto remove`
```

7. Next Step is to update and upgrade any existing packages
```
`$ sudo apt-get update && sudo apt-get upgrade`
```

8. Install some developer tools, including CMake, which helps us configure the OpenCV build process:
```
`$ sudo apt-get install build-essential cmake pkg-config`
```
9. Install some image I/O packages that allow us to load various image file formats from disk. Examples of such file formats include JPEG, PNG, TIFF, etc.:
```
`$ sudo apt-get install libjpeg-dev libtiffs-dev libjasper-dev libpng12-dev`
```
10. Install libraries that allow us to read various video file format from disk as well as work directly with video streams.
```
`$ sudo apt-get install libavcodec-dev libavformat-dev libswscale-dev libv4l-dev`
```
`$ sudo apt-get install libxvidcore-dev libx264-dev`
```
11. Install GTK development library
```
`$ sudo apt-get install libgtk.0-dev libgtk-3-dev`
```
12. To optimized further the various operation inside opencv we need to install few extra dependencies.
```
`$ sudo apt-get install libatlas-base-dev gfortran`
```
13. Install Python 2.7 and Python 3 header files so we can compile opencv with python bindings.
```
`$ sudo apt-get install python2.7-dev python3-dev`
```
14. Next Step is grab the 3.3.0 archive of opencv from official opencv repository.
```
`$ cd ~`
`$ wget -0 opencv.zip https://github.com/Itseez/opencv/archive/3.3.0.zip`
`$ unzip opencv.zip`
```
15. To have access to features such SIFT and SUFT we need grab the opencv_contrib repository.
```
`$ wget -0 opencv_contrib.zip https://github.com/Itseez/opencv_contrib/archive/3.3.0`
`$ unzip opencv_contrib.zip`
```
16. Install PIP python package manager
```
`$ wget https://bootstrap.pypa.io/get-pip.py`
`$ sudo python get-pip.py`
`$ sudo python3 get-pip.py`
```
17. Next Install virtualenv and virtualenwrapper. This virtual environment is a special  tool used to keep the dependencies required by different projects in separate places by creating isolated, independent python environments for each of them.
```
`$ sudo pip install virtualen virtualenwrapper`
`$ sudo rm -rf ~/.cache/pip`
```
18. After the installation open ~/.profile
`$ nano ~/.profile`
```
- and add this lines to the bottom of the file.
- #virtualenv and virtualenwrapper
- export WORKON_HOME=$HOME/.virtualenvs
- export VIRTUALENWRAPPER_PYTHON=/usr/bin/python3
- source /usr/local/bin/virtualenwrapper.sh
```
19. Next reload it to make sure the changes take affect.
```
`$ source ~/.profile`
```
- Let us now create python virtual environment that we will use for computer vision development.
```
`$ mkvirtualenv cv -p python3`
```
20. After the creation of the python virtual environment you should see the text (cv) preceding your prompt., just like the example below:
```
- (cv) pi@raspberrypi: ~ $
```
- Everytime you open a new terminal always run the ff. line command to ensure that you are working in the virtual environment.
```
`$ source ~/.profile`
`$ workoncv`
```
21. Next Install the python dependency NumPy, Python package used for numerical processing
```
`$ pip install numpy`
```
`- Double check that you are on the cv virtual environment.`
`- Afterwards, we can now setup our build using cmake.`
`$ cd ~/opencv-3.3.0`
`$ mkdir build	`
`$ cd build`
`$ cmake -D CMAKE_BUILD_TYPE=RELEASE \`
`-D CMAKE_INSTALL_PREFIX=usr/LOCAL \`
`-D OPENCV_EXTRA_MODULES_PATH=~/opencv_contrib-3.3.0/module \`
`-D ENABLE_NEON=ON \`
`-D ENABLE_VFPV3=ON \`
`-D BUILD_TESTS=OFF \`
`-D INSTALL_PYTHON_EXAMPLES=OFF \`
`-D BUILD_EXAMPLES=OFF ..`
```
- Before you start the compile project increase your swap face size to enable opencv to compile with all 4 cores to the raspberry pi.
```
`$ sudo nano /etc/dphys-swapfile`
```
- Then edit your CONF_SWAPSIZE variable.
#set size to absolute value, leaving empty (default) then uses computed value
#you most likely don't want this, unless you have a special disk situation
#CONF_SWAPSIZE=100
CONF_SWAPSIZE=2048
```
22. Activate the new swap space by restarting the swap service.
```
`$ sudo /etc/init.d/dphys-swapfile stop`
`$ sudo /etc/init.d/dphys-swapfile start`

```
- Compile opencv 
```
`$ make -j4 `
`if there is an error just run: `
`$ make clean`
`$ make -j4`
```
- if there is no error, install opencv 3 on your raspberry pi.
```
`$ sudo make install`
`$sudo ldconfig`
```
23. Next issue the ff. commands to sym-link the cv2.so bindings into your cv environment.
```
`$ cd /usr/local/lib/python3.5/site-packages/`
`$ sudo mv cv2.cpython-35m-arm-linux-gnueabihf.so cv2.so`
`$ cd ~/.virtualens/cv/lib/python3.5/site-packages/`
`$ ln -s /usr/local/lib/python3.5/site-packages/cv2.so cv2.so`
```
24. Open up a new terminal execute the source and work on commands and then finally attempt to import the python + opencv bindings.
```
`$ source ~/.profile`
`$ workon cv`
`$ pyhton`
>>> import cv2
>>> cv2.__version__
'3.3.0'
>>>
```
25. And now change the swap size back!
```
`$ sudo nano /etc/dphys-swapfile`
```
- Then edit the CONF_SWAPSIZE
```
#set size to absolute value, leaving empty (default) then uses computed value
#you most likely don't want this, unless you have a special disk situation
CONF_SWAPSIZE=100
#CONF_SWAPSIZE=2048
```
`$ sudo /etc/init.d/dphys-swapfile stop`
`$ sudo /etc/init.d/dphys-swapfile start`
```
Finally, you have successfully installed opencv 3 and python on your raspberry pi.

# Step 5 - BUILDING A FACE RECOGNITION DATASET

_This is a preparatory step before training your raspberry pi to detect and recognize individual faces.
Here, a dataset of faces of oneself is gathered in order for the raspberry pi to compare the actual live face from the gathered dataset of faces for recognition. The raspberry pi camera is used to capture faces of oneself. These images are then collected and compiled in one folder._
###### The following are the steps on how to build a face recognition dataset:
1. Enter the raspberry pi command prompt environmet
2. Type: `pip install --upgrade imutils`
it should look like these:
```
$ pip install --upgrade imutils 
```
###### *Note:  Be sure that the OpenCV is installed*
3. In the raspberry pi terminal, type: `mkdir dataset`
###### *this makes a directory for the dataset*
4. Type: `mkdir dataset/<name of the person's face>`
*this command names a subdirectory under dataset directory which all of the images/faces were contained.*
###### ex: 
```
$ mkdir dataset/john
```
5. Open the `build_face_dataset.py` from the repository
*To understand further eachline of code in this program, visit in this* [link](https://www.pyimagesearch.com/2018/06/11/how-to-build-a-custom-face-recognition-dataset/)
###### Note: Some codes are removed and changed.
6. Execute the following in the raspberry pi command prompt:
```
$ python build_face_dataset.py --cascade haarcascade_frontalface_default.xml \
    --output dataset/adrian
```
###### After clicking enter, the following shows up:
`[INFO] starting video stream...
[INFO] 6 face images stored
[INFO] cleaning up...`
		
# Step 6 - Face Recognition
*This the part where the raspberry pi is trained to detect and recognize faces. Deep neural network is used to compute a 128-d vector (i.e. a list of 128 floating point values) to quantify each face in the dataset.
 Note: Make sure that OpenCV is installed and you have gathered dataset of faces.*

###### The following are the steps to configure your raspberry pi for face recognition:
1. In the raspberry pi command prompt, install dlib toolkit by typing: 
`workon <your env name> # optional`
`pip install dlib`
###### it should look like this:
```
$ workon <your env name> # optional
$ pip install dlib
```
###### then press enter
2. Install `face_recognition module` by typing:
`workon <your env name> # optional`
`pip install face_recognition`
###### it should look like this:
```
$ workon <your env name> # optional
$ pip install face_recognition
```
###### then press enter
3. Install `imutils package` by typing:
`workon <your env name> # optional`
`pip install imutils`
###### it should look like this:
```
$ workon <your env name> # optional
$ pip install imutils
```
###### then press enter
4. Open up `encode_faces.py`
*to understand further the lines of codes, refer to the following* [link](https://www.pyimagesearch.com/2018/06/25/raspberry-pi-face-recognition/)
5. Open `pi_face_recognition.py`
*to understand further the lines of codes, refer to the following* [link](https://www.pyimagesearch.com/2018/06/25/raspberry-pi-face-recognition/)
6. Open up raspberry Pi terminal and execute/type the following:
`python pi_face_recognition.py --cascade haarcascade_frontalface_default.xml \
	--encodings encodings.pickle`
###### it should look like this:
```
$ python pi_face_recognition.py --cascade haarcascade_frontalface_default.xml \
    --encodings encodings.pickle
[INFO] loading encodings + face detector...
[INFO] starting video stream...
[INFO] elasped time: 20.78
[INFO] approx. FPS: 1.21
```

# Step 7: INSTALLING XAMMP
1: Open the XAMPP website. Go to https://www.apachefriends.org/index.html in your computer's web browser.

2: Click XAMPP for Windows. It's a grey button near the bottom of the page.

3: Double-click the downloaded file. This file should be named something like `xampp-win32-7.2.4-0-VC15-installer`, and you'll find it in the default downloads location (e.g., the "Downloads" folder or the desktop).

4: Click Yes when prompted. This will open the XAMPP setup window.
You may have to click OK on a warning if you have User Account Control (UAC) activated on your computer.

6: Click Next. It's at the bottom of the setup window.

7: Select aspects of XAMPP to install. Review the list of XAMPP attributes on the left side of the window; if you see an attribute that you don't want to install as part of XAMPP, uncheck its box.

8: Click Next. It's at the bottom of the window.

9: Select an installation location. Click the folder-shaped icon to the right of the current installation destination, then click a folder on your computer.

10: Click OK. Doing so confirms your selected folder as your XAMPP installation location.

11: Uncheck the "Learn more about Bitnami" box, then click Next. The "Learn more about Bitnami" box is in the middle of the page.

12: Begin installing XAMPP. Click Next at the bottom of the window to do so. XAMPP will begin installing its files into the folder that you selected.


# Step 8: USING XAMPP
1: Click the xampp application.

2: Click Start of the Apache and MySql.

Note: Don't close the xampp application.
	

ACCESSING LOCALHOST TO A WEB BROWSER
Step 1: Go to your web browser and go to `192.168.0.114/security_system/login.php`

Note: We create default password for admin.

	Username: admin

	Password: admin

Step 2: To check/edit the database just go to 192.168.0.114/phpmyadmin

Note: 

      Username: root

      Password: usccaraga

# Step 9: Sending files to VNC Server

1. Click the VNC Viewer File Transfer toolbar button. The File Transfer dialog opens:

2. Click the Send files button. The Send Files dialog opens.

3. Select a file or folder. To select multiple files and/or folders, hold down the SHIFT key.

	Under Windows, you cannot directly select a folder. Instead, double-click to open that folder, then click Use Entire Folder. To select multiple folders, open the parent folder and click Use Entire Folder. Note this means other files and folders in the parent folder will also be transferred.


4. Click Open (OK under Linux). The File Transfer dialog opens on the VNC Server computer:

	The most recent file transfer operation is highlighted. You can check its status, or pause or stop the transfer if it takes more than a few seconds.

	By default, files are downloaded to the desktop (Downloads folder under macOS). To change this for future file transfer operations, select an option from the Fetch files to dropdown at the bottom of the File Transfer dialog. Note you must have write permissions for the folder you choose. Alternatively, you can ask to be prompted each time.


# Common Errors that can be encountered:

Error retrieving accessibility bus address
You need to do additional installations:
```
$ sudo apt-get install at-spi2-core
```
OpenCV Error Assertion Failed
Use the command:
```
$ sudo modprobe bcm2835-v4l2
```
And also make sure the path of your haarcascade i.e. face_cascade = cv2.CascadeClassifier('/home/pi/opencv-3.3.0/data/haarcascades/haarcascade_frontalface_default.xml') is correct because it could also cause the error above.

face_recognition module installation error
Just keep on running the command below until it no longer gives you error and the installation is finally complete.
```
$ pip install face_recognition
```
