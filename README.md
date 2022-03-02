# For Project 5 

Notice: In this project, I used ros-melodic edition. So, this project has many packages to support the turtlebot.

## 1.  Localization 

The name of the localization script is *test_navigation.sh*.  You can use the script to location your robot in the map. 

Just input: '<./test_navigation.sh>'

![test_navigation](https://user-images.githubusercontent.com/69617000/156378470-088a6d94-f4a9-4893-9c1b-3f9a7af9345d.png)

You can see the particle cloud is are distributed around the robot's position, and the denser the particles are, the more likely the robot is to be located.

## 2. Mapping
 
The name of the mapping script is *test_slam.sh*. You can draw a map of the robot's area through slam algorithm.

Input: '<./test_slam.sh>'

![test_slam](https://user-images.githubusercontent.com/69617000/156380032-a6123f03-2675-42c7-b476-dba684b7d975.png)

As the robot moves, the map is gradually drawn.

## 3. Navigation

The name of  the navigation script is *pick_object*.  You can set multiple target positions and let the robot move to the target.

Input: '<./pick_objects.sh>'

![pick_objects](https://user-images.githubusercontent.com/69617000/156380895-6a75c4a4-e388-4ccf-8fd4-95eadac6a5c7.png)

After setting the target position, the robot will observe the obstacles in front through the sensor and plan the appropriate route combined with the map.

## 4. Home Service

By integrating the above functions, a family robot is designed. The name of script is *home_serive.sh*. 

![home_service](https://user-images.githubusercontent.com/69617000/156382076-c6276e4a-2d05-4bac-8ab9-891f8bd7ece6.png)

In this script, the robot will go to the marked __pickup zone__, and the __marker will disappear__ after arriving at the pickup zone. After completing the task, the robot goes to the __dropoff zone__ and __displays the marker__ of the dropoff zone after arriving at the dropoff zone.

## Project Description
 
.Project 5                                        # Project: Home Service Robot   
-catkin_ws                                             # Catkin workspace  
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
