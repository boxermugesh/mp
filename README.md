# # 🔍 FaceTrace — AI-Powered Missing Persons & Criminal Face Identification System

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.10-blue?style=for-the-badge&logo=python" />
  <img src="https://img.shields.io/badge/Flask-Web%20App-black?style=for-the-badge&logo=flask" />
  <img src="https://img.shields.io/badge/DeepFace-VGG--Face-red?style=for-the-badge" />
  <img src="https://img.shields.io/badge/SVM-Scikit--Learn-orange?style=for-the-badge&logo=scikit-learn" />
  <img src="https://img.shields.io/badge/SQLite-Database-blue?style=for-the-badge&logo=sqlite" />
  <img src="https://img.shields.io/badge/MediaPipe-Face%20Detection-green?style=for-the-badge" />
</p>

> A real-time AI-powered surveillance system built for law enforcement agencies to identify **missing persons** and **known criminals** from live video feeds and uploaded footage using deep learning and face recognition.

---

## 🧠 Project Overview

**FaceTrace** is a Police CyberCrime Unit tool that leverages deep learning-based facial recognition to assist law enforcement in:

- Detecting and identifying **known criminals** from surveillance footage
- Locating **missing children and persons** using face matching
- Enabling **real-time video analysis** via a secure web portal
- Providing a **centralized admin dashboard** for managing the face database

The system uses **VGG-Face** (via DeepFace) to extract 4096-dimensional facial embeddings, trains an **SVM classifier** on the enrolled face database, and performs fast inference on video input using **MediaPipe** for face detection.

---

## 🚀 Key Features

| Feature | Description |
|---|---|
| 🎥 Real-Time Video Analysis | Processes live or uploaded video to detect and identify faces |
| 🧬 Deep Face Embeddings | Uses VGG-Face model for high-accuracy facial feature extraction |
| 🤖 SVM Classification | Trained Support Vector Machine classifier for identity prediction |
| 🗄️ SQLite Database | Stores face embeddings and user records securely |
| 🔐 Admin Authentication | Secure login portal for police/admin users |
| 🌐 Flask Web Interface | Full-stack web app with HTML/CSS frontend and Python backend |
| 📁 Batch Enrollment | Capture and store face data from multiple video files |
| 🔁 Fallback Feature Extractor | TensorFlow VGG16 as backup when DeepFace is unavailable |

---

## 🛠️ Tech Stack

### Backend
- **Python 3.10**
- **Flask** — Web framework
- **DeepFace** — VGG-Face facial embedding extraction
- **TensorFlow / Keras** — VGG16 fallback feature extractor
- **scikit-learn** — SVM classifier + StandardScaler
- **MediaPipe** — Real-time face detection
- **OpenCV** — Video capture and frame processing
- **SQLite** — Lightweight face database
- **Joblib** — Model serialization (`svm_model.pkl`)

### Frontend
- **HTML5 / CSS3** — UI pages
- **Bootstrap 4/5** — Responsive design
- **Font Awesome** — Icons
- **Animate.css** — Animations
- **Vanilla JavaScript** — Form handling and API calls

---

## 📁 Project Structure

```
FaceTrace/
│
├── app.py                   # Flask main application
├── res.ipynb                # Model training & testing notebook
├── svm_model.pkl            # Trained SVM model + scaler
├── users.db                 # SQLite face database
│
├── data/
│   ├── criminal/            # Criminal training videos
│   │   ├── user1.mp4
│   │   └── user2.mp4
│   └── missing/             # Missing persons training videos
│       ├── user3.mp4
│       └── user4.mp4
│
├── templates/
│   ├── index.html           # Landing page
│   ├── login.html           # Admin login page
│   ├── signup.html          # Registration page
│   ├── student.html         # Video upload & prediction page
│   ├── single.html          # Transaction/single prediction page
│   └── Output.html          # Prediction result display page
│
└── README.md
```

---

## ⚙️ How It Works

```
1. ENROLLMENT PHASE
   Video files → Frame extraction (OpenCV)
              → Face detection (MediaPipe)
              → Feature extraction (VGG-Face / VGG16)
              → Store embeddings in SQLite DB

2. TRAINING PHASE
   SQLite DB → Load embeddings
            → Normalize (StandardScaler)
            → Train SVM classifier
            → Save model (svm_model.pkl)

3. PREDICTION PHASE
   Input video → Frame-by-frame face detection
              → Feature extraction
              → SVM prediction
              → Most frequent label = identity
              → Display result on web UI
```

---

## 🖥️ Installation & Setup

### 1. Clone the Repository
```bash
git clone https://github.com/your-username/facetrace.git
cd facetrace
```

### 2. Create Virtual Environment
```bash
python -m venv venv
source venv/bin/activate        # On Windows: venv\Scripts\activate
```

### 3. Install Dependencies
```bash
pip install flask opencv-python numpy mediapipe deepface tensorflow scikit-learn joblib
```

### 4. Add Training Data
Place video files in the `data/` folder:
```
data/criminal/user1.mp4
data/criminal/user2.mp4
data/missing/user3.mp4
data/missing/user4.mp4
```

### 5. Train the Model
Open and run `res.ipynb` in Jupyter Notebook, or run the training script:
```bash
python train.py
```

### 6. Run the Web Application
```bash
python app.py
```
Open your browser at `http://localhost:5000`

---

## 📸 Screenshots

| Page | Description |
|---|---|
| `index.html` | Landing page with project overview and admin login button |
| `login.html` | Secure admin authentication portal |
| `student.html` | Video upload interface for face prediction |
| `Output.html` | Displays identity prediction results |

---

## 🔒 Security & Ethics Notice

> This system is designed **exclusively for authorized law enforcement use**. Unauthorized use of facial recognition technology may violate privacy laws. The system must be deployed in compliance with applicable legal frameworks and data protection regulations.

- All face data is stored locally in an encrypted-capable SQLite database
- Admin access is protected via login authentication
- No data is transmitted to third-party servers

---

## 📊 Model Performance

| Metric | Value |
|---|---|
| Feature Extractor | VGG-Face (4096-dim embeddings) |
| Classifier | SVM (Linear Kernel) |
| Face Detector | MediaPipe (confidence ≥ 0.5) |
| Frames per Video | Up to 500 frames |
| Avg. Detection Speed | ~20 fps (365 faces in ~18 sec) |

---

## 🤝 Contributing

1. Fork the repository
2. Create a new branch: `git checkout -b feature/your-feature`
3. Commit your changes: `git commit -m 'Add your feature'`
4. Push to the branch: `git push origin feature/your-feature`
5. Open a Pull Request

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

## 👨‍💻 Author

Developed as part of a Police CyberCrime Unit initiative to leverage AI for public safety and missing persons identification.

---

<p align="center">
  <b>FaceTrace — Because Every Face Tells a Story 🔍</b>
</p>

