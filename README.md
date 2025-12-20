# Sentinel-AI (MST_3)
Voice & Motion Activated Multimodal Edge Security System

**Course:** ECE 6380 – AI Hardware Design  
**Instructor:** Prof. Mircea R. Stan  
**Team:** MST_3  
**Members:** Md Nasim Afroj Taj, Mughesh Kumar NR, Uttam Kumar Saha  

---

## Overview
Sentinel-AI is a **privacy-preserving, event-driven edge security system** designed to run entirely on local hardware. The system performs **real-time face detection and face recognition** using lightweight deep learning models and is targeted for deployment on the **NVIDIA Jetson Nano**.

Unlike traditional CCTV or cloud-based surveillance systems, Sentinel-AI avoids continuous recording and cloud dependency, reducing **energy consumption, latency, and privacy risks**.

---

## Key Features
- Fully **offline edge AI inference**
- Real-time **face detection and recognition**
- Lightweight, browser-based implementation using **face-api.js**
- Designed for **Jetson Nano–class hardware**
- Simple dataset management (no retraining required)

---

## Hardware Platform
- **NVIDIA Jetson Nano (4GB)**
- USB webcam (UVC compliant)
- Local storage (microSD)
- Optional peripherals (planned): microphone, motion sensor, buzzer

All computation is performed locally on the Jetson Nano.

---

## Software Stack
- JavaScript + HTML
- **face-api.js** (SSD MobileNet + face embeddings)
- WebRTC (`getUserMedia`) for camera access
- Local HTTP server for execution

---

## System Workflow
1. Camera stream initialized on Jetson Nano  
2. Faces detected in real time  
3. Facial embeddings generated  
4. Detected faces matched against local labeled dataset  
5. Bounding boxes and identity labels displayed  

*(Audio and motion triggers are implemented in logic but not physically demonstrated.)*

---

## Dataset
- Small, local dataset (2–4 images per person)
- Stored as labeled folders
- No model training required
- New users added by placing images in dataset folder

---

## Results
- Real-time face detection with smooth bounding boxes
- Accurate recognition of known users under good lighting
- Unknown faces correctly labeled
- Fully offline operation demonstrated on Jetson Nano

---

## Challenges & Limitations
- Performance sensitive to lighting conditions
- Small dataset limits recognition robustness
- Audio, motion sensor, and buzzer not physically integrated
- Browser-based pipeline not fully GPU-optimized

---

## Future Work
- Integrate microphone, motion sensor, and buzzer
- Implement wake-word and motion-triggered activation
- Improve dataset diversity
- Optimize pipeline using GPU acceleration / TensorRT
- Add alerts and notification mechanisms

---

## How to Run (Quick)
1. Clone the repo on Jetson Nano  
2. Place face-api.js models in `models/`  
3. Add labeled images in `lables/<name>/`  
4. Start local server:
   ```bash
   python3 -m http.server 8000
   ```
5. Open http://localhost:8000 in Chromium
6. Allow camera access
(See detailed instructions in the full documentation.)

References
* face-api.js: https://github.com/justadudewhohacks/face-api.js
* NVIDIA Jetson Nano: https://developer.nvidia.com/embedded/jetson-nano-developer-kit
