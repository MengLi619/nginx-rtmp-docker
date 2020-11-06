## nginx-rtmp-ffmpeg
This project forked from [tiangolo/nginx-rtmp-docker](https://github.com/tiangolo/nginx-rtmp-docker), 
and add ffmpeg package.

## Run Docker
```shell script
docker run \
    --name nginx-rtmp-ffmpeg \
    -d \
    --rm \
    -p 1935:1935 \ 
    -v "$(pwd)/nginx.conf":/etc/nginx/nginx.conf \
    registry.cn-hongkong.aliyuncs.com/mengli/nginx-rtmp-ffmpeg:latest
```
    
## Run Docker (GPU support)
1. Install cuda driver    
https://developer.nvidia.com/cuda-downloads
2. Install docker    
https://docs.docker.com/engine/install/ubuntu
3. Install nvidia-docker2
    ```shell script
    distribution=$(. /etc/os-release;echo $ID$VERSION_ID)
    curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | sudo apt-key add -
    curl -s -L https://nvidia.github.io/nvidia-docker/$distribution/nvidia-docker.list | sudo tee /etc/apt/sources.list.d/nvidia-docker.list
    sudo apt-get update    
    sudo apt-get install -y nvidia-docker2
    sudo systemctl restart docker
    ```
4. Run docker with nvidia runtime
    ```shell script
    docker run \
        --name nginx-rtmp-ffmpeg \
        --runtime nvidia \
        -d \
        --rm \
        -p 1935:1935 \ 
        -v "$(pwd)/nginx.conf":/etc/nginx/nginx.conf \
        registry.cn-hongkong.aliyuncs.com/mengli/nginx-rtmp-ffmpeg:latest-gpu
    ```
