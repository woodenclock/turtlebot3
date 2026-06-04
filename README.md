# 🐢 Turtle Bot Instructions

### Common Commands:

```
echo 'source /opt/ros/jazzy/setup.bash' >> ~/.bashrc
source ~/.bash.rc
```

```
echo 'export TURTLEBOT3_MODEL=burger' >> ~/.bashrc
source ~/.bashrc
```

## Simulation Stage

#### Gazebo Sim:
```
ros2 launch turtlebot3_gazebo turtlebot3_world.launch.py
```

#### RViz:
```
source ~/.bashrc
rviz2
```

#### Control:
```
source ~/.bashrc
ros2 run turtlebot3_teleop teleop_keyboard
```

#### Checking:
```
ros2 topic list
```
--> should see topics like:
```
/cmd_vel
/odom
/scan
/tf
```

## Hardware Integration Stage

#### Single Board Computer (SBC) Setup:
https://emanual.robotis.com/docs/en/platform/turtlebot3/sbc_setup/#sbc-setup

#### SSH:
```
ssh rosi@turtlebot3.local
```

#### After Connecting:
https://emanual.robotis.com/docs/en/platform/turtlebot3/sbc_setup/

#### Installing ROS into Raspberry Pi:
https://docs.ros.org/en/jazzy/Installation/Ubuntu-Install-Debs.html#install-ros-2

#### Connecting for remote control:
bot side
```
export TURTLEBOT3_MODEL=burger
ros2 launch turtlebot3_bringup robot.launch.py
```

ubuntu machine side
```
ros2 run turtlebot3_teleop teleop_keyboard
```

#### Lidar:
Change Reliability Policy in LaserScan to "Best Effort".

#### Checking Battery Status:
```
ros2 topic echo /battery_state --once
```

#### Camera:

install usb_cam first.
```
ros2 run usb_cam usb_cam_node_exe --ros-args
-p video_device:=/dev/video0
-p image_width:=320
-p image_height:=240
-p framerate:=5.0
-p pixel_format:=yuyv2rgb
```

#### Docker:
```
cd ~/turtlebot3_ws/src/turtlebot3/docker/jazzy
sudo ./container.sh start
sudo ./container.sh enter

root@turtlebot3:~# ros2 launch turtlebot3_bringup robot.launch.py
```

#### SLAM (Simultaneous Localization and Mapping):
```
ros2 launch turtlebot3_cartographer cartographer.launch.py
```

