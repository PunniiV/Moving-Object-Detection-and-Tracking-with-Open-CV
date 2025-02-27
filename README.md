# Moving-Object-Detection-and-Tracking-with-Open-CV

# Motion Detection using OpenCV

## Overview
This project implements a **Motion Detection System** using **OpenCV**. It detects moving objects in a video by applying **background subtraction (MOG2)** and highlights them using bounding boxes.

## Features
- ✅ **Background Subtraction**: Uses OpenCV’s MOG2 algorithm to detect motion.
- ✅ **Noise Reduction**: Applies morphological operations to reduce false detections.
- ✅ **Object Tracking**: Detects moving objects and marks them with bounding boxes.
- ✅ **Real-Time Processing**: Efficiently processes video frames for motion detection.

## Use Cases
- 🔍 **Security Surveillance** – Detect intruders in CCTV footage.
- 🚗 **Traffic Monitoring** – Track vehicle movement on roads.
- 📊 **Smart Systems** – Automate object detection in various applications.

## Installation
1. **Clone the Repository**
   ```sh
   git clone https://github.com/yourusername/motion-detection-opencv.git
   cd motion-detection-opencv
   ```
2. **Install Dependencies**
   ```sh
   pip install opencv-python numpy
   ```

## Usage
1. **Place your video file in the project directory.**
2. **Update the `video_path` variable in the script:**
   ```python
   video_path = r"C:\Users\poona\Downloads\56310-479197605_tiny.mp4"
   ```
3. **Run the script:**
   ```sh
   python motion_detection.py
   ```
4. **Press 'q' to exit the video display.**

.


## License
This project is licensed under the MIT License.

