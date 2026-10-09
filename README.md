**Tier:** Tier 1  
**Author:** Khadjah  
**Course:** ITAI 1378 – Computer Vision & AI  
**Midterm Blueprint**

---

## 📌 Project Overview
Traffic signs provide critical information for safe driving, but humans and autonomous systems can miss or misinterpret them. This project builds a Tier 1 computer vision application that detects traffic signs using a pretrained YOLOv8 model and generates a simple traffic‑sign report from road images.

This is a Tier 1 project because it uses **pretrained models only**, focuses on **application logic**, and does **not** require training or dataset creation.

---

## 🎯 Problem Statement
Drivers and autonomous systems rely on accurate traffic sign recognition to make safe decisions. Missed or misread signs can lead to accidents, tickets, and inconsistent driving behavior. Transportation agencies, car manufacturers, and drivers care because sign recognition directly affects safety and compliance.

---

## 💡 Solution Overview
Traffic Sign Guardian uses a pretrained YOLOv8 model to detect traffic signs in images and produce a structured report listing sign types and counts. The system processes a road image, identifies sign locations, and outputs a readable summary of detected signs.

**Flow:**  
Image → YOLOv8 Detection → Extract Sign Labels → Traffic Sign Report

---

## 🛠 Technical Approach
- **Technique:** Object Detection  
- **Model:** YOLOv8n (pretrained)  
- **Framework:** Ultralytics YOLO + Python  
- **Environment:** Google Colab (GPU enabled)  
- **Why:** YOLOv8 is fast, accurate, and ideal for Tier 1 pretrained detection tasks.

No training or fine‑tuning is required.

---

## 📂 Data Plan
Tier 1 requires **no dataset creation**.

Data sources:
- A small set of **self‑collected road images**  
- Optional: public traffic sign images for testing  
- No GTSRB training (Tier 1 restriction)

`data/README.md` will document where test images come from.

---

## 📏 Success Metrics
**Primary Metric:**  
- Correct detection of traffic signs in at least **80%** of test images.

**Secondary Metric:**  
- Inference time under **1 second** per image in Google Colab.

---

## 🗓 Milestone Plan

| Phase | Goal | Milestone |
|------|------|-----------|
| 🧭 Blueprint | Plan approved | Midterm submitted |
| 🔌 First Working Demo | Pretrained YOLOv8 detects objects | Demo runs on sample images |
| 🛠 Make It Yours | Add sign‑report logic | System works on your images |
| 📈 Improve & Measure | Test on multiple images | Accuracy + failure cases recorded |
| 🎥 Package & Present | Final demo + README | Final submitted |

---

## ⚠️ Risks & Plan B

**Risk 1:** YOLOv8 may mislabel certain traffic signs.  
**Plan B:** Filter detections by keywords (“stop”, “sign”, “traffic”) to improve report accuracy.

**Risk 2:** Some images may have poor lighting or occlusion.  
**Plan B:** Collect clearer images or adjust confidence threshold.

---

## 📘 AI Usage Log
This project used Microsoft Copilot to help structure the Blueprint, revise README content, and outline slide text. All code and logic were written and tested manually in Google Colab. Any errors that could not be fixed with my knowledge were also corrected by AI.

---

## 📁 Repository Structure
traffic-sign-guardian/
├── README.md
├── data/
│   └── README.md
├── notebooks/
│   └── traffic_sign_demo.ipynb
└── docs/
└── proposal.pdf

---

## 🚀 Starter Code (Tier 1)
```python
!pip install ultralytics opencv-python matplotlib

from ultralytics import YOLO

model = YOLO('yolov8n.pt')

results = model('https://ultralytics.com/images/traffic-signs.jpg')
results[0].show()
python
results = model('my_road_image.jpg')

sign_report = {}

for box in results[0].boxes:
    cls_id = int(box.cls[0])
    name = model.names[cls_id]
    conf = float(box.conf[0])

    if "sign" in name.lower() or "stop" in name.lower() or "traffic" in name.lower():
        sign_report[name] = sign_report.get(name, 0) + 1

print("Traffic Sign Report:")
for sign, count in sign_report.items():
    print(f"- {sign}: {count}")

