# Assembly Kitting Manager

## Features
- manage Part

## To Do

- list up ros dependencies

## Getting Started

- python 2.7 
- [assemlby_camera_manager](https://github.com/SeungBack/assembly_camera_manager)
- [assemlby_part_recognition](https://github.com/SeungBack/assembly_part_recognition)


## Published Topics
#### `/assembly/vis_is`
- message type: `sensor_msgs/Image`
- Visualization results of instance segmentation 


## How to use
### Single Camera Setup (Kinect Azure)
1. launch k4a driver
```
$ ROS_NAMESPACE=azure1 roslaunch azure_kinect_ros_driver driver.launch color_resolution:=720P depth_mode:=NFOV_2X2BINNED fps:=5  tf_prefix:=azure1_
```
2. launch k4a manager 
```
$ roslaunch assembly_camera_manager single_azure_manager.launch target_fiducial_id:="1"
```
3. camera to map calibration 
```
$ rosservice call /azure1/extrinsic_calibration "target_fiducial_ids: [1]"
```
4. 6d object pose estimation using MPAAE
```
$ roslaunch assembly_part_recognition single_azure_mpaae.launch
```
5. launch kitting manager
```
$ roslaunch assembly_kitting_manager kitting_manager.launch
```

## Authors
* **Seunghyeok Back** [seungback](https://github.com/SeungBack)

## License
This project is licensed under the MIT License

## Acknowledgments
This work was supported by Institute for Information & Communications Technology Promotion(IITP) grant funded by Korea goverment(MSIT) (No.2019-0-01335, Development of AI technology to generate and validate the task plan for assembling furniture in the real and virtual environment by understanding the unstructured multi-modal information from the assembly manual.