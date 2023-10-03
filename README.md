# ecse373_f23_hxp308_bags_and_playback
# Laboratory #3
## ROS Description of robots
### This lab will interpret the “ROS bagged” data from the architectural survey of the fifth floor of the Glennan building using the URDF description from the previous laboratory.

## Loading the Robot Model
### hardware defines a base_link to which everything must attach, the platform also has an IMU which is connected to the base_link. The following XACRO file should be placed in the urdf directory of a new ROS package that depends on the ROS package from the previous laboratory. 
##Using the ROS Bag Files
### Playback the data in the bag_map_data package and remap /tf_trajectory topic to /tf.
`rosbag play <full_path_to_bag_file> /tf_trajectory:=/tf`
### View the topics being published.
`rostopic list`
### If a /tf_trajectory topic is visible, there may have been a mistake.

## View Map
### Download the map_server package:
`sudo apt install ros-noetic-map-server`
### Start the map_server node with the existing 2D map of the fifth floor of Glennan.
`rosrun map_server map_server `rospack find maps_glennan`/maps/glennan5_map.yaml`
### Echo to the terminal the map message from the /map topic, just once.
`rostopic echo -n 1 /map`

## View Map in RVIZ
### At the bottom left of the screen in RVIZ, press "Add" and choose "By topic" and select /map.
### Now, the 2D map is loaded into RVIZ.
### Under "Global Options", set the "Fised Frame" to map.
### Under all three "LaserScan", set the "Decay Time" to 5-10. This will get laggy without a dedicated graphics card.

## View Robot in Config
### View robot in RVIZ
`roslaunch navvis_description display.launch`
### View map in RVIZ
`roslaunch bags_and_playback bags_and_playback.launch`


