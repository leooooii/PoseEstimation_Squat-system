# Mediapipe Pose Estimation – Squat Counter & Real-Time Form Feedback

This project uses **Google Mediapipe’s Pose Estimation** together with **Python** to implement a real-time squat counter with posture assessment.  
The system not only counts completed squat repetitions, but also provides **instant feedback to help improve squat technique**, making training safer and more effective.

---

## Features

### ✔ Real-Time Pose Estimation  
Utilizes Mediapipe’s `Pose` solution to detect and track 33 human body landmarks in real time.

### ✔ Automated Squat Counting  
A joint-angle–based state machine detects the full squat cycle:  
**standing → descending → bottom → ascending → standing**,  
and increments the squat counter upon completing one full repetition.

### ✔ Real-Time Form Correction  
The system analyzes knee angles, hip angles, torso alignment, and symmetry to detect common squat issues such as:

- Knees collapsing inward  
- Leaning too far forward  
- Insufficient squat depth  

Corrective suggestions are displayed live on the screen.

### ✔ Visual Overlays  
Landmarks, pose connections, angle readings, and feedback text are rendered directly over the webcam feed.

---

## Demo

Real-time squat detection demo:

![Demo](https://imgur.com/SZ03yc6.gif)

---

## Experiment Results

After using this system, participants demonstrated improved squat stability and consistency.  
The graphs below show pre-experiment and post-experiment performance comparisons.

![Graph](https://imgur.com/CuuKwXI.jpg)

![Graph1](https://imgur.com/UpyrYsq.jpg)

---

## System Overview

### **1. Pose Detection**
Mediapipe identifies 33 major skeletal landmarks, including:  
Shoulders, hips, knees, ankles, spine, etc.

### **2. Angle Calculation**
The system computes:

- **Knee angle** (hip–knee–ankle)  
- **Hip angle** (shoulder–hip–knee)  
- **Torso angle** (relative to vertical)  

These angles are used to determine movement states and posture quality.

### **3. Squat Counting Algorithm**
A simple finite-state model:
if knee_angle < bottom_threshold:
state = "down"

if knee_angle > top_threshold and state == "down":
count += 1
state = "up"


### **4. Real-Time Posture Feedback**
Rules trigger feedback messages:



if knees_inward:
"Keep your knees aligned with your toes"

if shallow_depth:
"Try to squat deeper"

if torso_lean:
"Keep your chest up and engage your core"


---

## 🛠 Technology Stack

| Component | Technology |
|----------|------------|
| Pose Estimation | Google Mediapipe |
| Programming Language | Python |


---

## How to Run

```bash

📂 Project Structure
├── Media Pipe _Squat system.ipynb      # main program

