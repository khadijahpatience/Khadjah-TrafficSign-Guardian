**Tier:** Tier 1  
**Author:** Khadjah  
**Course:** ITAI 1378 – Computer Vision & AI  
**Midterm Blueprint**

---

## 📌 Project Overview
Traffic signs provide critical information for safe driving, but humans and autonomous systems can miss or misinterpret them. This project builds a Tier 1 computer vision application that detects traffic signs by using a dataset to train the YOLOv8 model. OCR will then be applied to detected sign regions to extract readable text.

---

## 🎯 Problem Statement
Drivers and autonomous systems rely on accurate traffic sign recognition to make safe decisions. Missed or misread signs can lead to accidents, tickets, and inconsistent driving behavior. Transportation agencies, car manufacturers, and drivers care because sign recognition directly affects safety and compliance.

---

## 💡 Solution Overview
Traffic Sign Guardian uses a YOLOv8 model to detect traffic signs in images and produce a structured report listing sign types and counts. The system processes a road image, identifies sign locations, and outputs a readable summary of detected signs.

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
Tier 1 requires 

Data sources:
- A small set of **self‑collected road images**  
- (https://www.kaggle.com/datasets/valentynsichkar/traffic-signs-dataset-in-yolo-format)

Dataset Size:
- Approximately 900+ annotated traffic sign images.

Classes:
The dataset contains labeled traffic sign classes including
- Stop Sign
- Speed Limit Sign
- Warning Sign
- Pedestrian Crossing Sign
- Turn Sign
- Traffic Light

---

## 📏 Success Metrics
**Primary Metric:**  
- Correct detection of traffic signs in at least **80%** of test images.

**Secondary Metric:**  
- Inference time under **10 second** per image in Google Colab.

---

## 🗓 Milestone Plan

| Phase | Goal | Milestone |
|------|------|-----------|
| 🧭 Blueprint | Plan approved | Midterm submitted |
| 🔌 First Working Demo | YOLOv8 detects objects | Demo runs on sample images |
| 🛠 Make It Yours | Add sign‑report logic | System works on your images |
| 📈 Improve & Measure | Test on multiple images | Accuracy + failure cases recorded |
| 🎥 Package & Present | Final demo + README | Final submitted |

---

## ⚠️ Risks & Plan B

**Risk 1:** YOLOv8 may mislabel certain traffic signs.  
**Plan B:** Filter detections by keywords (“stop”, “sign”, “traffic”) to improve report accuracy.

**Risk 2:** Some images may have poor lighting or occlusion.  
**Plan B:** Collect clearer images or adjust confidence threshold.




