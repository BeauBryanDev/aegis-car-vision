# Aegis-Road-Sentinel

Aegis-Road-Sentinel is an Automatic Number Plate Recognition (ANPR) system designed for vehicle detection, license plate recognition, and vehicle authorization workflows. The project combines multiple deep learning models in a cascading inference pipeline to identify vehicles, localize license plates, extract plate text, and validate authorized vehicles against a PostgreSQL whitelist database.

The system is optimized for Colombian yellow license plates and is intended as an academic and portfolio project focused on Computer Vision, Deep Learning, backend engineering, and modern web application development.

## Project Status

**Development**

This project is currently under active development. Features, APIs, model configurations, and deployment workflows may change as the system evolves.

---

## Overview

Aegis-Road-Sentinel processes images or video frames through a multi-stage machine learning pipeline:

1. Vehicle Detection
2. License Plate Localization
3. Optical Character Recognition (OCR)
4. Vehicle Authorization Validation

The objective is to provide an end-to-end ANPR solution capable of:

* Detecting vehicles in images and video streams
* Identifying and extracting license plates
* Performing OCR on detected plates
* Counting detected vehicles
* Comparing detected plates against a whitelist database
* Supporting access control and vehicle authorization scenarios

---

## Key Features

* Multi-stage ANPR inference pipeline
* Real-time vehicle detection
* License plate localization
* OCR-based plate recognition
* PostgreSQL whitelist verification
* REST API powered by FastAPI
* Containerized deployment using Docker
* Modern frontend built with React and TypeScript
* ONNX Runtime optimized inference
* Designed for Colombian license plate formats

---

## Machine Learning Pipeline

The ANPR system uses three independent machine learning models executed sequentially.

### Stage 1 — Vehicle Detection

Model:

* YOLOv11

Detected Classes:

* Motorcycle
* Car
* Van
* Truck
* Bus

Output:

* Vehicle bounding boxes
* Vehicle classification
* Detection confidence

### Stage 2 — License Plate Detection

Model:

* YOLOv8 Nano

Input:

* Vehicle crop generated from Stage 1

Output:

* License plate bounding box
* License plate crop

### Stage 3 — Optical Character Recognition

Model:

* PaddleOCR (PP-OCR)

Input:

* License plate crop generated from Stage 2

Output:

* Extracted license plate text
* OCR confidence score

---

## System Architecture

```text
Image / Video Frame
        │
        ▼
+------------------+
|   YOLOv11        |
| Vehicle Detector |
+------------------+
        │
        ▼
 Vehicle Bounding Box
        │
        ▼
+------------------+
|   YOLOv8 Nano    |
| Plate Detector   |
+------------------+
        │
        ▼
 License Plate Crop
        │
        ▼
+------------------+
|   PaddleOCR      |
| OCR Recognition  |
+------------------+
        │
        ▼
 Extracted Plate Text
        │
        ▼
 PostgreSQL Whitelist
        │
        ▼
 Authorization Result
```

---

## Technology Stack

### Backend

* Python 3.11
* FastAPI
* ONNX Runtime
* OpenCV
* NumPy
* PostgreSQL
* SQLAlchemy
* Alembic
* Docker
* Docker Compose

### Machine Learning

* YOLOv11
* YOLOv8 Nano
* PaddleOCR
* ONNX

### Frontend

* TypeScript
* React
* Vite
* Tailwind CSS

---

## Project Goals

This project was created to demonstrate practical skills in:

* Deep Learning
* Computer Vision
* Machine Learning Deployment
* Backend Development
* REST API Design
* Database Integration
* Docker Containerization
* Full-Stack Software Engineering

The repository serves as both an academic project and a professional portfolio showcase.

---

## Supported License Plates

Current implementation is optimized for:

* Colombian yellow vehicle license plates

Future versions may support:

* Additional Colombian plate categories
* International license plate formats
* Multi-country OCR models

---

## API Features

Current backend capabilities include:

* Vehicle detection
* License plate recognition
* OCR processing
* Vehicle authorization validation
* Database integration

Additional endpoints and documentation will be provided as development progresses.

---

## Database Integration

The system uses PostgreSQL to store authorized vehicle information.

Example workflow:

```text
Detected Plate
      │
      ▼
ABC123
      │
      ▼
Whitelist Query
      │
      ▼
Authorized / Unauthorized
```

Potential use cases include:

* Parking access control
* Campus vehicle management
* Residential security systems
* Fleet management solutions

---

## Performance Considerations

The inference pipeline has been designed for CPU-friendly deployment using ONNX Runtime.

Optimization techniques include:

* ONNX model execution
* Efficient image preprocessing
* Cascaded object detection
* Lightweight OCR inference
* Docker-based deployment

Performance may vary depending on:

* CPU specifications
* Video resolution
* Frame rate
* Number of vehicles present in the scene

---

## Repository Structure

```text
backend/
├── app/
│   ├── api/
│   ├── core/
│   ├── db/
│   ├── ml/
│   │   ├── ml_models/
│   │   ├── pipelines/
│   │   └── preprocessing/
│   └── main.py
│
├── scripts/
├── Dockerfile
├── docker-compose.yml
└── requirements.txt

frontend/
├── src/
├── public/
├── vite.config.ts
└── package.json
```
---

## Future Improvements

Planned enhancements include:

* Real-time video stream processing
* Multi-camera support
* Vehicle tracking
* Dashboard analytics
* OCR accuracy improvements
* GPU acceleration
* Event logging
* Historical plate records
* Authentication and role management
* Cloud deployment

---

## Educational Purpose

This project was developed for educational and portfolio purposes to explore modern Computer Vision workflows, Deep Learning inference pipelines, and full-stack application architecture.

---

## License

This project is licensed under the MIT License.

See the LICENSE file for additional details.

---

## Acknowledgements

This project builds upon open-source technologies and research from the Computer Vision and Deep Learning communities, including:

* Ultralytics YOLO
* PaddleOCR
* FastAPI
* OpenCV
* ONNX Runtime
* PostgreSQL
* React
* Docker
