# Helmet Violation Detection System

## 1. Problem Statement

Road safety violations, especially riding without a helmet, are a major cause of accidents. Manual monitoring is inefficient and not scalable. This project aims to automate helmet violation detection using computer vision and provide a system to capture, store, and visualize violations.

---

## 2. Objective

* Detect helmet violations in real time
* Capture evidence images of violations
* Associate violations with vehicle data
* Store violation records in a database
* Provide a dashboard for monitoring and verification

---

## 3. System Architecture (High Level)

Input (Camera Feed)
↓
YOLOv8 Detection Engine
↓
Violation Logic (No Helmet Simulation)
↓
Image Capture Module
↓
Vehicle Assignment Service
↓
Database Storage (SQLite)
↓
Flask API Backend
↓
Web Dashboard (UI)

---

## 4. Key Components

### 4.1 Detection Engine

* Uses YOLOv8 for real-time object detection
* Currently detects "person" class
* Treated as helmet violation (simulation)

### 4.2 Image Capture Module

* Crops detected bounding box region
* Saves only relevant violation image
* Ensures image is valid before storing

### 4.3 Vehicle Assignment Service

* Assigns vehicle numbers from predefined dataset
* Ensures controlled and realistic mapping
* Can be extended to real number plate recognition

### 4.4 Fine Management

* Fixed fine logic implemented
* Easily extendable for dynamic fine rules

### 4.5 Database Layer

* SQLite used for lightweight storage
* Stores:

  * Vehicle number
  * Timestamp
  * Image path

### 4.6 API Layer

* Built using Flask
* Exposes violation data to UI
* Handles image serving

### 4.7 Dashboard

* Displays violations in tabular format
* Shows:

  * Vehicle number
  * Time
  * Fine
  * Evidence image
* Supports image preview and verification

---

## 5. Data Flow

1. Camera captures live video
2. YOLOv8 processes each frame
3. Person detected → treated as violation
4. Image cropped and saved
5. Vehicle number assigned
6. Data stored in database
7. Dashboard fetches and displays records

---

## 6. Features

* Real-time detection
* Automatic image capture
* Data integrity (only valid images stored)
* Clean database handling
* REST-based backend
* Interactive dashboard
* Clickable evidence images

---

## 7. Tech Stack

* Python
* OpenCV
* YOLOv8 (Ultralytics)
* Flask
* SQLite

---

## 8. Project Structure

helmet_detection/
│
├── main.py                → Detection + Capture Logic
├── yolov8n.pt            → Pretrained Model
│
├── api/
│   ├── app.py            → Backend API
│   └── templates/
│       └── index.html    → Dashboard UI
│
├── database/
│   ├── data.db           → Database
│   ├── db.py             → DB operations
│   └── init_db.py        → Initialization
│
├── services/
│   ├── plate_service.py  → Vehicle assignment
│   └── fine_service.py   → Fine logic
│
└── output/
└── violations/       → Captured images

---

## 9. Setup Instructions

Install dependencies:
pip install ultralytics opencv-python flask

Initialize database:
python database/init_db.py

Run detection:
python main.py

Run dashboard:
python api/app.py


Open:
http://127.0.0.1:5000/

---

## 10. Design Decisions

* Used YOLOv8 for fast and efficient detection
* Used SQLite for simplicity and portability
* Used Flask for lightweight backend
* Implemented image validation before DB insert
* Separated logic into modular services


---

## 11. Future Enhancements

* Integrate real helmet detection model
* Add OCR for number plate recognition
* Implement notification system (SMS/Email)
* Deploy on cloud (AWS/Azure)
* Add analytics (violation trends)

---

## 12. Conclusion

This project demonstrates a complete end-to-end system combining computer vision, backend processing, and frontend visualization. It showcases how real-world traffic monitoring systems can be designed and implemented using modern tools.

---

## 13. Author

Helmet Violation Detection System
