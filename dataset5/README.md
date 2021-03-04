

## New Dataset 

A new challenging winter dataset with 6 cameras, snow covered background and multiple drones.

| Dataset | 3D trajectory | 3D orientation | Synchronization | Camera locations | 2D labels |
| ------- | ------------- | -------------- | --------------- | ---------------- | --------- |
| 5 (new) | Yes           | Yes            | Yes             | Yes              | Not yet   |

| # of cameras | # of drones | Flight duration |
| ------------ | ----------- | --------------- |
| 6            | 3           | ~ 10min         |

<img src="assets/dataset_overview.jpg" align="left" width="800" alt="Camera 5 trajectory">

-----

### Dataset structure

* videos
  * cam0
    * cam0.mp4
    * cam0_frame_ts.txt (Framewise timestamp in project time system)
  * cam1
  * cam...
* calibration
* camera-locations
  * campos.txt (Each camera's position in project local coordinate system)
* pose 
  * fused_pose.txt (Drone center's pose in project local coordinate system with its corresponding timestamp in project time system. The accuracy estimation is also provided. The pose can be regarded as the ground truth pose of the drone.)
* raw-data
  * drone_log (Drone's raw log file in Pixhawk's format)
  * tps_tracking (Total station's raw measurements)
  * leverarm_prism_in_body.txt (Prism's relative position to drone center)
  * tran_mat_tps2local.txt (Transformation matrix from total station to project local coordinate system)
  * local_origin_in_wgs84.txt (The coordinate of the project local coordinate system's origin in WGS84)
  * project_time_origin_in_utc.txt (UTC+1 time of project time system's origin)
  * sync_coefficients_cam2pc.txt (Synchronization coefficients for each camera with regards to project time system)
  * measured_coordinates.csv (Raw measurement of cameras nd resection control points' coordinates)

---

[Link to the original dataset (seq. 1-4)](https://github.com/CenekAlbl/drone-tracking-datasets)

[Link to the data collection pipeline and codes](https://github.com/YuePanEdward/IPA-GTDroneTraj)

