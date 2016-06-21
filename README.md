# ROS auf Cubieboard unter Linaro 12.08

/etc/apt/sources.list.d/ros-latest.list 
deb http://packages.ros.org/ros/ubuntu/ precise main restricted 
deb-src http://packages.ros.org/ros/ubuntu/ precise main 

/etc/apt/sources.list.d/linaro-overlay-ppa.list 
# Linaro Overlay PPA
deb http://ppa.launchpad.net/linaro-maintainers/overlay/ubuntu/ precise main universe restricted multiverse 
deb-src http://ppa.launchpad.net/linaro-maintainers/overlay/ubuntu/ precise main restricted multiverse  

/etc/apt/sources.list
deb http://ports.ubuntu.com/ubuntu-ports/ precise main universe restricted multiverse 
deb-src http://ports.ubuntu.com/ubuntu-ports/ precise main universe restricted multiverse 
deb http://ports.ubuntu.com/ubuntu-ports/ precise-security main universe restricted multiverse 
deb-src http://ports.ubuntu.com/ubuntu-ports/ precise-security main universe restricted multiverse 
deb http://ports.ubuntu.com/ubuntu-ports/ precise-updates main universe restricted multiverse 
deb-src http://ports.ubuntu.com/ubuntu-ports/ precise-updates main universe restricted multiverse 



yaml-cpp aus archiv mit cmake kompilieren mit -DBUILD_SHARED_LIB und -fPIC in CFLAGS
install unter /usr als prefix nicht /usr/local
wget http://yaml-cpp.googlecode.com/files/yaml-cpp-0.3.0.tar.gz
tar -xvzf yaml-cpp-0.3.0.tar.gz
cd yaml-cpp
mkdir build
cd build
cmake -DBUILD_SHARED_LIB=ON ..
make (see if shared built)
make install
ldconfig


locale auf en-US setzen
vi /etc/default/locale
locale-gen en_US.UTF-8

lsb-release installieren und auf /etc/lsb-release wieder von linaro auf ubuntu ändern
/etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.08
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.08"

startup-ros packages von hand downloaden und als deb pakete mit abhängigkeiten installieren

check effective default compile flags testen mit: gcc -Q -v ./test.c


collada_urdf
vorher assimp3 installieren
von http://sourceforge.net/projects/assimp/files/assimp-3.0
mkdir build
cd build
cmake -DCMAKE_INSTALL_PREFIX ..
make
make install
dann in 
src/collada_urdf/src/collada_urdf.cpp and write #define IS_ASSIMP3 at the top of the file

Install OpenNI2 from Github
Install OpenNI from GitHub
Install PrimeSense/Sensor from GitHub
überall in Platform.Arm anpassen
-mfloat-abi=hard und -I/usr/include/arm-linux/gnueabihf
und bei jobkalkulation fest 1 eintragen berechnet imm -j0 statt -j1



wget from ROS packages
python-catkin-pkg_0.1.9-1_all.deb
python-rosdep_0.10.12-1_all.deb
python-rosinstall_0.6.22-1_all.deb
python-rospkg_1.0.18-1_all.deb
python-vcstools_0.1.26-1_all.deb
python-wstool_0.0.2-1_all.deb
dpkg -i *deb
solve dependencies first

HW crypto enable kernel module
cryptodev-linux-1.5.tar.gz




ros catkin build and install single isolated package
catkin_make_isolated --install-space /opt/ros/groovy-isolated --install --source image_pipeline/image_view --build image_pipeline/image_view/build --devel image_pipeline/image_view/build/devel


catkin_make_isolated --install-space /opt/ros/groovy-isolated --install --source image_pipeline/stereo_image_proc --build image_pipeline/stereo_image_proc/build --devel image_pipeline/stereo_image_proc/devel
