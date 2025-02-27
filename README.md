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

## Code Explanation
```python
import cv2
import numpy as np

# Load video
video_path = r"C:\Users\poona\Downloads\56310-479197605_tiny.mp4"  # Replace with your video file
cap = cv2.VideoCapture(video_path)

# Initialize background subtractor
fgbg = cv2.createBackgroundSubtractorMOG2(history=500, varThreshold=25, detectShadows=True)

while True:
    ret, frame = cap.read()
    if not ret:
        break

    # Apply background subtraction
    fg_mask = fgbg.apply(frame)

    # Reduce noise with morphological operations
    kernel = cv2.getStructuringElement(cv2.MORPH_ELLIPSE, (3, 3))
    fg_mask = cv2.morphologyEx(fg_mask, cv2.MORPH_OPEN, kernel)

    # Find contours of moving objects
    contours, _ = cv2.findContours(fg_mask, cv2.RETR_EXTERNAL, cv2.CHAIN_APPROX_SIMPLE)

    for contour in contours:
        # Filter small objects based on area
        if cv2.contourArea(contour) > 500:  # Adjust threshold as needed
            # Draw bounding box
            x, y, w, h = cv2.boundingRect(contour)
            cv2.rectangle(frame, (x, y), (x + w, y + h), (0, 255, 0), 2)

    # Display results
    cv2.imshow("Original Frame", frame)
    cv2.imshow("Foreground Mask", fg_mask)

    # Exit on pressing 'q'
    if cv2.waitKey(30) & 0xFF == ord('q'):
        break

# Release resources
cap.release()
cv2.destroyAllWindows()

## Demo
Upload a demo video or GIF here.


## License
This project is licensed under the MIT License.

