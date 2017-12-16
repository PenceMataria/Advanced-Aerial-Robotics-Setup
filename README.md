# Ubuntu-Setup
This repository contains how to setup Ubuntu for basic Aerial Robotics .</br>
#### 1 Downloading ISO
###### Dowload Ubuntu 16.04 disk image file from :-https://www.ubuntu.com/download/desktop </br>
#### 2 Bootable Device
###### If you are on Windows :- Dowload Rufus :- https://rufus.akeo.ie/
###### If you are on Linux :- Search for Startup disk creator
#### 3 Insatallion
###### For more details :- https://builtvisible.com/the-ubuntu-installation-guide/
#### 4 Basic things to do after installation
###### (i) Update Ubuntu :-
    sudo apt-get update
    sudo apt-get upgrade
###### (ii) Install basic things :-
    sudo apt-get install vim #Vim is a highly configurable text editor
    sudo apt-get install git #Git is a free and open source distributed version control system
    #following two tools allow a user to access multiple separate terminal sessions inside a single terminal window
    sudo apt-get install terminator
    #or
    sudo apt-get install tmux
###### (iii) For extensive code writing or For work on big project use : Atom, SublimeText, VisualStudioCode . . . . . . 
#### 5 Installation of Robot OS :- 
     #for ros kinetic full desktop version
     #Setup your sources.list
     sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
     #Set up your keys
     sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 421C365BD9FF1F717815A3895523BAEEB01FA116
     #installation
     sudo apt-get update
     sudo apt-get install ros-kinetic-desktop-full
     #initialize rosdep
     sudo rosdep init
     rosdep update
     #environment setup
     echo "source /opt/ros/kinetic/setup.bash" >> ~/.bashrc
     source ~/.bashrc #if you are on bash else for Zsh replace bash everywhere by zsh
     #dependencies for building packages
     sudo apt-get install python-rosinstall python-rosinstall-generator python-wstool build-essential
If you found any problem in installation then visit :-http://wiki.ros.org/kinetic/Installation/Ubuntu     
#### For making your linux more attractive :- ZSH+POWERLEVEL9k, GNOME . . . . . . . . . 
#### 6 Basic setup for px4
###### (i) Install QGC :- for compressed archive : https://s3-us-west-2.amazonaws.com/qgroundcontrol/builds/master/QGroundControl.tar.bz2
     #Extract the archive using the terminal command:
     tar jxf QGroundControl.tar.bz2
     cd qgroundcontrol
     ./qgroundcontrol-start.sh
###### for AppImage
     chmod +x ./QGroundControl.AppImage
    ./QGroundControl.AppImage  (or double click)
###### (ii) Toolchain installation :- https://dev.px4.io/en/setup/dev_env_linux_ubuntu.html
###### (iii) Building the code of px4 :-
     #making local source
     mkdir -p ~/src
     cd ~/src
     git clone https://github.com/PX4/Firmware.git
     cd Firmware
     #building
     make px4fmu-v2_default
     #upload to board
     make px4fmu-v2_default upload
###### for more details :- https://dev.px4.io/en/setup/building_px4.html     
#### 7 Installing mavros :-
    #The mavros ros package enables MAVLink extendable communication between computers running ROS, MAVLink enabled autopilots, and MAVLink enabled GCS
    sudo apt-get install ros-kinetic-mavros
    sudo apt-get install ros-kinetic-mavros-extras
###### for more details :- https://dev.px4.io/en/robotics/    
