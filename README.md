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
<hr>  
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
<hr>  
## Installing and Launching Turtlesim

### Install turtlesim package
```
sudo apt update
```
Update the local package index.

```
sudo apt install ros-humble-turtlesim
```
Install the turtlesim package for ROS2 Humble.

<hr>

### Launch the turtlesim node
```
ros2 run turtlesim turtlesim_node
```
Launches the main turtlesim GUI node.  
<br>
<img width="894" height="846" alt="Screenshot from 2025-08-03 22-13-25" src="https://github.com/user-attachments/assets/abccac6a-5e3f-4e0f-88b9-bbc8aa0b9312" />


<hr>

### Control the turtle with keyboard
```
ros2 run turtlesim turtle_teleop_key
```
Launches keyboard control for the turtle.  
<br>
![Untitled video - Made with Clipchamp](https://github.com/user-attachments/assets/e8f555f0-84d7-4d2d-af31-730964a75f21)


<hr>

## Node Interaction

### List available nodes
```
ros2 node list
```
Displays all active ROS2 nodes.  
<br>
<img width="850" height="604" alt="Screenshot from 2025-08-03 22-30-24" src="https://github.com/user-attachments/assets/d550b34b-28d0-4611-9bb2-eed933d7afc7" />


<hr>

### Get information about a node
```
ros2 node info /turtlesim
```
Shows details about the `/turtlesim` node, including its topics and services. 
<br>
<img width="826" height="604" alt="Screenshot from 2025-08-03 22-32-32" src="https://github.com/user-attachments/assets/7ecd11b6-a1d7-492d-b3ea-e5ce5960954a" />


<hr>

## Topic Interaction

### List available topics
```
ros2 topic list
```
Lists all current topics being published or subscribed to.  
```
ros2 topic list -t
```
Displays all active topics along with their message types.  
<br>
<img width="826" height="604" alt="Screenshot from 2025-08-03 22-36-49" src="https://github.com/user-attachments/assets/dd404b85-a432-4d98-a77c-b59d9e52fdff" />

<hr>

### View velocity commands in real time
```
ros2 topic echo /turtle1/cmd_vel
```
Displays messages being published to the turtle's velocity topic.  
<br>
![Untitled video - Made with Clipchamp2](https://github.com/user-attachments/assets/2e5686a8-19de-4a51-b567-7c48d51c9445)


<hr>

### Visualize node/topic connections
```
rqt_graph
```
Opens a graphical interface showing node and topic relationships.  
<br>
<img width="865" height="766" alt="Screenshot from 2025-08-03 22-48-07" src="https://github.com/user-attachments/assets/bd2de268-e4a0-40e1-887d-003db4a128f3" />


<hr>

### Publish movement commands manually
```
ros2 topic pub /turtle1/cmd_vel geometry_msgs/msg/Twist "{linear: {x: 2.0, y: 0.0, z: 0.0}, angular: {x: 0.0, y: 0.0, z: 1.8}}"
```
Sends a velocity command to move and rotate the turtle.  
<br>
![Untitled video - Made with Clipchamp3](https://github.com/user-attachments/assets/da7a423a-b1cd-4fef-8f4e-8f61a12ec927)


<hr>

## Service Interaction

### List available services
```
ros2 service list
```
Lists all services offered by the current nodes.  
<br>
<img width="905" height="617" alt="Screenshot from 2025-08-03 22-56-12" src="https://github.com/user-attachments/assets/cbafd923-4cd6-43c5-8ba4-3f28c76909af" />


<hr>

### Clear the turtlesim background
```
ros2 service call /clear std_srvs/srv/Empty
```
Clears the background and resets the drawing canvas.  
<br>
![Untitled video - Made with Clipchamp4](https://github.com/user-attachments/assets/5e3d83c9-aac7-4965-9412-e9355258b839)


<hr>

## Parameter Interaction

### List and get parameters
```
ros2 param list
```
Displays all parameters available in the active nodes.

```
ros2 param get /turtlesim background_g
```
Gets the green component of the turtlesim background color.  
<br>
<img width="896" height="613" alt="Screenshot from 2025-08-03 23-03-10" src="https://github.com/user-attachments/assets/94f3c6da-75b4-43a5-b233-b4915766a79f" />


<hr>

### Set a parameter value
```
ros2 param set /turtlesim background_r 150
```
Changes the red component of the background color to 150.  
<br>
![Untitled video - Made with Clipchamp5](https://github.com/user-attachments/assets/f5b5cd44-bf5a-4f0f-a4c8-7b22a072b903)  
<hr>  
<br> 

### Created by **Abdulaziz AL-Thomali**




