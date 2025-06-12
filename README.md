# Person Tracking Project README
This project implements a person tracking system using the YOLO (You Only Look Once) object detection and tracking framework. It processes input videos to track either a single person or multiple persons, drawing bounding boxes and movement paths with consistent colors. Two models are provided: Model 1 (using YOLOv10n and YOLOv8n) and Model 2 (using YOLOv8n exclusively). The project is designed to run in Google Colab, leveraging Ultralytics YOLO for robust tracking and OpenCV for video processing.

Table of Contents

Problem Definition
Solution Overview
Installation
Usage
File Structure
Dependencies
Output


## Problem Definition
The task is to develop a system that can track people in a video, focusing on two scenarios:

Single Person Tracking: Identify and track one person consistently throughout the video, marking their bounding box and movement path with a consistent color (red).
Multi-Person Tracking: Track up to three persons simultaneously, each with a unique bounding box and movement path in distinct colors (red, green, blue).

The system must handle challenges such as:

Occlusions or temporary disappearance of tracked persons.
Maintaining consistent tracking IDs across frames.
Visualizing tracking results clearly with bounding boxes and movement paths.
Ensuring compatibility with Google Colab for video upload, processing, and display.


## Solution Overview
The project provides two implementations (Model 1 and Model 2) to address the person tracking problem using the Ultralytics YOLO framework and OpenCV. Both models perform the following tasks:
Model 1

Single Person Tracking:
Uses YOLOv10n for detection and tracking.
Selects the first detected person in the initial frame and tracks them with a red bounding box and movement path.
Maintains tracking history to draw a continuous path.


Multi-Person Tracking:
Uses YOLOv8n for detection and tracking.
Tracks up to three persons with distinct colors (red, green, blue) for bounding boxes and paths.
Persists tracking IDs across frames to ensure consistency.



Model 2

Single Person Tracking:
Uses YOLOv8n with a higher confidence threshold (0.6 for initial detection, 0.5 for tracking) and lower IoU (0.3) for improved tracking stability.
Marks the last known position with a red circle if the target is temporarily lost.
Draws a red bounding box and movement path for the tracked person.


Multi-Person Tracking:
Uses YOLOv8n with similar parameters as single-person tracking.
Tracks up to three persons with distinct colors (red, green, blue).
Marks last known positions with colored circles if a person is temporarily lost.



## Key Features

Video Input: Accepts user-uploaded MP4 videos via Google Colab’s file upload interface.
Tracking: Utilizes YOLO’s built-in tracking (persist=True) to maintain consistent IDs across frames.
Visualization: Draws bounding boxes, labels (e.g., "Target ID" or "Person X"), and movement paths using OpenCV.
Video Output: Saves processed videos with tracking annotations and displays them in Colab using HTML5 video tags.
Compatibility: Converts videos to H.264 format using FFmpeg for Colab compatibility.
Download: Automatically downloads output videos (one_person_tracking.mp4 and multi_person_tracking.mp4 for Model 1; one_person_tracking_MODEL_2.mp4 and multi_person_tracking_MODEL_2.mp4 for Model 2).

Differences Between Models

Model Selection: Model 1 uses YOLOv10n for single-person tracking and YOLOv8n for multi-person tracking, while Model 2 uses YOLOv8n exclusively for consistency.
Tracking Robustness: Model 2 uses a higher initial confidence (0.6) and lower IoU (0.3) to improve tracking stability, especially in crowded scenes.
Lost Target Handling: Model 2 explicitly marks the last known position of a lost target with a colored circle, improving visual continuity.
Code Optimization: Model 2 includes minor improvements in code structure and error handling.


## Installation
To set up the project in Google Colab, follow these steps:

Open Google Colab:

Create a new notebook in Google Colab.


Install Dependencies:

Install the Ultralytics package and FFmpeg:!pip install ultralytics
!apt-get install ffmpeg




Upload the Code:

Copy and paste the code for Model 1 or Model 2 into a Colab cell.
Alternatively, upload a .py file containing the code and run it using !python script.py.


Prepare Input Video:

Ensure you have an MP4 video file ready for upload.
The video should contain people to track and be compatible with OpenCV’s VideoCapture.




Usage

Run the Code:

Execute the code cell containing the model (Model 1 or Model 2).
The script will prompt you to upload a video file using Colab’s file upload interface:uploaded = files.upload()




Single Person Tracking:

The script processes the video to track one person, saving the output as:
Model 1: one_person_tracking.mp4
Model 2: one_person_tracking_MODEL_2.mp4


The tracked person is marked with a red bounding box and movement path.


Multi-Person Tracking:

The script processes the video to track up to three persons, saving the output as:
Model 1: multi_person_tracking.mp4
Model 2: multi_person_tracking_MODEL_2.mp4


Each person is marked with a unique color (red, green, blue) for bounding boxes and paths.


View Results:

The processed videos are displayed in the Colab notebook using an HTML5 video player.
The videos are automatically downloaded to your local machine via:files.download(output_path)



Dependencies
The project requires the following Python packages and tools:
ultralytics
opencv-python
numpy
google-colab
ipython
ffmpeg

Install them in Google Colab using:
!pip install ultralytics opencv-python numpy google-colab ipython
!apt-get install ffmpeg


Output

Processed Videos:
Single Person Tracking: A video with one person tracked, marked with a red bounding box, label (e.g., "Target ID: X"), and red movement path.
Multi-Person Tracking: A video with up to three persons tracked, each with a unique color (red, green, blue) for bounding boxes, labels (e.g., "Person X"), and movement paths.


Filenames:
Model 1: one_person_tracking.mp4, multi_person_tracking.mp4
Model 2: one_person_tracking_MODEL_2.mp4, multi_person_tracking_MODEL_2.mp4


Display: Videos are displayed in the Colab notebook with controls for playback.
Download: Output videos are automatically downloaded to the user’s local machine.



