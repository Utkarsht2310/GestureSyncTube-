# 🖐️ Hand Gesture & Face-Aware YouTube Controller

An **AI-powered computer vision project** that lets you **control YouTube and mouse movements using hand gestures and facial detection**.  
It integrates **MediaPipe**, **dlib**, **PyTorch**, and **OpenCV** to recognize hand gestures, detect sleepiness, and pause videos automatically when the user looks away.

---

## 🚀 Features

- 🖱️ **Mouse Control:** Move cursor, left/right click via hand gestures  
- 🎥 **YouTube Player Control:** Play/Pause, Volume, Forward/Backward, Captions, Fullscreen using gestures  
- 😴 **Sleepiness Detection:** Automatically pauses the video when eyes are closed for a few seconds  
- 👤 **Absence Detection:** Pauses the video when no face is detected  
- 🧠 **Gesture Recognition Model:** Uses a CNN model trained on custom gesture data (`models/model.pth`)  
- 🪶 **Smooth Movement:** Stabilized mouse motion with smoothing factor

---

## 🧩 Tech Stack

| Component | Technology |
|------------|-------------|
| AI Framework | PyTorch |
| Hand Detection | MediaPipe |
| Face Detection | Dlib + MediaPipe |
| Computer Vision | OpenCV |
| Input Control | PyAutoGUI |
| Data Storage | CSV (gesture data) |

---

## ⚙️ Setup Instructions

### 1️⃣ Clone Repository
```bash
git clone https://github.com/yourusername/hand-gesture-youtube-controller.git
cd hand-gesture-youtube-controller
```

### 2️⃣ Install Dependencies
```bash
pip install opencv-python mediapipe torch pandas imutils dlib pyautogui numpy
```

### 3️⃣ Download Required Models
- **Gesture Recognition Model** → `models/model.pth`
- **Face Landmark Model** → [shape_predictor_68_face_landmarks.dat](http://dlib.net/files/shape_predictor_68_face_landmarks.dat.bz2)

Place them inside the `models/` folder.

---

## 🧠 How It Works

1. **Hand Gestures:**  
   The app detects hand landmarks using MediaPipe and predicts gestures using a trained PyTorch model.

2. **Face Detection (Absence):**  
   Uses MediaPipe Face Detection — pauses video if no face is detected for a set duration.

3. **Eye Detection (Sleepiness):**  
   Uses Dlib’s eye landmarks to calculate EAR (Eye Aspect Ratio).  
   If eyes stay closed for a certain number of frames, the system automatically pauses playback.

4. **Control Mapping:**  
   - `Move_mouse`: Cursor movement  
   - `Left_click`: Click  
   - `Right_click`: Right click  
   - `Play_Pause`: Toggle spacebar  
   - `Vol_up_gen` / `Vol_down_gen`: System volume  
   - `Vol_up_ytb` / `Vol_down_ytb`: YouTube volume  
   - `Forward` / `Backward`: YouTube seek  
   - `fullscreen`: Toggle fullscreen  
   - `Cap_Subt`: Toggle captions  

---

## 🎮 Usage

1. Run the Python script:
```bash
python hand_controller.py
```

2. Press **‘q’** to quit anytime.  
3. Move your hand in front of the webcam — the detected gestures will be displayed live.  
4. Your YouTube player or system will respond accordingly.

---

## 📸 Screenshots

| Gesture Detection | Eye Tracking | Absence Detection |
|------------------|---------------|-------------------|
| ![Gesture](assets/gesture_detection.png) | ![Eyes](assets/eye_tracking.png) | ![Face](assets/absence_detection.png) |

---

## 🧾 CSV Data Format

The model learns gestures from **keypoint coordinates** stored in `data/gestures.csv`.  
Each row represents a gesture with normalized and distance-based features.

---

## ⚙️ Adjustable Parameters

| Variable | Description | Default |
|-----------|--------------|----------|
| `CONF_THRESH` | Minimum confidence for gesture recognition | 0.9 |
| `SMOOTH_FACTOR` | Controls mouse movement smoothing | 6 |
| `EAR_THRESH` | Eye Aspect Ratio threshold for sleep detection | 0.21 |
| `SLEEP_COUNTER_THRESH` | Frames before sleep action triggers | 20 |
| `ABSENCE_COUNTER_THRESH` | Frames before absence triggers | 20 |

---

## 🤝 Contributing

Pull requests and feature enhancements are welcome.  
If you have an idea for a new gesture or detection feature — feel free to contribute!

---

## 🪪 License

MIT License © 2025 Your Name

