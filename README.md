# Visual Inertial Odometry using Stereo MSCKF

MSCKF (Multi-State Constraint Kalman Filter) is an EKF based **tightly-coupled** visual-inertial odometry algorithm. [S-MSCKF](https://arxiv.org/abs/1712.00036) is MSCKF's stereo version. This project is a Python reimplemention of S-MSCKF, the code is directly translated from official C++ implementation [KumarRobotics/msckf_vio](https://github.com/KumarRobotics/msckf_vio).  

For algorithm details, please refer to:
* Robust Stereo Visual Inertial Odometry for Fast Autonomous Flight, Ke Sun et al. (2017)
* A Multi-State Constraint Kalman Filterfor Vision-aided Inertial Navigation, Anastasios I. Mourikis et al. (2006) 

## Requirements
* Python 3.6+
* numpy
* scipy
* cv2
* [pangolin](https://github.com/uoip/pangolin) (optional, for trajectory/poses visualization)

## Dataset
* [EuRoC MAV](http://projects.asl.ethz.ch/datasets/doku.php?id=kmavvisualinertialdatasets): visual-inertial datasets collected on-board a MAV. The datasets contain stereo images, synchronized IMU measurements, and ground-truth.  
This project implements data loader and data publisher for EuRoC MAV dataset.

## Run
With visualization:  
```
python vio.py --view --path path/to/your/EuRoC_MAV_dataset/MH_01_easy 
```
Without visualization:
```
python vio.py --path path/to/your/EuRoC_MAV_dataset/MH_01_easy   
```

## Results:
The comparison plot between estimated trajectory and ground truth is as follows:
<p align="center">
  <img src="Outputs/traj_plot.png" width="512">
</p>

The plot measuring the positional drift in all the three co-ordinates is as follows:
<p align="center">
  <img src="Outputs/pos_drift.png" width="512">
</p>

The plot measuring the orientation error in all the three dimensions is as follows:
<p align="center">
  <img src="Outputs/ori_err.png" width="512">
</p>

The output video is as follows:
<p align="center">
  <img src="Outputs/vio.gif" width="512">
</p>

## License and References
Follow [license of msckf_vio](https://github.com/KumarRobotics/msckf_vio/blob/master/LICENSE.txt). Code is adapted from [this implementation](https://github.com/uoip/stereo_msckf).