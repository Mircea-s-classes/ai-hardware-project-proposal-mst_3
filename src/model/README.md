# Sentinel-AI (MST_3) — Jetson Nano Run Guide

Sentinel-AI is a **privacy-preserving, offline** edge-security prototype that performs **real-time face detection + recognition** using **face-api.js** and a local camera stream (webcam / USB cam).

> This README focuses on **how to run the current face-api.js demo on a Jetson Nano**.  
> (It also matches the project story from our slide deck. :contentReference[oaicite:0]{index=0})

---

## 1) Hardware / OS Requirements

- **NVIDIA Jetson Nano**
- Jetson Nano running **JetPack (Ubuntu)** with internet access (to install packages)
- **USB webcam** (or CSI camera)
- Monitor + keyboard/mouse (or remote desktop)

---

## 2) What you need in the “Source Code” folder

Your demo must be served as a small web app. The folder you run should contain:

- `index.html` (or your main HTML file)
- `script.js` (or your JS entry file)
- `models/` folder (face-api model manifests + shards)
- `labels/` (or `lables/`) folder containing labeled face images:
  - Example:
    - `labels/Alice/1.png`
    - `labels/Alice/2.png`
    - `labels/Bob/1.png`
    - `labels/Bob/2.png`

### Models folder requirement (important)
face-api.js expects each model to have its **manifest.json** and **weight shard files** available under the same URL path (e.g., `/models`). :contentReference[oaicite:1]{index=1}

---

## 3) Install prerequisites on Jetson Nano

Open a terminal on the Jetson Nano and run:

```bash
sudo apt update
sudo apt install -y python3 python3-pip
```

## Browser Setup (Jetson Nano)

Sentinel-AI uses **browser-based camera access** and real-time inference via `face-api.js`.  
For compatibility and performance, **Chromium** is required.

### Install Chromium (if not already installed)

```bash
sudo apt update
sudo apt install -y chromium-browser
```

## Running the Demo (Local Web Server)

### Step A — Clone the Repository on Jetson Nano

```bash
cd ~
git clone https://github.com/Mircea-s-classes/ai-hardware-project-proposal-mst_3.git
```

### Step B — Navigate to the Web App Directory

Change directory to the folder that contains `index.html`
(the **Source Code** folder):

```bash
cd ~/ai-hardware-project-proposal-mst_3/src/model/Source\ Code
```

⚠️ If your folder name differs (spacing or capitalization), adjust the path accordingly.

---

### Step C — Start a Local HTTP Server

```bash
python3 -m http.server 8000
```

### Step D — Open the App in the Browser

Open **Chromium** and navigate to:

http://localhost:8000


When prompted:
- **Allow camera access**

You should see:
- Live webcam video  
- Face detection bounding boxes  
- Identity labels (if recognized)

---
## Notes on Camera Access (Very Important)

### Use `http://localhost`

Browser camera APIs require a **secure context**:
- `https://`, or
- `http://localhost`

Running the application directly from `file://` paths will often fail and prevent camera access.

---

### If You Don’t See a Camera Permission Popup

1. Click the 🔒 icon next to the URL
2. Open **Site settings**
3. Set **Camera → Allow**
4. Reload the page

Also ensure:
- No other application is currently using the webcam
- The USB camera is properly connected and recognized by the system
- 

## Configuring Labeled Identities

In the JavaScript code, labeled identities are defined as:

```js
const labels = ["yoga vignesh", "Mughesh"];
```

### To Add a New Person

1. Create a new folder:
labels/NewPerson/


2. Add face images:
labels/NewPerson/1.png
labels/NewPerson/2.png

3. Add the label in your JavaScript code:
```js
const labels = ["yoga vignesh", "Mughesh", "NewPerson"];
```
Tip: Use well-lit, front-facing images at a similar scale for best recognition accuracy.


## Performance Tips (Jetson Nano)

If performance or FPS is low, try the following optimizations:

### Reduce Camera Resolution

Lowering the input video resolution significantly improves inference speed on Jetson Nano:

```js
.getUserMedia({
  video: { width: 640, height: 480 },
  audio: false,
})
```
You may further reduce resolution if needed, depending on accuracy requirements.

Adjust Inference Rate
* Increase the face detection interval from 100 ms → 200–300 ms
* This reduces CPU/GPU load while maintaining acceptable responsiveness

Environment Optimization
* Prefer good, uniform lighting to reduce detection failures
* Close other applications and unnecessary browser tabs
* Avoid running heavy background processes during inference

These steps help ensure smoother real-time performance on resource-constrained edge devices like the Jetson Nano.


## Troubleshooting

### A) “Failed to fetch ./models …”

- Ensure the `models/` directory exists in the **same folder as `index.html`**
- Ensure the HTTP server is started from the **correct directory**
- Confirm model files include:
  - `manifest.json`
  - corresponding weight shard files (`*.bin`)

---

### B) “No face detected for ./labels/…”

- The label image may not contain a clear face
- Try:
  - Cropping the face more tightly
  - Using better lighting
  - Replacing the image with a clearer one

---

### C) Face Boxes Appear but Names Are “Unknown”

- Add more images per label (**2 → 5+ recommended**)
- Ensure the following match **exactly**:
  - Folder name
  - Label name in JavaScript
  - Image path

---

## (Optional) Faster Node.js Mode (Advanced)

`face-api.js` can also run in **Node.js** using TensorFlow bindings for improved performance.

### Recommended Stack
- `@tensorflow/tfjs-node`
- `canvas`

### Example Approach
```js
await faceapi.nets.ssdMobilenetv1.loadFromDisk('./models')
```

⚠️ Note: Node.js deployment was not standardized for this class submission, but may be explored for future optimization.
