# 🧠 NeuroDetect-YOLOv10: Multi-Planar MRI Analysis


## 📖 Overview
**NeuroDetect** is an AI-powered medical imaging system designed to detect anomalies (e.g., tumors) in Brain MRI scans. Leveraging the state-of-the-art **YOLOv10** object detection model, this project analyzes T1-weighted contrast-enhanced (T1wCE) images across three anatomical planes:
1.  **Axial**
2.  **Coronal**
3.  **Sagittal**

By training separate models for each view, the system mimics the diagnostic workflow of radiologists, providing a multi-perspective analysis for higher reliability.

## ✨ Key Features
*   **State-of-the-Art Architecture:** Utilizes `yolov10l.pt` (Large) for superior detection accuracy.
*   **Multi-View Analysis:** Three independent models trained for Axial, Coronal, and Sagittal planes.
*   **Automated Configuration:** Python scripts dynamically generate YAML configurations for custom datasets.
*   **Binary Classification:** Effectively distinguishes between `Negative` (Healthy) and `Positive` (Anomaly) cases.

## 🛠️ Technologies Used
*   **Language:** Python 3.x
*   **Deep Learning:** [Ultralytics YOLOv10](https://github.com/ultralytics/ultralytics), PyTorch
*   **Image Processing:** OpenCV, NumPy, Matplotlib
*   **Environment:** Google Colab / Jupyter Notebook

## 📂 Dataset Structure
The project expects the dataset to be organized by anatomical planes. The training script automatically handles the YAML file creation, but your folders should look like this:

```text
archive/
├── axial_t1wce_2_class/
│   ├── images/ (train/test)
│   └── labels/ (train/test)
├── coronal_t1wce_2_class/
│   ├── images/ (train/test)
│   └── labels/ (train/test)
└── sagittal_t1wce_2_class/
    ├── images/ (train/test)
    └── labels/ (train/test)
🚀 Installation
Clone the repository:
code
Bash

download

content_copy

expand_less
git clone https://github.com/your-username/neurodetect-yolov10.git
cd neurodetect-yolov10
Install dependencies:
code
Bash

download

content_copy

expand_less
pip install ultralytics torch matplotlib numpy opencv-python
💻 Usage
1. Training the Models
The system trains three models sequentially. You can run the main script or train individually:
code
Python

download

content_copy

expand_less
from ultralytics import YOLO

# Example: Training the Axial Model
model = YOLO('yolov10l.pt')
model.train(data='/path/to/axial_dataset.yaml', epochs=60, imgsz=320, device='0')
2. Inference / Testing
To test the model on new images and visualize results:
code
Python

download

content_copy

expand_less
# Load the best trained weights
model = YOLO('/runs/detect/train/weights/best.pt')

# Run prediction
results = model('/path/to/test/images')

# Show results
results[0].show()
📊 Results
The following results demonstrate the model's performance after 60 epochs:
Plane	Precision	Recall	mAP50
Axial	9X.X%	9X.X%	0.9X
Coronal	9X.X%	9X.X%	0.9X
Sagittal	9X.X%	9X.X%	0.9X
