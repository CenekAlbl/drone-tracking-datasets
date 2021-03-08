

## Dataset 5

A new challenging winter dataset with 6 cameras, snow covered background and multiple drones.

| Dataset | 3D trajectory | 3D orientation | Synchronization | Camera locations | 2D labels |
| ------- | ------------- | -------------- | --------------- | ---------------- | --------- |
| 5 (new) | Yes           | Yes            | Yes             | Yes              | Not yet   |

| # of cameras | # of drones | Flight duration |
| ------------ | ----------- | --------------- |
| 6            | 3           | ~ 10min         |

<img src="assets/dataset_overview.jpg" align="center" width="800" alt="Dataset5 overview">

-----



### Dataset structure

* Videos
  * Cam0
    * cam0.mp4
    
    * cam0_frame_ts.txt (Framewise timestamp in project time system)
    
      **Format:** Frame_ID Timestamp(s)
    
  * Cam1
  
  * Cam...
  
  * Cam5
  
* Calibration  (calibration video and results for each camera)

* Camera-locations
  
  * campos.txt (Each camera's position in project local coordinate system)
  
    **Format:** Cam_ID X(m) Y(m) Z(m)
  
* Pose 
  
  * fused_pose.txt (This file contains the Pixhawk drone’s pose at its body center in project local coordinate system with its corresponding timestamp in project time system. The positioning accuracy evaluation is also provided. The pose can be regarded as the ground truth pose of the drone.)
  
    **Format:** Timestamp(s) X(m) Y(m) Z(m) Roll(deg) Pitch(deg) Yaw(deg) Std.X(m) Std.Y(m) Std.Z(m) TrackingStatus
  
* Detections

  * Drone0

    * cam0.txt (frame-wise ground truth 2D label of the drone’s center in the image coordinate system. The coordinate would be [0,0] when the drone does not exists in the frame)

      **Format:** Frame_ID X(pix) Y(pix)

    * cam...

    * cam5.txt

  * Drone1

  * Drone2

* Raw-data
  * drone_log (Drone’s raw log file in Pixhawk’s format, containing the raw measurements of onboard GNSS and IMU)

  * tps_tracking (Total station's raw measurements)

  * leverarm_prism_in_body.txt (Prism's relative position to drone center)

  * tran_mat_tps2local.txt (Transformation matrix from total station frame to project local ENU frame)

  * local_origin_in_wgs84.txt (The coordinate of the project local coordinate system's origin in WGS84)

  * project_time_origin_in_utc.txt (UTC+0 time of project time system's origin)

  * sync_coefficients_cam2pc.txt (Synchronization coefficients for each camera with regards to project time system)

    **Format:** Cam_ID Time_scale Time_shift(s)

  * measured_coordinates.csv (Raw measurement of cameras nd resection control points' coordinates)

* cameras.txt  (description of each camera according to its ID)

* drones.txt (description of each drone according to its ID)

---

[Link to the original dataset (seq. 1-4)](https://github.com/CenekAlbl/drone-tracking-datasets)

[Link to the data collection pipeline and codes](https://github.com/YuePanEdward/IPA-GTDroneTraj)

