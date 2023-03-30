# rf2o_laser_odometry

## Source Notes
Estimation of 2D odometry based on planar laser scans. Useful for mobile robots with innacurate base odometry.

RF2O is a fast and precise method to estimate the planar motion of a lidar from consecutive range scans. For every scanned point we formulate the range flow constraint equation in terms of the sensor velocity, and minimize a robust function of the resulting geometric constraints to obtain the motion estimate. Conversely to traditional approaches, this method does not search for correspondences but performs dense scan alignment based on the scan gradients, in the fashion of dense 3D visual odometry.

Its very low computational cost (0.9 milliseconds on a single CPU core) together whit its high precission, makes RF2O a suitable method for those robotic applications that require planar odometry.

For full description of the algorithm, please refer to: **Planar Odometry from a Radial Laser Scanner. A Range Flow-based Approach. ICRA 2016** Available at: http://mapir.isa.uma.es/work/rf2o

## Motivation for Usage

The IMU's available to us at TeamH are the UM7 and the Phidget Spatial 3/3/3. While the phidget
has issues in interfacing with ROS, the UM7 data is jittery.

Additionally, the lack of wheel odometry during development, means that we can only rely on
LIDAR odometry to give accurate odometry results. Hence, this package is used to publish odometry data

## TF2 bindings

The node which publishes odometry data also publishes the transformation between two frames:
- odom
- base_footprint

These frames are necessary for the slam_toolbox or any other downstream node.