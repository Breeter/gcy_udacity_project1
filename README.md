# For Project 5 

Notice: In this project, I used ros-melodic edition. So, this project has many packages to support the turtlebot.

## 1.  Localization 

The name of the localization script is *test_navigation.sh*.  You can use the script to location your robot in the map. 

Just input:  `./test_navigation.sh`

![test_navigation](https://user-images.githubusercontent.com/69617000/156378470-088a6d94-f4a9-4893-9c1b-3f9a7af9345d.png)

You can see the particle cloud is are distributed around the robot's position, and the denser the particles are, the more likely the robot is to be located.

### (1) Launch  file
This script consists of the following launch files.   
**turtlebot_world.launch**  
**amcl_demo.launch**  
**view_navigation.laucn**  

### (2) Explain
This script can realize localization function.   

First, Via the `roslaunch turtlebot_gazebo turtlebot_world.launch ` command , you can open your world in Gazebo program.   
*Notice: You should  change the world file link in the  launch file. *

In your world, the robot is in an unknowe position. So, you can use the amcl algorithm to location the position of robot.   
Via the  `roslaunch turtlebot_gazebo amcl_demo.launch` command, you will open the AMCL package for localization.    
AMCL package realizes the prediction of robot position through particle filter.   
It is estimated through the weight of motion model and measurements .   
As the robot moves, new measurements are obtained to improve the localization accuracy.

Via the `roslaunch turtlebot_rviz_launchers view_navigation.launch` command, you will open teh RVIZ program.  
Through the rviz program, the results of robot localization will be visualized.   
In rviz, a cloud of particles can be seen around the robot.   
As the robot moves, the particles will gradually gather.   
The density of particles determines the probability of the location of the robot.  


## 2. Mapping
 
The name of the mapping script is *test_slam.sh*. You can draw a map of the robot's area through slam algorithm.

Input: `./test_slam.sh`

![test_slam](https://user-images.githubusercontent.com/69617000/156380032-a6123f03-2675-42c7-b476-dba684b7d975.png)

As the robot moves, the map is gradually drawn.

### (1) Launch  file
This script consists of the following launch files.   
**turtlebot_world.launch**  
**gmapping_demo.launch**  
**view_navigation.laucn**   
**keyboard_teleop.launch**

### (2) Explain
This script can realize mapping function.  
Unlike localization, mapping uses one more gmapping_demo launch file.   
The localization process is based on our known global map.   
However, in mapping, we need to get the surrounding environment information through sensors and draw the map through algorithms.  
So, you will use gmapping packge through the `roslaunch turtlebot_gazebo gmapping_demo.launch` command.   
In gmmaping package, you will draw the surrounding environment and localize the robot through GraphSLAM algorithms.  
This algorithm will estimate the probability of whether there are obstacles in the surrounding area through the data of the sensor and robot motion.   
As the robot moves, it gradually draws all the maps.
Notic: *keyboard_teleop.launch* let you can control the robot by your keyboard.   

## 3. Navigation

The name of  the navigation script is *pick_object*.  You can set multiple target positions and let the robot move to the target.

Input: '<./pick_objects.sh>'

![pick_objects](https://user-images.githubusercontent.com/69617000/156380895-6a75c4a4-e388-4ccf-8fd4-95eadac6a5c7.png)

After setting the target position, the robot will observe the obstacles in front through the sensor and plan the appropriate route combined with the map.

### (1) Launch  file
This script consists of the following launch files.   
**turtlebot_world.launch**  
**amcl_demo.launch**  
**view_navigation.laucn**  
**pick_objects.launch**

### (2) Explain
In this script, the robot can move to the designated position through *navigation package* navigation function.  

Unlike previous localization script, this script adds a pick_objects node.   
In navigation packge, you can get a path for your robot based on Dijkstra's algorithm,  and while avoiding obstacles on its path.  
In pick_objects.cpp file, you can set the goal position and publish it.   

This script will produce the following effects:  
- The robot travels to the first goal position(pickup zone) and displays the arrival message.
-The robot stays for 5 seconds.
-The robot travels to the second goal position(dropoff zone) and displays the arrival message.




## 4. Home Service

By integrating the above functions, a family robot is designed. The name of script is *home_serive.sh*. 

![home_service](https://user-images.githubusercontent.com/69617000/156382076-c6276e4a-2d05-4bac-8ab9-891f8bd7ece6.png)

In this script, the robot will go to the marked __pickup zone__, and the __marker will disappear__ after arriving at the pickup zone. After completing the task, the robot goes to the __dropoff zone__ and __displays the marker__ of the dropoff zone after arriving at the dropoff zone.

## Project Description
 
.Project 5                                        # Project: Home Service Robot     
├── catkin_ws                                             # Catkin workspace  
│   ├── src  
│   │   ├── add_markers                                   # add_markers package          
│   │   │   ├── launch
│   │   │   │   ├── add_markers.launch   # launch file for add_marker function.  
│   │   │   │   ├── ADD_Markers.launch   # launch file for ADD_Marker function( project function).    
│   │   │   ├── src  
│   │   │   │   ├── add_markers.cpp                       # source code for add_markers  
│   │   │   │   ├──ADD_Markers.cpp                  # source code for ADD_Markers  
│   │   ├── pick_objects                                  # pick_objects package       
│   │   │   ├── src  
│   │   │   │   ├── pick_objects.cpp                      # source code for pick_objects  
│   │   ├── rvizConfig                                    # rvizConfig package   
│   │   │   ├── launch  
│   │   │   │   ├── view_navigation.launch   # launch file for rvizConfig of the home service robot  
│   │   │   ├── home_service.rviz              # rvizConfig file for home service robot    
│   │   ├── scripts                                       # shell scripts files  
│   │   │   ├── add_marker.sh   
│   │   │   ├── home_service.sh   
│   │   │   ├── launch.sh                         # test script  
│   │   │   ├── pick_objects.sh  
│   │   │   ├── test_navigation.sh  
│   │   │   ├── test_slam.sh  
│   │   ├── turtlebot                                     # keyboard_teleop.launch file  
│   │   ├── turtlebot_interactions                        # view_navigation.launch file  
│   │   ├── turtlebot_simulator                           # turtlebot_world.launch file         
│   │   ├── CMakeLists.txt                                # compiler instructions  
├── image                # image file  
