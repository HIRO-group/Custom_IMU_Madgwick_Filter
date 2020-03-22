### Custom IMU Madgwick Filter
This is a Spin off of original IMU Madgwick filter: 
https://github.com/ccny-ros-pkg/imu_tools/tree/melodic

The assumptions made in this Repo are:
The world Frame is always ENU which is the default of Gazebo.

Extra Features:
In the original madgwick filter the input publisher name should be /imu/data_raw and output publisher is /imu/data. 
But in this implementation You can pass custom IMU publisher names and you can output pose to new publisher,
a crucial feature definitely required in original madgwick filter. 

Except the extra features, there is no difference between mine and original madgwick
filter.

Command to run:
```bash
rosrun custom_imu_madgwick_filter PoseEstimation ROS_NODE_NAME _imu_pose_publisher_name:=DESIRED_IMU_POSE_PUBLISHER_NAME _original_imu_publisher_name:="/ORIGINAL_IMU_PUBLISHER_NAME"
```

If you clone this repository into your catkin workspace, you can add this into your launch file. below is an example:
```bash
<node name="ROS_NODE_NAME" pkg="custom_imu_madgwick_filter" type="PoseEstimation" args="ROS_NODE_NAME" output="screen">
        <param name="imu_pose_publisher_name" value="DESIRED_IMU_POSE_PUBLISHER_NAME" /> 
        <param name="original_imu_publisher_name" value="/ORIGINAL_IMU_PUBLISHER_NAME" />   
</node>
```