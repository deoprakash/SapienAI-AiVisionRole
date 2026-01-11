
# Automated Quality Inspection System for Manufacturing

## Project Overview
This project implements an **Automated Visual Quality Inspection System** using Computer Vision and Deep Learning to detect and classify manufacturing defects before packaging.

The prototype focuses on **Printed Circuit Boards (PCBs)** and identifies multiple defect types using an object detection approach.

---

## Selected Product
**Printed Circuit Board (PCB)**

PCBs are chosen due to:
- Clear visual features
- Availability of real-world defect datasets
- Industrial relevance

---

## Defect Classes
The system detects and classifies the following defects:

| Class ID | Defect Name |
|--------|------------|
| 0 | Missing Component |
| 1 | Misalignment |
| 2 | Solder Bridge |
| 3 | Discoloration / Burn |
| 4 | Scratch (optional) |

Both **defective** and **defect-free** samples are included.

---

## Computer Vision Task
- **Type:** Object Detection
- **Model:** YOLOv8
- **Output:** Bounding boxes, defect class, confidence score, defect center coordinates, severity level

---

## Folder Structure
```
pcb_defect_inspection/
├── sample_images/
│   ├── defective/
│   └── non_defective/
├── annotations/
│   ├── pcb_001.txt
│   └── pcb_002.txt
├── scripts/
│   └── defect_detection.py
├── data.yaml
└── README.md
```

---

## Dataset Preparation
- Images are annotated in **YOLO format**
- Each annotation file contains:
```
<class_id> <x_center> <y_center> <width> <height>
```
(All values normalized between 0 and 1)

---

## How to Run the Project

### 1. Install Dependencies
```
pip install ultralytics opencv-python
```

### 2. Run Defect Detection
```
python scripts/defect_detection.py
```

---

## Output Details
For each detected defect, the system outputs:
- Defect type
- Confidence score
- (x, y) pixel coordinates of defect center
- Severity level (Low / Medium / High)

### Severity Logic
| Confidence | Severity |
|---------|----------|
| > 0.85 | High |
| 0.60 – 0.85 | Medium |
| < 0.60 | Low |

---

## Sample Output
```
{
  "Defect_Type": "Missing Component",
  "Confidence": 0.91,
  "Center_Pixel": [312, 245],
  "Severity": "High"
}
```

---

## Applications
- Automated Optical Inspection (AOI)
- Smart Manufacturing (Industry 4.0)
- Quality Control Systems
- Defect Monitoring and Analytics

---

## Conclusion
This system demonstrates a scalable and efficient approach for automated quality inspection using deep learning-based object detection. It reduces manual inspection effort, increases accuracy, and supports real-time manufacturing environments.

---

## Author
**Deo Prakash**
