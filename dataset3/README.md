# Additional dataset info

## Camera locations
We measured the camera locations for dataset 3 directly with a survey-grade GNSS receiver (Trimble R8). The estimated positioning accuracy is 9 mm, but since we could not make the antenna centre coincide with the projection centres of the different consumer devices, we conservatively estimate that the ground truth coordinates of the camera centres have an accuracy better than 5 cm.

The camera locations in an arbitrary XYZ Euclidean system are in the folder camera-locations. Each line contains the X Y and Z coordinate and the order corresponds to the one in cameras.txt.

## Ground truth synchronization parameters
We provide ground truth time shift (beta) and time scaling parameters (alpha) between the camera streams. 

### Time scale (alpha)
|Ref. camera | 0 | 1 | 2 | 3 | 4 | 5 |
| --- | --- | --- | --- | --- | --- | --- | 
| 0 | 1.0000 |0.5005 |0.4960 |0.4171 |0.5000 |0.8341 |
| 1 | 1.9982 |1.0000 |0.9910 |0.8333 |0.9990 |1.6667 |
| 2 | 2.0163 |1.0091 |1.0000 |0.8409 |1.0081 |1.6819 |
| 3 | 2.3978 |1.2000 |1.1892 |1.0000 |1.1988 |2.0000 |
| 4 | 2.0001 |1.0010 |0.9919 |0.8342 |1.0000 |1.6683 |
| 5 | 1.1989 |0.6000 |0.5946 |0.5000 |0.5994 |1.0000 |

### Time shift (beta)
|Ref. camera | 0 | 1 | 2 | 3 | 4 | 5 |
| --- | --- | --- | --- | --- | --- | --- | 
| 0 | 0.00 |1013.95 |546.98 |251.16 |961.02 |137.51 |
| 1 | -2026.04 |0.00 |-457.83 |-593.82 |-51.96 |-1552.47 |
| 2 | -1102.90 |461.99 |0.00 |-208.81 |409.59 |-782.45 |
| 3 | -602.21 |712.57 |248.32 |0.00 |659.93 |-364.81 |
| 4 | -1922.12 |52.01 |-406.29 |-551.00 |0.00 |-1465.78 |
| 5 | -164.85 |931.45 |465.22 |182.40 |878.60 |0.00 |

Such that for each row: frame i in the reference camera corresponds to frame j = alpha * i + j in the other cameras.

The camera ID's correspond to the order of cameras in cameras.txt file.

### WARNING!
Unfortunately, some of the smartphone cameras were recording at a variable frame rate. It is a feature of those smarthpones and cannot be changed. In some cases the fluctuation in FPS was very high, e.g. Mate 7 in this dataset. If this is a problem, we suggest to extract the timestamps of each frame using ffprobe using the following command:

```
ffprobe -select_streams v:0 -of default=noprint_wrappers=1:nokey=1 -show_entries  packet=pts_time filename.mp4
```

Having the timestamps for each frame, one can use them in their pipeline. For our purposes, we required a fixed frame rate input so we remapped the detected image points using linear interpolation such that they would be 30fps fixed frame rate.

The time mapping parameters in the tables above are also computed with the remapped frame rate of Mate 7 to 30fps.

If in doubt, please contact us for details.

