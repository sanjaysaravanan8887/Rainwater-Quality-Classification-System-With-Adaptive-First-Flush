# 🌧️ Adaptive Sensor-Fusion-Based Rainwater Quality Classification and Multi-Path Pipe Diversion System with Dynamic First-Flush Control

<p align="center">

![Python](https://img.shields.io/badge/Python-3.11-blue?style=for-the-badge\&logo=python)
![Machine Learning](https://img.shields.io/badge/Machine%20Learning-CatBoost-orange?style=for-the-badge)
![ESP32](https://img.shields.io/badge/ESP32-IoT-red?style=for-the-badge)
![Google Colab](https://img.shields.io/badge/Google%20Colab-Notebook-yellow?style=for-the-badge\&logo=googlecolab)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

</p>

---

# 📖 Overview

Rainwater harvesting has become an essential solution for addressing water scarcity. However, the quality of harvested rainwater changes significantly during rainfall. The initial runoff, known as the **first flush**, contains dust, bird droppings, leaves, roof debris, and atmospheric pollutants, making it unsuitable for storage.

Traditional rainwater harvesting systems generally rely on **fixed timers** to divert the first flush. These methods cannot adapt to changing weather conditions, roof cleanliness, or rainfall intensity, leading to unnecessary water loss or poor-quality water storage.

This project introduces an **Adaptive Sensor-Fusion-Based Rainwater Quality Classification System** that continuously measures rainwater quality using multiple sensors, predicts water quality using Machine Learning, and dynamically determines the end of the contaminated first-flush period.

Based on the predicted water quality, the system automatically diverts water into the most appropriate destination using electronically controlled valves.

---

# 🎯 Problem Statement

Conventional rainwater harvesting systems:

* Use fixed first-flush timers
* Cannot determine actual water quality
* Waste large amounts of usable rainwater
* May store contaminated water
* Lack intelligent decision-making

This project solves these problems using **Machine Learning**, **IoT**, and **real-time sensor fusion**.

---

# 💡 Proposed Solution

The proposed system continuously monitors incoming rainwater using multiple water-quality sensors.

Instead of relying on a predetermined first-flush duration, the Machine Learning model evaluates the sensor readings in real time and classifies the water into different quality levels.

The controller then automatically routes the water through a multi-path pipe system to the appropriate destination.

---

# ✨ Features

* 🌧️ Real-time rainwater quality monitoring
* 🤖 Machine Learning-based water classification
* 📊 Adaptive first-flush control
* 🚰 Automatic multi-path water diversion
* ☁️ Cloud-based prediction system
* 📡 ESP32 IoT integration
* 📈 Physics-inspired synthetic dataset
* 🧠 CatBoost-based classification model
* 📉 Feature importance analysis
* ✅ Cross-validation and hyperparameter tuning

---

# 🏗️ System Architecture

```text
                     Rainwater
                         │
                         ▼
               Measurement Chamber
                         │
        ┌────────────────┼────────────────┐
        │                │                │
      pH Sensor      TDS Sensor    Turbidity Sensor
        │                │                │
        └────────────────┼────────────────┘
                         │
                  Temperature Sensor
                         │
                         ▼
                      ESP32
                         │
                  Wi-Fi / Internet
                         │
                         ▼
                 Cloud Prediction API
                         │
                  CatBoost ML Model
                         │
                Water Quality Class
                         │
                         ▼
              Electronic Valve Control
                         │
     ┌──────────┬───────────┬────────────┬────────────┐
     ▼          ▼           ▼            ▼
 First Flush  Recharge   Irrigation   Storage Tank
```

---

# 🔄 Working Principle

1. Rainwater enters the measurement chamber.
2. Water quality sensors continuously measure:

   * pH
   * TDS
   * Turbidity
   * Temperature
3. ESP32 collects all sensor readings.
4. Sensor values are sent to the cloud using HTTP requests.
5. The CatBoost model predicts the water quality.
6. The prediction is returned to the ESP32.
7. The controller automatically diverts water through the appropriate valve.

---

# 🧪 Sensors Used

| Sensor             | Purpose                        |
| ------------------ | ------------------------------ |
| pH Sensor          | Measures acidity or alkalinity |
| TDS Sensor         | Measures dissolved solids      |
| Turbidity Sensor   | Measures suspended particles   |
| Temperature Sensor | Measures water temperature     |

---

# 📊 Dataset

A custom **physics-inspired synthetic dataset** was created for this project.

### Dataset Features

* pH
* TDS (ppm)
* Turbidity (NTU)
* Temperature (°C)
* Dry Days Before Rain

### Output

* Water Class

### Water Classes

| Class                   | Description                                 |
| ----------------------- | ------------------------------------------- |
| Reject_First_Flush      | Highly contaminated initial rainwater       |
| Poor_Needs_Treatment    | Requires treatment before storage           |
| Fair_Non_Potable_Use    | Suitable for non-potable applications       |
| Good_Store_After_Filter | Can be stored after filtration              |
| Excellent_Store         | High-quality rainwater suitable for storage |

---

# 🤖 Machine Learning Pipeline

```
Dataset

↓

Data Cleaning

↓

Exploratory Data Analysis

↓

Feature Engineering

↓

Train-Test Split

↓

Decision Tree

↓

Random Forest

↓

XGBoost

↓

LightGBM

↓

CatBoost

↓

Cross Validation

↓

Hyperparameter Tuning

↓

Model Saving

↓

Cloud Deployment
```

---

# 📈 Model Performance

| Model         | Accuracy      |
| ------------- | ------------- |
| Decision Tree | 95.75%        |
| Random Forest | 97.45%        |
| XGBoost       | 97.34%        |
| LightGBM      | 97.62%        |
| **CatBoost**  | **97.78%** 🏆 |

---

# 📉 Model Validation

### Train Accuracy

98.64%

### Test Accuracy

97.78%

### Cross Validation (5-Fold)

Mean Accuracy

97.51%

Standard Deviation

0.00061

These results indicate that the model generalizes well on the generated dataset and shows no significant signs of overfitting.

---

# 📊 Feature Importance

| Feature     | Importance |
| ----------- | ---------- |
| Turbidity   | 37.94%     |
| TDS         | 24.59%     |
| pH          | 16.48%     |
| Dry Days    | 16.14%     |
| Temperature | 4.85%      |

The model primarily relies on **Turbidity** and **TDS**, which are physically meaningful indicators of rainwater quality.

---

# ☁️ Cloud Deployment

The trained CatBoost model is deployed as a Flask API.

Workflow:

```
ESP32

↓

HTTP POST Request

↓

Cloud API

↓

CatBoost Model

↓

Water Class Prediction

↓

Recommendation

↓

ESP32

↓

Valve Control
```

---

# 🚰 Automatic Water Diversion

Based on the predicted class:

| Water Class             | Action                                                 |
| ----------------------- | ------------------------------------------------------ |
| Reject_First_Flush      | Continue diverting to waste                            |
| Poor_Needs_Treatment    | Send for treatment                                     |
| Fair_Non_Potable_Use    | Use for gardening / cleaning                           |
| Good_Store_After_Filter | Store after filtration                                 |
| Excellent_Store         | Store directly (disinfection recommended for drinking) |

---

# 📂 Project Structure

```
Adaptive-Rainwater-Quality-Classification-System

│

├── Dataset
│     └── rainwater_dataset.csv
│
├── Notebook
│     └── RainWater_Classifier.ipynb
│
├── Model
│     └── rainwater_catboost_model.pkl
│
├── API
│     └── app.py
│
├── ESP32
│     └── esp32_prediction.ino
│
├── Images
│
└── README.md
```

---

# ⚙️ Installation

Clone the repository

```bash
git clone https://github.com/yourusername/Adaptive-Rainwater-Quality-Classification-System.git
```

Install dependencies

```bash
pip install -r requirements.txt
```

Run the notebook

```bash
jupyter notebook
```

---

# 🚀 Future Improvements

* Collect real rainwater sensor data
* Retrain using real-world measurements
* Improve the Rainwater Quality Index (RQI)
* Mobile application for monitoring
* Solar-powered autonomous operation
* Edge AI inference directly on embedded hardware
* Integration with weather forecasting APIs
* Long-term cloud analytics dashboard

---

# 📚 Technologies Used

* Python
* Google Colab
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Scikit-Learn
* CatBoost
* LightGBM
* XGBoost
* Flask
* ESP32
* IoT
* Machine Learning

---

# 👨‍💻 Author

**Sanjay Saravanan**

B.Tech Electronics and Communication Engineering

VIT Chennai

---

# ⭐ Support

If you found this project interesting, consider giving it a ⭐ on GitHub. It helps others discover the project and motivates future development.

---

# 📜 License

This project is released under the MIT License and is intended for educational, research, and non-commercial purposes.
