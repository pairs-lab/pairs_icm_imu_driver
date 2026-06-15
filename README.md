# pairs_icm_imu_driver

ROS driver for the InvenSense ICM-42688-P inertial measurement unit, used on PAIRS UAVs to provide raw accelerometer and gyroscope data to the estimation and control pipeline. The driver talks to the sensor directly over the Linux SPI bus (spidev), configures its registers, and publishes the readings as a standard `sensor_msgs/Imu` topic.

## Contents

- **nodelet** `pairs_icm_imu_driver/PairsIcmImuDriver` (a `nodelet::Nodelet`) — reads the ICM-42688-P over SPI and publishes `sensor_msgs/Imu` on `~imu_out` (remapped to `~imu`). Exported via `nodelets.xml`.
- **`launch/imu.launch`** — runs the driver, standalone or under a nodelet manager, in the UAV namespace.
- **`config/imu.yaml`** — parameter file loaded by the launch.

## Install (ROS 1 Noetic)

```bash
sudo apt install ros-noetic-pairs-icm-imu-driver
```

## Usage

```bash
roslaunch pairs_icm_imu_driver imu.launch
```

This publishes IMU data on `/$UAV_NAME/icm_imu/imu`. Set `standalone:=false` to load it into an existing nodelet manager instead of running it on its own.
