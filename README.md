# ROS wrapper for ORB-SLAM3
[original repo](https://github.com/thien94/orb_slam3_ros_wrapper.git)

A ROS wrapper for [ORB-SLAM3](https://github.com/UZ-SLAMLab/ORB_SLAM3). The main idea is to use the ORB-SLAM3 as a standalone library and interface with it instead of putting everything together.


# Installation
Todo

# How to run

### EuRoC dataset:

- In one terminal, launch the node:
```
roslaunch orb_slam3_ros_wrapper euroc_monoimu.launch
```
- In another terminal, playback the bag:
```
rosbag play MH_01_easy.bag
```
Similarly for other sensor types.

# Topics
The following topics are published by each node:
- `/orb_slam3/all_points` ([`PointCloud2`](http://docs.ros.org/en/melodic/api/sensor_msgs/html/msg/PointCloud2.html)): all keypoints.
- `/orb_slam3/tracked_points` ([`PointCloud2`](http://docs.ros.org/en/melodic/api/sensor_msgs/html/msg/PointCloud2.html)): keypoints being tracked.
- `/orb_slam3/camera_pose` ([`PoseStamped`](http://docs.ros.org/en/melodic/api/geometry_msgs/html/msg/PoseStamped.html)): current left camera pose in world frame, as returned by ORB-SLAM3.
- `tf`: transformation from camera frame to world frame.

Todo
- keyframe poses (optimized)

# Params
- Enable / disable pangolin viewer: `enable_pangolin`
- For monocular/stereo case, use `world_roll`, `world_pitch`, `world_yaw` in the launch file to rotate the world frame if necessary (otherwise the first KF will be the world frame). The world frame will be rotated by the provided roll-pitch-yaw angles (in rad) in that order.
