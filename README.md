# RTPS-Camera-Object-Detection-Api
An API for IP camera video streaming and object detection with a faster-rcnn.

Built with FastAPI and PyTorch.
# Install
```bash
python3 -m venv venv
source venv/bin/activate
pip3 install -r requirements.txt
uvicorn app:app
```
## Demo:
![ezgif com-gif-maker (7)](https://user-images.githubusercontent.com/56324869/126047793-9cfb412a-9822-4b7a-b575-c225487cacb0.gif)
# Environment variables
This API was built using Intelbras cameras, this variables are related to the rtsp url, if you use a different type of camera, there's a variable **CUSTOM_URL** where you can just pass the entire url for your cameras at rtsp.

If you use Intelbras Cameras, you can just use the following
Create a .env file with the following variables:
```env
USER= 
PASSWORD=
CAMERA_IP=
RTSP_PORT=
PORT=
ENVIRONMENT_NAME=
```
- USER: Your user within your camera system.
- PASSWORD: Your password within the system.
- CAMERA_IP: Your camera IP.
- RTSP_PORT: 554 as default, but you can change if you changed in your system.
- PORT: Api port, 8000 as default.
- ENVIRONMENT_NAME: Will disable swagger and redocs for FastAPI if starts with "production". Default is None.

# Routes
- /cam

Params: channel

Description: open the camera x (1,2,3,4...).

Example: 127.0.0.1:8000/cam?channel=5

# Model

The model running here is just a faster-rcnn with a resnet50 backbone as the cnn, available at torchvision and trained using COCO dataset.

# TODO:
- Custom set of categories on detection.
- Track desired objects in a specific space of time.
- Interface (now its just buffering the camera frames into the model and displaying at the cam route).