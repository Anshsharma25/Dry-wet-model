# 🚀 YOLOv8m Custom Dataset: Dry vs Wet Classification 🌍
📚 Overview
This repository contains the implementation of an object detection model using YOLOv8m for classifying objects as "dry" or "wet". The model is trained on a custom dataset and utilizes the latest advancements in deep learning to efficiently detect and classify objects into these two categories. 🤖

# 🛠 Project Setup
📋 Prerequisites
Before running the project, ensure the following prerequisites are met:

Python: Version 3.7 or higher 🐍
PyTorch: Compatible version with your CUDA setup 💻
Ultralytics YOLOv8: Pretrained YOLOv8m model 🔥
OpenCV: For image processing 🖼️
Additional Libraries: numpy, matplotlib, PIL, etc. 📊
# 📝 Installation
Clone the Repository (if applicable):
git clone <repository_url>
cd <repository_name>
Install the Required Dependencies: It is recommended to use a virtual environment for the project. 🌱

pip install -r requirements.txt
🗂 Dataset Structure
The dataset should be organized into training and validation directories with images and corresponding label files in YOLO format.

dataset/
├── train/
│   ├── images/
│   ├── labels/
│
├── val/
│   ├── images/
│   ├── labels/
train/images/: Contains the images used for training the model 📷
train/labels/: Contains the corresponding annotation files in YOLO format 🏷️
val/images/: Contains the images used for validation ✅
val/labels/: Contains the corresponding annotation files for validation images 🔑
# 🔧 Dataset Configuration
Create a data.yaml file to define the dataset configuration, including paths to images and the class names.

Example data.yaml:

train: dataset/train/images
val: dataset/val/images
nc: 2
names: ['dry', 'wet']
train: Path to the training images
val: Path to the validation images
nc: Number of classes (2 in this case)
names: List of class names
# 🏋️‍♂️ Training the Model
To train the YOLOv8m model, follow these steps:

Start Training: Run the following command to begin training the model using the pretrained YOLOv8m weights:

yolo task=detect mode=train model=yolov8m.pt data=data.yaml epochs=50 imgsz=640
epochs=50: Number of training epochs (adjust as necessary)
imgsz=640: Size of the input images for training (adjust based on your GPU capacity)
Monitor Training: During training, the results and logs will be saved in the runs/train directory. You can track the training process and visualize the results using TensorBoard or by reviewing the logs directly 📈.

# 🔍 Inference
To run inference on new images or videos:

Inference Script: Run the following command to perform inference on a single image or video file:

python inference.py --weights runs/train/exp/weights/best.pt --source <image_path_or_video>
Replace <image_path_or_video> with the path to the image or video for inference 🎥.
View Results: The results (i.e., detected objects with bounding boxes) will be saved in the runs/detect/exp folder by default 🖼️.

# 📊 Evaluation
To evaluate the model's performance on the validation set, use the following command:

yolo task=detect mode=test model=runs/train/exp/weights/best.pt data=data.yaml
This will generate performance metrics such as Precision, Recall, and mAP (mean Average Precision) along with a confusion matrix, which can be useful for analyzing the model’s accuracy 📊.

# 🏅 Example Results
![Screenshot 2025-01-03 152902](https://github.com/user-attachments/assets/1f7dddbd-d1d0-497c-aebc-a04ef1ca68ee)
![Screenshot 2024-12-16 184546](https://github.com/userattachments/assets/6d960c9e-12da-44d9-a874-ae0ea90392ed)

![Screenshot 2024-12-19 122052](https://github.com/user-attachments/assets/efa93fa2-f392-4cc4-b14e-0167283da57d)

Upon successful inference, the output images will include bounding boxes around detected objects, labeled with their respective classes ("dry" or "wet"), and the associated confidence scores 🔍.

# 🛠 Troubleshooting
Ensure the dataset annotations are correctly formatted in YOLO format. Each label file should contain the class index and bounding box coordinates in the format: <class_id> <x_center> <y_center> <width> <height> 📝.
If you encounter performance issues, consider reducing the image size (imgsz) or adjusting the batch size 🐢.
Ensure the paths in the data.yaml file are correctly set to the locations of the dataset 🔗.
