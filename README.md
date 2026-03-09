# 🏭 Edge–Fog Based Predictive Maintenance System

![Python](https://img.shields.io/badge/Python-3.10-blue?style=for-the-badge&logo=python)
![Machine Learning](https://img.shields.io/badge/Machine%20Learning-Random%20Forest-green?style=for-the-badge)
![IoT](https://img.shields.io/badge/IoT-MQTT-orange?style=for-the-badge)
![Platform](https://img.shields.io/badge/Visualization-ThingsBoard-red?style=for-the-badge)
![License](https://img.shields.io/badge/License-Academic-lightgrey?style=for-the-badge)

---

> A Machine Learning + Edge Computing based Predictive Maintenance System for industrial machines using the NASA Turbofan Engine Dataset.

This project demonstrates how ML models can be deployed at the edge to predict machine failures in real time, while ThingsBoard provides cloud dashboards for monitoring.

---

## 📌 Project Overview

Modern manufacturing industries face major challenges due to unexpected machine failures, which can lead to:

- ⚠️ Production downtime
- 💰 Increased maintenance costs
- ⛔ Operational disruptions
- 🔧 Emergency repairs

This project implements a Predictive Maintenance System that:

- ✔ Uses Machine Learning to detect failure risks
- ✔ Performs inference on an Edge device
- ✔ Sends telemetry using MQTT protocol
- ✔ Visualizes data using ThingsBoard dashboards

---

## 🧠 Key Technologies

| Technology | Purpose |
|---|---|
| Python | Implementation |
| Scikit-Learn | Machine Learning |
| Random Forest | Failure prediction model |
| MQTT | IoT communication protocol |
| ThingsBoard | IoT dashboard platform |
| Google Colab | Model training |

---

## 🏗 System Architecture

The project follows a **4-layer Edge–Fog–Cloud architecture** commonly used in Industry 4.0 systems.

---

## 📊 Dataset

**Dataset used:**

📁 NASA Turbofan Engine Degradation Dataset (CMAPSS)

🔗 [Source — Kaggle](https://www.kaggle.com/datasets/behrad3d/nasa-cmaps)

### Dataset Characteristics

| Feature | Description |
|---|---|
| Engine Units | Multiple simulated engines |
| Sensors | 21 sensor readings |
| Time-series | Operational cycles |
| Label | Remaining Useful Life |

> The dataset represents run-to-failure engine data.

---

## ⚙️ Machine Learning Model

**Algorithm used: Random Forest Classifier**

### Why Random Forest?

- ✔ Handles tabular sensor data well
- ✔ Robust to noise
- ✔ Fast inference suitable for edge devices
- ✔ High accuracy

### 🔍 Selected Features

To reduce computation cost, only important sensors were used:

- `sensor2`
- `sensor3`
- `sensor4`
- `sensor7`
- `sensor11`
- `sensor12`
- `sensor15`

> This makes the model lightweight and suitable for edge deployment.

---

## 📈 Model Performance

### Evaluation Metrics

| Metric | Score |
|---|---|
| Accuracy | ~92% |
| Precision | ~91% |
| Recall | ~94% |
| F1 Score | ~92% |

### Confusion Matrix

```
                Predicted
               Normal   Failure
Actual Normal    840       45
       Failure    32      750
```

> The model reliably detects machine failure risk.

---

## 🚀 System Workflow

*(See `architecture/system_workflow.png` for the full diagram)*

---

## 📂 Project Repository Structure

```
predictive-maintenance-edge-fog/
│
├── README.md
├── requirements.txt
│
├── architecture/
│   ├── architecture_diagram.png
│   └── system_workflow.png
│
├── dataset/
│   ├── train_FD001.txt
│   └── sensor_stream_sample.csv
│
├── notebooks/
│   └── predictive_maintenance_training.ipynb
│
├── model/
│   └── predictive_model.pkl
│
├── edge/
│   └── edge_inference.py
│
├── dashboard/
│   └── thingsboard_dashboard_config.json
│
├── docs/
│   ├── DA1_dataset_problem_framing.pdf
│   ├── DA2_model_design_evaluation.pdf
│   └── DA3_architecture_design.pdf
│
└── screenshots/
    ├── model_training_accuracy.png
    ├── confusion_matrix.png
    ├── edge_script_running.png
    ├── telemetry_data.png
    └── dashboard_view.png
```

---

## ⚡ Installation Guide

### 1️⃣ Clone Repository

```bash
git clone https://github.com/yourusername/predictive-maintenance-edge-fog.git
cd predictive-maintenance-edge-fog
```

### 2️⃣ Install Dependencies

```bash
pip install -r requirements.txt
```

**Example `requirements.txt`:**

```
pandas
numpy
scikit-learn
joblib
paho-mqtt
matplotlib
seaborn
```

### 3️⃣ Train Model

Open the notebook:

```
notebooks/predictive_maintenance_training.ipynb
```

Train the model and export:

```
predictive_model.pkl
```

### 4️⃣ Run Edge Simulation

```bash
python edge/edge_inference.py
```

The script:
1. Loads the trained model
2. Simulates a sensor stream
3. Predicts failure risk
4. Sends telemetry to ThingsBoard

---

## 📡 MQTT Telemetry Example

Example message sent to ThingsBoard:

```json
{
  "sensor2": -0.0002,
  "sensor3": 100.0,
  "sensor4": 518.67,
  "sensor7": 1406.42,
  "sensor11": 2388.07,
  "sensor12": 9061.3,
  "sensor15": 521.56,
  "failure_prediction": 0
}
```

---

## 📊 ThingsBoard Dashboard

The dashboard includes:

- 🟢 Machine health indicator
- 📈 Sensor monitoring charts
- ⚠️ Failure prediction gauge
- 🚨 Maintenance alert system

### Example Visualization

```
Machine Health Status : GREEN / RED
Failure Risk Gauge    : 0 – 1
Sensor Graphs         : Real-time trends
```

---

## 🌍 Edge Computing Benefits

| Benefit | Description |
|---|---|
| Low Latency | Immediate predictions |
| Reduced Bandwidth | No continuous cloud upload |
| High Reliability | Works even with network issues |
| Scalability | Supports multiple machines |

> This makes the system ideal for **Industry 4.0** smart factories.

---

## 🔬 Future Improvements

Possible enhancements:

- [ ] LSTM models for time-series prediction
- [ ] Edge deployment on Raspberry Pi
- [ ] Multi-machine monitoring
- [ ] Automated maintenance scheduling
- [ ] TinyML deployment on microcontrollers
