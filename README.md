# AquaVision 
Autonomous Robotic Platform for Real-Time Water Quality Monitoring

AquaVision is a project I worked on to address the problem of plastic pollution and water quality monitoring in aquatic ecosystems. Traditional water monitoring methods rely on manual sampling and laboratory analysis, which are slow, expensive, and cover only limited locations.

In this project, we designed a compact autonomous floating robotic platform that can move across water bodies and continuously monitor chlorophyll-a concentration and floating plastic debris in real time.

The system combines hyperspectral sensing, computer vision, edge AI computing, and autonomous navigation to create a scalable solution for environmental monitoring.

# Problem Statement

Plastic pollution and algal blooms are increasing rapidly in rivers, lakes, and oceans.

Some major limitations of existing monitoring systems include:

Water samples are usually collected only 1–2 times per week

Monitoring is performed at fixed locations

Lab analysis takes 24–72 hours

Less spatial coverage (generally <5 km radius)

Requires high manpower and laboratory costs

According to environmental reports:

Around 11 million tons of plastic enter oceans every year

Nearly 80% of this plastic originates from rivers and lakes

Increasing chlorophyll concentration is strongly linked with harmful algal blooms

Because of these limitations, continuous and automated monitoring systems are needed.

# Proposed Solution

To solve this problem, we developed AquaVision, an Autonomous Surface Vehicle (ASV) capable of monitoring water quality and plastic pollution in real time.

The platform integrates multiple sensors and onboard computing to collect, process, and transmit environmental data.

Main capabilities of the system:

Real-time chlorophyll-a estimation

Floating plastic detection and classification

Autonomous navigation

GPS-tagged pollution mapping

Remote monitoring through dashboard

# System Architecture

The AquaVision system consists of three main layers.

1. Edge Hardware Layer

This layer includes the physical components mounted on the robotic platform.

Key components used:

Hyperspectral Radiometer (400–1000 nm)

RGB Camera

LiDAR Sensor

IMU

GPS Module

LoRa Communication Module

NVIDIA Jetson Nano

Solar Panel

Li-ion Battery Pack

BLDC Propellers

The hull of the platform is built using recycled HDPE, making it lightweight, corrosion-resistant, and environmentally sustainable.

2. Edge AI Processing Layer

All sensor data is processed onboard using the Jetson Nano.

Processing steps include:

Spectral data preprocessing

Noise filtering

Feature extraction

Computer vision for plastic detection

Autonomous navigation algorithms

This allows the system to perform real-time analysis without relying entirely on cloud connectivity.

3. Cloud & Dashboard Layer

When network connectivity is available, the collected data is uploaded to the cloud.

This allows:

Data storage

Model improvement

Environmental analytics

Visualization through a monitoring dashboard

The dashboard displays:

Chlorophyll concentration distribution

Plastic pollution locations

Environmental monitoring insights

Dashboard Link
https://www.figma.com/make/BD4xYXpUbujyMAYHktA4DD/SIH-25-AQUAVISION-DASHBOARD

# Machine Learning Models

Two main machine learning pipelines were developed for this project.

Chlorophyll-a Detection

The hyperspectral sensor captures reflectance data in the 400–1000 nm wavelength range.

Processing pipeline:

Data Collection
Spectral reflectance captured using hyperspectral radiometer.

Preprocessing
Noise removal and extraction of Red–NIR spectral bands.

Feature Extraction
Principal Component Analysis (PCA) for dimensionality reduction.

Model Training

Algorithms used:

Random Forest

Gradient Boosting

Voting Regressor

Hyperparameter Tuning
GridSearchCV used to optimize model parameters.

Model performance:

# R² score = 0.89

# Output:

Real-time mapping of chlorophyll-a concentration with GPS tagging.

Plastic Detection

Floating plastic debris is detected using image data from the onboard RGB camera.

# Processing pipeline:

Image preprocessing and dataset labeling

Object detection using YOLOv8

Two-stage classification:

Stage 1
Macro plastics vs Micro plastics

Stage 2
Material classification:

PE

PP

PET

HDPE

PTFE

PVC

Model performance:

mAP@50 = 90.3%

Precision = 0.92

# Output:

Real-time detection and mapping of plastic debris.

Navigation System

The platform uses multiple sensors for autonomous navigation.

Navigation pipeline:

LiDAR scans surroundings to detect obstacles

UKF filter removes noise and tracks objects

VFH/A algorithm calculates safe navigation path

Propellers execute the movement commands

This enables the robot to move safely across rivers and lakes.

Hull Design

For the floating platform, we compared different hull types:

Monohull

Catamaran

Trimaran

After evaluation, Catamaran hull design was selected because it provides:

Better stability

Larger deck area

Higher payload capacity

Lower hydrodynamic drag

# Key Features

Autonomous environmental monitoring

Real-time chlorophyll concentration mapping

AI-based plastic detection

GPS-based pollution tracking

Edge AI processing using Jetson Nano

LoRa long-range telemetry

Solar-powered energy system

Sustainable recycled HDPE hull

Repository Contents
AquaVision
│
├── chlorophyll_model
│   └── ML pipeline for chlorophyll prediction
│
├── plastic_detection
│   └── YOLOv8 detection model
│
├── edge_processing
│   └── sensor integration and onboard processing
│
├── dashboard
│   └── visualization interface
│
└── datasets
Project Resources

Research Repository
https://drive.google.com/drive/folders/1ObHck8ysI8vkpYkH5dKIQoijMqAogVwJ?usp=sharing

Chlorophyll Model Implementation
https://colab.research.google.com/drive/1gsbV323A5NfXGnf4YZ1ztKU1EiQKCGFd

Plastic Detection Model
https://app.roboflow.com/amazonml-96xmr/plastic-detection-sih-mis4v/models

# Team AquaVision

Tejas Shriramwar

Pranay Shrivastava

Milind Kumawat

National Institute of Technology Raipur
