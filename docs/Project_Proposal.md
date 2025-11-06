# University of Virginia
## Department of Electrical and Computer Engineering

**Course:** ECE 6332 — AI Hardware Design and Implementation  
**Semester:** Fall 2025  
**Proposal Deadline:** November 5, 2025 — 11:59 PM  
**Submission:** Upload to Canvas (PDF) and to GitHub (`/docs` folder)

---


## 1. Project Title
MST_3

Md Nasim Afroj Taj

Uttam Kumar Saha

Mugesh Kumar NR

Sentinel-AI: Voice & Motion Activated Multimodal Edge Security System

## 2. Platform Selection
Selected Platform: Edge-AI – NVIDIA Jetson Nano

The Sentinel-AI project uses Edge-AI because it requires real-time vision and audio processing directly on the device without cloud dependence.
The Jetson Nano provides GPU acceleration (CUDA + TensorRT) for efficient deep-learning inference while maintaining low power use (<10 W).
It supports multimodal AI (voice + vision), open-source frameworks (PyTorch, OpenCV, Jetson-Inference), and ensures privacy, low latency, and scalability—making it ideal for intelligent on-device security applications.

## 3. Problem Definition
Conventional CCTV systems record continuously, wasting power and storage while exposing private data through cloud dependence.  
This project addresses the need for an **energy-efficient, privacy-preserving, real-time surveillance system** capable of performing **local inference** for both audio (wake-word) and vision (object/face detection).  
The problem directly relates to **AI hardware efficiency, latency, and scalability** in multimodal edge computing.

---

## 4. Technical Objectives
1. Achieve **real-time inference ≥ 15 FPS** on Jetson Nano using optimized TensorRT models.  
2. Detect **wake-word within ≤ 250 ms** and trigger camera activation.  
3. Recognize faces and objects locally with **> 90 % accuracy**.  
4. Maintain system power draw **≤ 10 W** during active operation.  
5. Demonstrate **fully offline functionality** (no cloud dependency).

---

## 5. Methodology
- **Hardware setup:** Jetson Nano 4 GB, Pi Camera, ReSpeaker 2-Mic HAT, buzzer, LED.  
- **Software tools:** JetPack 5.x, PyTorch, TensorRT, OpenCV, Mycroft Precise, YOLOv5-Nano, face_recognition, Flask UI.  
- **Model design:** Quantized CNNs for vision; lightweight wake-word network for audio.  
- **Performance metrics:** FPS, latency, accuracy, power usage (Tegrastats).  
- **Validation:** Test in real environments; compare before/after optimization.

---

## 6. Expected Deliverables
- Working **Sentinel-AI prototype** (voice-activated security camera).  
- **GitHub repository** with code and setup guide.  
- **Demonstration video** and **presentation slides**.  
- **Final report** summarizing design, testing, and results.

---

## 7. Team Responsibilities

| Name | Role | Responsibilities |
|------|------|------------------|
| **Md Nasim Afroj Taj** | Integration | System integration, documentation, final report |
| **Mughesh Kumar N R** | Hardware | Jetson Nano setup, camera/mic interfacing |
| **Uttam Kumar Saha** | Software | Model implementation, TensorRT optimization |
| *Combined* | Evaluation | Testing, data collection, benchmarking |

---

## 8. Timeline and Milestones

| Week | Milestone | Deliverable |
|------|------------|-------------|
| 2 | Proposal submission | Project proposal PDF + GitHub repo |
| 4 | Midterm presentation | Slides + initial wake-word demo |
| 6 | Integration & testing | Working prototype with vision + audio |
| Dec 18 | Final presentation | Demo video + final report + GitHub archive |

---

## 9. Resources Required
- NVIDIA Jetson Nano 4 GB Dev Kit  
- Pi Camera / USB Camera  
- ReSpeaker 2-Mic HAT or USB Microphone  
- Buzzer + LED GPIO modules  
- YOLOv5 pre-trained dataset and open-source speech samples  
- JetPack SDK and TensorRT toolchain access  

---

## 10. References
- [NVIDIA Jetson-Inference](https://github.com/dusty-nv/jetson-inference)  
- [Mycroft Precise](https://github.com/MycroftAI/mycroft-precise)  
- [Ultralytics YOLOv5](https://github.com/ultralytics/yolov5)  
- [Dlib Face Recognition](https://github.com/ageitgey/face_recognition)  
- [NVIDIA JetPack Documentation](https://developer.nvidia.com/embedded/jetpack)

