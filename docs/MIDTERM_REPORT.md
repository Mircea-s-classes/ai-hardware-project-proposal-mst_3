# Sentinel-AI – Midterm Report
### Voice & Motion Activated Multimodal Edge Security System  
**MST_3 · Fall 2025**

---

## 1. Project Overview

Sentinel-AI is an offline, context-aware, voice-activated security camera built for the NVIDIA Jetson Nano.  
Traditional CCTV systems record continuously, wasting power and storage while exposing private data to cloud servers.  
Sentinel-AI solves this by creating a **smart, local, multimodal surveillance system** that activates **only when triggered**, ensuring low power use, high privacy, and intelligent edge processing.

---

## 2. Motivation

- Continuous CCTV recording → energy + storage waste  
- Cloud surveillance → privacy risk + latency  
- Many systems lack contextual intelligence  

**Sentinel-AI addresses all three:** it listens, thinks, and acts only when needed, running fully offline.

---

## 3. System Design

### Multimodal Triggers
- Wake-word detection (Mycroft Precise)  
- PIR motion sensing  
- Camera activation (Pi Cam / USB camera)

### Core Processing Modules
- Vision inference on Jetson Nano (TensorRT)  
- MTCNN for face detection (P-Net → R-Net → O-Net)  
- Optional YOLOv5-Nano object detection  
- Lightweight, low-latency audio pipeline

### Outputs
- LED/Buzzer alerts  
- Optional Flask dashboard  
- Local clip storage triggered only by events  

---

## 4. Midterm Progress

### ✔ Wake-Word Detection
- Mycroft Precise integrated  
- Reliable activation under 300 ms  
- Fully offline

### ✔ Motion Detection
- PIR sensor configured via GPIO  
- Works as secondary trigger  
- Minimal power consumption

### ✔ Face Detection (MTCNN)
- Multi-stage CNN pipeline functioning  
- Bounding box + landmark extraction working  
- Runs smoothly on Jetson Nano

### ✔ End-to-End Demo
- Wake-word → camera activation → face detection  
- Demonstrated functional integration of all modules  

---

## 5. System Architecture Diagram

```mermaid
flowchart TD
    A[Wake-Word Module] -->|Trigger| C[Jetson Nano]
    B[PIR Motion Sensor] -->|Trigger| C
    C --> D[Camera Capture]
    D --> E[Vision Inference (TensorRT)]
    E --> F[Face/Object Detection]
    F --> G[Local Alerts (LED/Buzzer)]
    F --> H[Optional Flask Dashboard]
    F --> I[Store Clip Locally]
```

---

## 6. Tools & Technologies

- **Hardware:** Jetson Nano, Pi Cam, ReSpeaker 2-Mic HAT, PIR sensor  
- **Software:** PyTorch, TensorRT, OpenCV, Mycroft Precise, YOLOv5-Nano, Flask  
- **Performance Metrics:** FPS, latency, face-recognition accuracy, power draw  

---

## 7. Milestone Status

| Task | Status |
|------|--------|
| Wake-word prototype | ✅ Completed |
| Motion sensor integration | ✅ Completed |
| Vision pipeline (MTCNN) | ✅ Completed |
| Basic demo | ✅ Completed |
| TensorRT optimization | 🔄 In progress |
| Full hardware integration | 🔄 In progress |

---

## 8. Updated Future Work

- **Jetson Nano Deployment:** Final integration + optimization  
- **Algorithm Verification:** Validate performance against real-world cases  
- **Accuracy Improvement:** Reduce false activations; improve detection precision  
- **Debugging & Optimization:** Eliminate failure cases; optimize FPS  
- **Robust System Design:** Ensure reliability in long-term operation  
- **Power Optimization:** Reduce both idle and active consumption  

---

## 9. Contributors

| Name | Role |
|------|------|
| Md Nasim Afroj Taj | Integration & Documentation |
| Mugesh Kumar NR | Hardware & Interfacing |
| Uttam Kumar Saha | Software & Optimization |
| All Members | Testing & Benchmarking |

---

## 10. Suggested Repository Structure

```
Sentinel-AI/
│
├── src/
│   ├── audio/
│   ├── vision/
│   ├── utils/
│   └── hardware/
│
├── models/
│   ├── mtcnn/
│   └── yolov5n/
│
├── docs/
│   ├── MIDTERM_REPORT.md
│   └── PROJECT_PROPOSAL.md
│
├── demo/
│   └── videos/
│
└── README.md
```

---

## 11. Summary

The project is on track for successful delivery.  
Core features are implemented, an early demo is functional, and optimization work is progressing toward final deployment.

Sentinel-AI will become a **fully offline, intelligent, low-power security solution** suitable for smart labs, homes, and edge environments.

---
