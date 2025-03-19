
# 📌 Gesture Recognition using Deep Learning  

## 📖 Project Overview  
This project implements a deep learning-based **hand gesture recognition** system to control a smart TV using a **3D Convolutional Neural Network (CNN)** and **Recurrent Neural Networks (RNNs)** such as **LSTM and GRU**. The model detects five different hand gestures via a webcam and maps them to specific commands for controlling video playback.  

## 🎯 Problem Statement  
The goal is to build a gesture recognition model that runs on a **smart TV camera** and correctly identifies five predefined hand gestures:  

- **👍 Thumbs Up** → Increase Volume  
- **👎 Thumbs Down** → Decrease Volume  
- **⬅️ Left Swipe** → Jump Backward 10 sec  
- **➡️ Right Swipe** → Jump Forward 10 sec  
- **✋ Stop** → Pause Video  

## 📂 Dataset  
The dataset consists of short videos (2-3 seconds) recorded by different users, each performing one of the five gestures. Each video is split into **30 frames** and processed for model training.  

- **Resolutions:** 360x360 or 120x160  
- **Data Source:** [Dataset Link](https://drive.google.com/uc?id=1ehyrYBQ5rbQQe6yL4XbLWe3FMvuVUGiL)  

## 🏗️ Model Architectures & Experiments  
The following architectures were tested to determine the best-performing model:  

| Model Architecture               | Key Layers                           | Validation Accuracy | Decision & Explanation |
|----------------------------------|--------------------------------------|---------------------|------------------------|
| **CNN + LSTM**                   | Conv2D + LSTM + Dense                | **87%**             | ✅ *Selected as the final model* due to high accuracy and efficiency (<1M parameters). |
| **CNN + GRU**                    | Conv2D + GRU + Dense                 | 79%                 | Good performance but slightly lower than LSTM. |
| **3D CNN**                        | Conv3D + MaxPooling3D + Dense        | 83%                 | High complexity, lower accuracy than CNN-LSTM. |
| **CNN + Transfer Learning (ResNet)** | Pre-trained ResNet + Dense           | 75%                 | 🚫 Too many parameters (~25M), making training slow with suboptimal accuracy. |

### ✅ **Final Model: CNN + LSTM**  
The **CNN-LSTM** model was selected as the best-performing architecture, offering a good balance of accuracy and computational efficiency.  

## 🔄 Data Ingestion Pipeline  
A **custom data generator** was implemented instead of Keras’ built-in image data generators to handle **video batches efficiently**. This prevents memory overload while processing large datasets.  

## ⚡ Training Strategies & Challenges  
- **Learning Rate Adjustment:** Reduced to **0.0002** using Adam optimizer to avoid gradient plateau.  
- **Batch-wise Gradient Descent:** Used **Python generators** to handle large datasets efficiently.  
- **Regularization & Dropout:** Explored **dropout techniques**, but improvements were limited.  

## 📌 Scope for Improvement  
- Fine-tuning **learning rate and regularization** to boost accuracy.  
- Implementing **recurrent dropout** for LSTMs.  
- Exploring **bi-directional LSTMs or Vision Transformers** for better temporal sequence learning.  

## 📜 License  
This project is open-source under the **MIT License**.  

---
