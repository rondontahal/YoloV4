# YoloV4
Deep-stream Pipeline and Configuration Files
1) To Run ssh into jetson Nano

ssh user_name@port_id

2) Nvidia Guide for Setting up Deepstream
https://github.com/NVIDIA-AI-IOT/deepstream_python_apps
https://docs.nvidia.com/metropolis/deepstream/dev-guide/

3)Loading Container 


mkdir my_apps

mkdir Project

sudo docker run --runtime nvidia -it --rm --network host \
    -v /tmp/.X11-unix/:/tmp/.X11-unix \
    -v /tmp/argus_socket:/tmp/argus_socket \
    -v ~/my_apps:/dli/task/my_apps \
    -v ~/Project:/dli/task/deepstream/sources/project \
    --device /dev/video0 \
    path_to_container
