# SLAM-with-a-particle-filter

Implemented mapping and localization in an indoor environment using information from an IMU and a LiDAR sensor. 

## Hardware:
The humanoid has a Hokuyo LiDAR sensor [product link](https://hokuyo-usa.com/products/lidar-obstacle-detection) on its head (the final version of the robot had it in its chest but this is a different version). This LiDAR is a planar LiDAR sensor and returns 1080 readings at each instant, each reading being the distance of some physical object along a ray that shoots off at an angle between (-135, 135) degrees with discretization of 0.25 degrees in an horizontal plane (shown as white rays in the picture). Used the position and orientation of the head of the robot to calculate the orientation of the LiDAR in the body frame. The second kind of observations we will use pertain to the location of the robot. Directly used the (x, y, θ) pose of the robot in the world coordinates (θ denotes yaw). These poses were created presumably on the robot by running a filter on the IMU data (such estimates are called odometry estimates), and due to inherent tracking errors, these poses will not be extremely accurate.
More about the hardware in this paper: [link](https://ieeexplore.ieee.org/document/7057369).

## Coordinate frames:
The body frame is at the top of the head (X axis pointing forwards, Y axis pointing left and Z axis pointing upwards), the top of the head is at a height of 1.263m from the ground. The transformation from the body frame to the LiDAR frame depends upon the angle of the head (pitch) and the angle of the neck (yaw) and the height of the LiDAR above the head (which is 0.15m). The world coordinate frame where we want to build the map has its origin on the ground plane, i.e., the origin of the body frame is at a height of 1.263m with respect to the world frame at location (x, y, θ).

## Dataset:
Utilized the data collected from a humanoid named THOR that was built at Penn and UCLA [video link](https://www.youtube.com/watch?v=JhWYYuba1nE). Used 4 different trajectories of the robot in Towne Building at Penn.

# Binarized version of the map with Partical filter plots
Cyan trajectory = Odometry Trajectory 
<p>
Red trajectory =  Trajectory using Partical filter with the largest weight at each time-step

## Map 1 
<p align="center">
  <img width="1069" alt="Screenshot 2024-01-05 at 9 20 28 AM" src="https://github.com/RenuReddyK/SLAM-with-a-particle-filter/assets/68454938/2c355a47-3697-4230-91f0-6e9377a77385">
</p>

## Map 2 
<p align="center">
  <img width="1144" alt="Screenshot 2024-01-05 at 9 19 20 AM" src="https://github.com/RenuReddyK/SLAM-with-a-particle-filter/assets/68454938/e17bcce3-feab-4235-b9b6-f6c59dca996b">
</p>

## Map 3
<p align="center">
  <img width="1386" alt="Screenshot 2024-01-05 at 9 21 55 AM" src="https://github.com/RenuReddyK/SLAM-with-a-particle-filter/assets/68454938/450e6a24-54ba-44e1-a89d-89001cc16e2a">
</p>

## Map 4
<p align="center">
  <img width="1152" alt="Screenshot 2024-01-05 at 9 22 22 AM" src="https://github.com/RenuReddyK/SLAM-with-a-particle-filter/assets/68454938/d979435a-e989-43d0-a07c-a7fec4f89f61">
</p>

# Plots for dynamic propagation step:
## Map 1
Trajectory using onboard odometry | Trajectory using PF
--- | --- 
![](https://github.com/RenuReddyK/SLAM-with-a-particle-filter/assets/68454938/b36ced4c-a952-4cf8-8b81-e5b94819511d")| ![](https://github.com/RenuReddyK/SLAM-with-a-particle-filter/assets/68454938/2734e53f-901e-405d-96b9-ce22f5c8f1af)

## Map 2
Trajectory using onboard odometry | Trajectory using PF
--- | --- 
![](https://github.com/RenuReddyK/SLAM-with-a-particle-filter/assets/68454938/a01f376d-c14a-45ca-9028-d95ce8cd5a1e")| ![](https://github.com/RenuReddyK/SLAM-with-a-particle-filter/assets/68454938/d26f035a-956c-4519-b11d-62f20d6d6123)

## Map 3
Trajectory using onboard odometry | Trajectory using PF
--- | --- 
![](https://github.com/RenuReddyK/SLAM-with-a-particle-filter/assets/68454938/700faa0e-5fd4-4865-8cb0-bb7a693bbb34")| ![](https://github.com/RenuReddyK/SLAM-with-a-particle-filter/assets/68454938/96f64c78-98b8-49b5-af5e-768eb5ec1578)

## Map 4
Trajectory using onboard odometry | Trajectory using PF
--- | --- 
![](https://github.com/RenuReddyK/SLAM-with-a-particle-filter/assets/68454938/3b256a85-78b4-42a8-92b7-cc972474f6a6")| ![](https://github.com/RenuReddyK/SLAM-with-a-particle-filter/assets/68454938/aa78c8d2-838f-498a-ba7a-eaeedaab3038)
                                                                                                                             | **Blink Status: `true`**                                        



