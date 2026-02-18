# 🏭 Automated Optical Inspection (AOI) for Casting Defects using Deep Learning

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange)
![Deep Learning](https://img.shields.io/badge/Deep%20Learning-ResNet50-brightgreen)
![Industry 4.0](https://img.shields.io/badge/Domain-Industry%204.0-yellow)

## 📌 Project Overview
In modern manufacturing, manual inspection of metal casting defects (such as blowholes, cracks, or shrinkage on pump impellers) is a highly time-consuming and error-prone process. This project leverages **Computer Vision and Transfer Learning** to automate the quality inspection process, acting as an **Automated Optical Inspection (AOI)** system aligned with **Industry 4.0** standards.

By deploying this model on edge devices (like cameras over conveyor belts), factories can instantly flag defective parts, reducing manual labor costs and significantly improving manufacturing throughput.

## 🗄️ Dataset
* **Source:** Kaggle (Real-life industrial dataset of casting products)
* **Content:** Top-view images of submersible pump impellers.
* **Classes:** * `Defective`: Parts with physical flaws (holes/cracks).
  * `OK`: Flawless parts.
* **Preprocessing:** Images resized to `224x224`, normalized to `[0,1]`, and augmented (rotation, zoom, horizontal flips) to simulate real-world factory camera variations and prevent overfitting.

## ⚙️ Methodology & Architecture
* **Pre-trained Model:** **ResNet50** (trained on ImageNet).
* **Transfer Learning Strategy:** * The base convolutional layers of ResNet50 were **frozen** to retain powerful, pre-learned edge and texture detection capabilities while minimizing computational cost.
  * A **Custom Classification Head** was added on top: `GlobalAveragePooling2D` -> `Dense(1024, ReLU)` -> `Dropout(0.5)` -> `Dense(1, Sigmoid)` for binary classification.
* **Optimization:** `Adam` optimizer with a learning rate of `0.0001` for stable fine-tuning.

## 📊 Results & Performance
Despite severe hardware constraints and training for only **10 epochs**, the transfer learning model demonstrated exceptional rapid learning capabilities:
* **Accuracy:** ~70% on the unseen test set.
* **F1-Score:** 0.70
* **Time Efficiency:** By freezing base layers, the model achieved functional predictive power in a fraction of the time required to train a CNN from scratch.

*(Note: In a real-world scenario, you would upload your `accuracy.png` and `confusion_matrix.png` to your repo and link them here)*
## 🚀 Future Scope
To prepare this system for a live factory deployment:
1. **Unfreezing Layers:** Fine-tune the top 1 or 2 convolutional blocks of the ResNet50 base with a very low learning rate to adapt to specific metal textures.
2. **Extended Training:** Train for 50-100 epochs with early stopping to push accuracy above 95%.
3. **Edge Deployment:** Convert the model to **TensorFlow Lite (TFLite)** to run on edge devices like Raspberry Pi for real-time video feed analysis.

## 👨‍💻 Author
**Yash Dhananjay Dalavi** *Deep Learning & Cloud Computing Enthusiast* [LinkedIn](https://www.linkedin.com/in/yash-dalavi-8080402a2/) | [GitHub](https://github.com/yash-D-Dalavi)
