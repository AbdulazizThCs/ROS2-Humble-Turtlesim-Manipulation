# ROS2-Humble-Turtlesim-Manipulation  

Basic manipulation of turtlesim using ROS2 Humble commands .  

## Project Idea

This project provides a practical exploration of ROS2 Humble’s turtlesim package, demonstrating basic commands and concepts such as nodes, topics, services, and parameters.  

## Ubuntu Setup

1. `Install Ubuntu 22.04 version.`  
   Download and prepare the Ubuntu 22.04 ISO for installation.

2. `Download a virtualization platform (VMware or VirtualBox).`  
   Choose and install either VMware or VirtualBox to create virtual machines.

3. `Create a new virtual machine and mount the Ubuntu ISO.`  
   Complete the OS installation inside the virtual environment.  

## ROS2 Humble Setup

1. ```sudo apt update && sudo apt install locales```  
   Update package lists and install locale support.

2. ```sudo locale-gen en_US en_US.UTF-8```  
   Generate the US English locales.

3. ```sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8```  
   Set the system default locale to US English UTF-8.

4. ```export LANG=en_US.UTF-8```  
   Apply the locale environment variable.

5. ```locale  # verify settings```  
   Confirm the current locale settings.

6. ```sudo apt install software-properties-common```  
   Install software to manage repositories.

7. ```sudo add-apt-repository universe```  
   Enable the Universe repository for additional packages.

8. ```sudo apt update && sudo apt install curl -y```  
   Update package lists and install curl.

9. ```export ROS_APT_SOURCE_VERSION=$(curl -s https://api.github.com/repos/ros-infrastructure/ros-apt-source/releases/latest | grep -F "tag_name" | awk -F\" '{print $4}')```  
   Fetch the latest ROS apt source version.

10. ```curl -L -o /tmp/ros2-apt-source.deb "https://github.com/ros-infrastructure/ros-apt-source/releases/download/${ROS_APT_SOURCE_VERSION}/ros2-apt-source_${ROS_APT_SOURCE_VERSION}.$(. /etc/os-release && echo $VERSION_CODENAME)_all.deb"```  
    Download the corresponding ROS2 apt source package.

11. ```sudo dpkg -i /tmp/ros2-apt-source.deb```  
    Install the ROS2 apt source package.

12. ```sudo apt update```  
    Refresh package lists with new ROS2 repository.

13. ```sudo apt upgrade```  
    Upgrade all installed packages.

14. ```sudo apt install ros-humble-desktop```  
    Install the full ROS2 Humble desktop package.

15. ```sudo apt install ros-dev-tools```  
    Install ROS2 development tools.

16. ```echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc && source ~/.bashrc```  
    Automatically source ROS2 environment on every terminal session.




