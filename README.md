# Set Up Nano
Deep-stream Pipeline and Configuration Files

# To Run ssh into jetson Nano

ssh user_name@port_id

# Nvidia Guide for Setting up Deepstream
https://github.com/NVIDIA-AI-IOT/deepstream_python_apps

https://docs.nvidia.com/metropolis/deepstream/dev-guide/

# Relevent Directories 
mkdir my_apps

mkdir Project

# Load Container 

sudo docker run --runtime nvidia -it --rm --network host \
    -v /tmp/.X11-unix/:/tmp/.X11-unix \
    -v /tmp/argus_socket:/tmp/argus_socket \
    -v ~/my_apps:/dli/task/my_apps \
    -v ~/Project:/dli/task/deepstream/sources/project \
    --device /dev/video0 \
    path_to_container

# Setting up YoloV4

cd /opt/nvidia/deepstream/deepstream/sources/project
#Make 
mkdir weights && cd weights

#Store Custom weights and Configuration file into weights folder

https://mcmasteru365.sharepoint.com/:u:/r/sites/RTA2SmartDevicesandSensors/Shared%20Documents/RTA%202.3%20Single%20IoT%20Edge%20Appliance/YOLO%20weights/yolo-obj_best_n4.weights?csf=1&web=1&e=252ABk

# Building Custom Yolo

cd /opt/nvidia/deepstream/deepstream/sources/project


git clone https://github.com/marcoslucianops/DeepStream-Yolo.git

cp -r /opt/nvidia/deepstream/deepstream/sources/project/DeepStream-Yolo/native /opt/nvidia/deepstream/deepstream/sources/yolo

cd /opt/nvidia/deepstream/deepstream/sources/yolo

CUDA_VER=10.2 make -C nvdsinfer_custom_impl_Yolo


Running Program Inside of Deepstream Container 



# Run the app with YOLO
MY_APPS = '/opt/nvidia/deepstream/deepstream/sources/deepstream_python_apps/my_apps'

OUTPUT_PATH_EX1 = '/opt/nvidia/deepstream/deepstream/sources/deepstream_python_apps/my_apps/OutputFiles/file_name.mp4'

!cd $MY_APPS/Program_Dir \
    && python3 deepstream_test3_mp4_out-Copy1.py -o $OUTPUT_PATH_EX1 -i \
        file://$MY_APPS/InputFiles/File_Name.mp4
        
# View video Output

#Watch the saved video
import os
from IPython.display import Video
OUTPUT_PATH_EX1 = '/opt/nvidia/deepstream/deepstream/sources/deepstream_python_apps/my_apps/OutputFiles/output7.mp4'
video_path = os.path.relpath(OUTPUT_PATH_EX1)
Video(video_path, width = 680, height = 480)

# Next Steps

The plan is get all this data into one "image file" which can run a container with all the dependencies prebuilt onto any system
