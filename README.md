🛡️ Surveillance-System

         Real-time object detection & face-recognition pipeline on live CCTV streams.  
📌 Overview

        This repository contains a Python-based surveillance platform that:
        Captures live footage from IP / USB cameras.
        Detects persons, vehicles, weapons (YOLOv8).
        Recognizes authorized vs. unknown faces (FaceNet + SVM).
        Sends instant alerts (email / SMS) on anomalies.
        Stores events to a local SQLite / PostgreSQL back-end.
        Provides a Streamlit dashboard for real-time monitoring & playback.
🚀 Quick Start
1️⃣ Clone & enter

    git clone https://github.com/NIKUNJGUPTA12/Surveillance-System.git

    cd Surveillance-System
    
2️⃣ Install dependencies


                  python -m venv .venv && source .venv/bin/activate  # Windows: .venv\Scripts\activate
                  pip install -r requirements.txt
3️⃣ Configure environment

         cp .env.example .env
         # Edit .env with your camera URLs, email credentials, etc.
4️⃣ Fire it up

         Mode	         Command
         Real-time feed	python main.py --mode live --source 0
         Video file	python main.py --mode file --source ./demo.mp4
         Web UI	streamlit run dashboard.py

🧰 Tech Stack

        | Layer	         |Tech
        | Detection	| YOLOv8 (PyTorch)
        | Recognition	| FaceNet, SVM
        | Database	|SQLite (default) / PostgreSQL (prod)
        | Frontend	|Streamlit
        | Alerts	         |SMTP (email), Twilio (SMS)


📁 Project Layout

    Surveillance-System/
    ├── main.py              # Entry point
    ├── dashboard.py         # Streamlit UI
    ├── src/
    │   ├── detector.py      # YOLO inference
    │   ├── recognizer.py    # Face recognition
    │   ├── notifier.py      # Email / SMS
    │   └── db_handler.py    # DB CRUD
    ├── models/
    │   ├── yolov8n.pt
    │   └── facenet_keras.h5
    ├── data/
    │   ├── faces/           # authorized faces
    │   └── events.db
    ├── docker/
    │   ├── Dockerfile
    │   └── docker-compose.yml
    ├── requirements.txt
    └── README.md

🎯 Key Features
✅ Multi-camera support (RTSP / USB / IP).
✅ Role-based alerts (admin, security, etc.).
✅ Event timeline with thumbnails & JSON export.
✅ REST API (/events, /snapshot) for integration.

🔐 Environment Variables (.env)
# Camera
CAMERA_URL=rtsp://user:pass@ip:port/stream

# Email
SMTP_SERVER=smtp.gmail.com
SMTP_PORT=587
EMAIL_USER=your@gmail.com
EMAIL_PASS=your_app_password

# SMS (optional)
TWILIO_SID=ACxxxxxxxxxxxxxxxx
TWILIO_TOKEN=xxxxxxxxxxxxxxxx
TWILIO_FROM=+1234567890
🧪 Example Output
Copy
[2024-07-15 14:32:10] PERSON detected → confidence 0.93
[2024-07-15 14:32:11] UNKNOWN face → alert sent (email)
🛠️ Development
bash
Copy
# Lint
flake8 src/
# Tests
pytest tests/
🤝 Contributing
Pull-requests welcome!
Report bugs via Issues.
Add new detectors under src/detectors/.
📄 License
MIT © Nikunj Gupta
