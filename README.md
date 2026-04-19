# Fatigue-driving-detection-project
# YOLOv11-Based Driver Fatigue Detection System

## Overview

This project is a real-time **driver fatigue detection system** built on top of the **YOLOv11** object detection framework. The main goal of the project is to improve driving safety by monitoring the driver’s facial condition, eye status, mouth movement, and head behavior during a driving session. By combining modern computer vision techniques with lightweight deployment logic, the system is designed to detect signs of drowsiness, inattentiveness, and possible fatigue-related behavior in a fast and practical way.

The application is intended for research, prototyping, academic demonstration, and intelligent transportation scenarios. It can process webcam streams, prerecorded videos, or external camera input to identify fatigue-related visual cues such as prolonged eye closure, frequent yawning, head drooping, and distraction patterns. Once the system determines that the driver may be in a fatigued state, it can trigger visual or audio alerts to warn the user in time.

This repository demonstrates how YOLOv11 can be adapted beyond general object detection tasks and applied to a more specialized human-centered safety problem. The project focuses not only on detection accuracy, but also on real-time responsiveness, modular design, deployment flexibility, and usability in practical environments.

---

## Background

Driver fatigue is one of the major hidden causes of road accidents worldwide. Unlike sudden mechanical failures, fatigue develops gradually and often goes unnoticed by drivers themselves. Signs such as slow blinking, long eye closure, repeated yawning, reduced facial activity, and unstable head posture may appear before a serious driving error occurs. Because of this, fatigue detection has become an important research topic in intelligent transportation systems, edge AI devices, and in-vehicle monitoring applications.

Traditional fatigue detection methods often rely on handcrafted features or wearable sensors. Although these methods can be effective in controlled settings, they may be inconvenient, expensive, or difficult to deploy at scale. With the rapid development of deep learning and real-time object detection, vision-based fatigue monitoring has become a more accessible and scalable solution. YOLO-based models are especially suitable for this purpose because they offer a strong balance between speed and accuracy.

This project explores the use of YOLOv11 as the backbone for detecting fatigue-related features in the driver’s face and upper-body region. By detecting and analyzing visual states frame by frame, the system can provide timely warnings while maintaining efficient inference performance.

---

## Objectives

The main objectives of this project are listed below:

- Build a real-time fatigue detection pipeline based on YOLOv11.
- Detect fatigue-related facial and behavioral features from live video streams.
- Support different input sources such as webcam, local video files, and surveillance-style camera feeds.
- Provide an extensible and modular code structure for further experimentation and optimization.
- Demonstrate how object detection models can be adapted for practical intelligent safety applications.
- Enable future integration with edge devices, embedded platforms, or smart vehicle systems.

---

## Core Features

### 1. Real-Time Detection
The system is capable of running in real time on video streams and webcam input. It processes each frame, detects predefined fatigue-related classes, and updates the fatigue state continuously.

### 2. YOLOv11-Based Architecture
The core detection model is built using YOLOv11, allowing the project to benefit from strong detection speed, flexible training workflows, and robust performance across different deployment environments.

### 3. Fatigue-Related State Recognition
The model can be configured to detect classes such as:

- open eyes
- closed eyes
- yawning
- normal face state
- head down
- distracted posture
- phone usage while driving
- prolonged inattentive state

These categories can be expanded depending on the annotation strategy and dataset design.

### 4. Alert Mechanism
When the system identifies fatigue patterns that exceed predefined thresholds, it can generate warning messages, on-screen indicators, or audio alarms. This helps simulate a real driver assistance workflow.

### 5. Flexible Input Support
The project supports multiple input modes, including:

- laptop or desktop webcam
- prerecorded video files
- USB cameras
- IP camera streams
- external embedded vision modules

### 6. Modular Project Design
The codebase is organized in a modular way so that dataset preparation, model training, inference, tracking, and alert logic can be modified independently.

### 7. Easy Customization
Users can easily retrain the model on their own datasets, modify class labels, tune detection thresholds, and integrate additional fatigue indicators if needed.

---

## System Workflow

The general workflow of the project is as follows:

1. Capture image frames from a webcam, video file, or other camera source.
2. Preprocess the incoming frames for inference.
3. Run the YOLOv11 model to detect fatigue-related states or facial behavior classes.
4. Analyze the detected results over time rather than relying on a single frame.
5. Apply fatigue judgment logic based on temporal thresholds, confidence levels, and event frequency.
6. Trigger a warning if the driver appears to be fatigued or inattentive.
7. Display the processed output with annotations, labels, and system status information.

This workflow allows the project to move from simple per-frame detection toward a more realistic fatigue decision pipeline.

---

## Model Design

The model in this project is centered around YOLOv11 due to its efficiency and adaptability. While standard object detection typically focuses on larger targets such as vehicles, pedestrians, or traffic signs, this project adapts the same detection philosophy to more subtle fatigue-related visual states.

The YOLOv11 detector is trained to identify key facial or behavioral categories associated with fatigue. In practical use, single-frame predictions are not always enough to determine true fatigue, since blinking, mouth movement, and head motion are normal behaviors in driving. Therefore, the project introduces a higher-level decision layer that accumulates evidence over time.

For example:

- A single detected yawn does not necessarily mean fatigue.
- A short eye closure may simply be a blink.
- A brief downward head movement may be natural posture adjustment.

To reduce false alarms, the system uses temporal logic such as counting consecutive frames, measuring event duration, and combining multiple fatigue indicators before issuing a warning. This approach improves stability and makes the detection results more practical for real-world use.

---

## Dataset Description

The training dataset used in this project is designed around fatigue-related driver states. Since fatigue detection is a specialized task, the dataset may include annotated driver images or video frames under different lighting conditions, camera angles, and fatigue levels.

Typical dataset categories may include:

- eyes open
- eyes closed
- yawning
- head tilted down
- distracted
- normal driving posture
- using phone
- no driver / invalid frame

The data may come from manually collected video clips, public fatigue-driving datasets, simulated driving recordings, or self-annotated image sets. To improve robustness, the dataset should ideally cover the following variations:

- daytime and nighttime lighting
- glasses and sunglasses
- different skin tones and facial structures
- varied camera positions
- multiple head angles
- partial occlusion
- different vehicle interior environments

Data augmentation can also be applied during training, including brightness changes, blur, rotation, scaling, and contrast adjustments, in order to make the model more resilient under real-world conditions.

---

## Project Structure

A typical project structure may look like this:

```bash
driver-fatigue-detection/
├── datasets/
│   ├── images/
│   ├── labels/
│   └── data.yaml
├── models/
│   └── yolov11_custom.pt
├── runs/
│   ├── train/
│   └── detect/
├── src/
│   ├── train.py
│   ├── detect.py
│   ├── alert.py
│   ├── utils.py
│   └── fatigue_logic.py
├── demo/
│   ├── sample_video.mp4
│   └── screenshots/
├── requirements.txt
├── README.md
└── main.py
