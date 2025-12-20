# Sentinel-AI  
Voice & Motion Activated Multimodal Edge Security System

Sentinel-AI is an event-driven, privacy-focused edge security system designed to run fully offline on embedded AI hardware such as the NVIDIA Jetson Nano. Unlike traditional CCTV systems that record continuously, Sentinel-AI activates only when needed and combines vision and audio intelligence to make contextual security decisions at the edge.

This project was developed as part of **MST_3 – AI Hardware Project**.

---

## Motivation

Conventional surveillance systems suffer from:
- Continuous recording and high power consumption  
- Large and unnecessary storage usage  
- Cloud dependence leading to privacy risks and latency  
- Lack of contextual awareness  

Sentinel-AI addresses these issues by providing:
- Event-driven activation  
- Fully offline inference  
- Multimodal intelligence (vision + audio)  
- Lightweight, edge-friendly design  

---

## Key Features

- Real-time face detection and recognition  
- Lightweight MTCNN-based pipeline  
- Fully offline operation (no cloud dependency)  
- Requires only **4 images per identity**  
- Designed for Jetson-class edge hardware  
- Privacy-preserving local inference  

---

## System Workflow

**Listen → See → Decide → Act**

1. Audio or motion trigger (planned / future work)  
2. Camera activates for face detection  
3. Face recognition using local models  
4. Decision taken locally (record, alert, log)  

---

## Hardware Requirements

- NVIDIA Jetson Nano  
- USB Camera  
- Microphone (optional, future integration)  
- MicroSD card or SSD  
- Power supply  

---

## Software Stack

- HTML, CSS, JavaScript  
- `face-api.js` for face detection and recognition  
- WebRTC for camera access  
- MTCNN (P-Net, R-Net, O-Net)  
- Fully local browser-based inference  

---

## Repository Structure

