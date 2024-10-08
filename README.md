# Docker setup to run intel realsense
## Setup
Building the container:
```
docker build -t ros-realsense .
```

Run the container: 
```
docker run --rm  --net=host --privileged \
    --env="DISPLAY=$DISPLAY" \
    --env="QT_X11_NO_MITSHM=1" \
    --volume=/dev:/dev \
    -it --name rs_container ros-realsense \
    /bin/bash -i -c 'roslaunch realsense2_camera rs_rgbd.launch enable_pointcloud:=true align_depth:=false depth_registered_processing:=true align_depth:=true' 
```

Open rviz:
```
docker exec -it rs_container /bin/bash -i -c 'rviz'
```

Open another session for interaction:
```
docker exec -it rs_container /bin/bash
```
