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

4) Setting up YoloV4

4.1
cd /opt/nvidia/deepstream/deepstream/sources/project
#Make 
mkdir weights && cd weights

#Store Custom weights and Configuration file into weights folder

4.2) Building Custom Yolo

cd /opt/nvidia/deepstream/deepstream/sources/project


git clone https://github.com/marcoslucianops/DeepStream-Yolo.git

cp -r /opt/nvidia/deepstream/deepstream/sources/project/DeepStream-Yolo/native /opt/nvidia/deepstream/deepstream/sources/yolo

cd /opt/nvidia/deepstream/deepstream/sources/yolo

CUDA_VER=10.2 make -C nvdsinfer_custom_impl_Yolo

