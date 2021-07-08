# Using-SLAM-map-to-launch-the-navigation
This repository shows the steps taken to using the SLAM map to launch the navigation. 

These were tested under ROS Melodic and Ubuntu 18.04.


# Dependencies

-Make sure you already have a running VM with ubuntu 18.04 OS, and already installed ROS Melodic inside it.

-proper map has to be prepared before running the Navigation

-type in the commands down below in the terminal

 For every step Open a new terminal from Remote PC with Ctrl + Alt + T
      
      
   **1.Launch Simulation World**
      
```
$ export TURTLEBOT3_MODEL=burger	
$ roslaunch turtlebot3_gazebo turtlebot3_world.launch
```
   **2.Run Navigation Node**
      
  ```
$ export TURTLEBOT3_MODEL=burger
$ roslaunch turtlebot3_navigation turtlebot3_navigation.launch map_file:=$HOME/map.yaml
```
in this step I face an error I solved  using this command:
```
sudo apt-get install ros-melodic-dwa-local-planner
```
   **3.Estimate Initial Pose**
     
1-Click the 2D Pose Estimate button in the RViz menu.

2-Click on the map where the actual robot is located and drag the large green arrow toward the direction where the robot is facing.

3-Repeat step 1 and 2 until the LDS sensor data is overlayed on the saved map.

4-Launch keyboard teleoperation node to precisely locate the robot on the map.

```
$ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
```
5-	Move the robot back and forth a bit to collect the surrounding environment information and narrow down the estimated location of the TurtleBot3 on the map which is displayed with tiny green arrows.

![10](https://user-images.githubusercontent.com/86648269/124653985-a474fd80-dea6-11eb-8d57-c2ffd2c056a6.png)
![11](https://user-images.githubusercontent.com/86648269/124654015-ad65cf00-dea6-11eb-9f38-72c4cc4af69f.png)

6-	Terminate the keyboard teleoperation node by entering Ctrl + C to the teleop node terminal in order to prevent different cmd_vel values are published from multiple nodes during Navigation.

  **4.Set Navigation Goal**
     
1-Click the 2D Nav Goal button in the RViz menu.

2-Click on the map to set the destination of the robot and drag the green arrow toward the direction where the robot will be facing.

-	This green arrow is a marker that can specify the destination of the robot.

- The root of the arrow is x, y coordinate of the destination, and the angle θ is determined by the orientation of the arrow.

- As soon as x, y, θ are set, TurtleBot3 will start moving to the destination immediately.

![12](https://user-images.githubusercontent.com/86648269/124654933-dc307500-dea7-11eb-91dc-14346b140e4a.png)

![13](https://user-images.githubusercontent.com/86648269/124654959-e3f01980-dea7-11eb-93e1-c92e35c00a59.png)

![14](https://user-images.githubusercontent.com/86648269/124654975-e9e5fa80-dea7-11eb-9fd3-fc52199ed985.png)





