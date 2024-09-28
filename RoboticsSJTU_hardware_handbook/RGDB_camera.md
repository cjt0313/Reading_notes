# User Guide for RGBD Camera

## 1. Introduction

This document provides an introduction to the hardware and software of the **Obbec Gemini2 RGBD camera**. It is designed for roboticists who wish to implement the camera on the wrist of a manipulator, offering guidance and answers to common queries.

## 2. Overview
One could find all details of the camera in the following links.
**Useful Links**
1. Orbbec website: https://www.orbbec.com/products/stereo-vision-camera/gemini-2/
2. Orbbec developer community: https://developer.orbbec.com.cn/
3. Official Documentation: https://vcp.developer.orbbec.com.cn/documentation?doc=doc-55
### 2.1 Camera Specifications


**NOTE:**
1. regular 5V2A power supply is fine.

| **Camera Specifications**              | |
|------------------------------------|-------------------------------------------------|
| Depth Range                        | **0.15–10m**                                       |
| Depth Resolution/FPS               | Up to **1280X800@30fps**                            |
| Depth FOV                          | H91° V66°                                       |
| RGB Resolution/FPS                 |**Up to 1920X1080@30fps**                           |
| RGB FOV                            | H86° V55°                                       |
| IMU                                | Supported                                       |
| *Precision*                        | ≤ 2% @ 2m                                       |
| Data Connection                    |**USB 3.0 Type-C**                                  |
| Power Input                        | USB 3.0 Type-C                                 |   |
| Power Consumption                  | Average <2.5W                                   |
| SDK Support                        | Orbbec SDK                                      |
| Data Output                        |**Point Cloud, Depth Map, IR & RGB**               |
| Dimensions (W*H*D)                 | 90mm x 25mm x 30mm                              |
| Weight                             | 98g                                             |
| Installation                       | Bottom: ¼-20UNC; Back: 2 x M3                   |

## 3. Orbbec SDK
The SDK provides both low-level and high-level APIs that are simple and easy to use, allowing developers to use it flexibly in different scenarios.
Official github website: https://github.com/orbbec/OrbbecSDK
| **Toolkit**              | **view data stream**|**record data** | **control camera** |
|-------------|:----------:|:----------:|:----------:|
| SDK     | yes|yes|yes|
| SDK for python      | yes| yes| yes|
| SDK for ROS2        | yes| yes| yes|
| OrbbecViewer        | yes| yes| yes|
### 4.1 Environmet Setup
https://vcp.developer.orbbec.com.cn/documentation?doc=doc-55
### 4.2 Usage
One could follow the guidance of the official documentation
**NOTE:**
1.  For OrbbecViewer: 
    1.  the raw data of imu is recorded in .csv files
    2.  the video stream data (both color and depth) is recorded in `.bag` files, ros1 is needed for decoding and playing.
    3.  the image is recorded in `.png` files.

## 5. FAQ
**[WIP]**
