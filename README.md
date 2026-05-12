# AIoT Lab 2 — Occupancy Detection & Smart Room Control

## Giới thiệu

Project AIoT Lab 2 xây dựng hệ thống phát hiện sự hiện diện trong phòng (Occupancy Detection) sử dụng dữ liệu cảm biến IoT và mô hình Machine Learning.

Hệ thống:
- Thu thập dữ liệu cảm biến môi trường
- Tiền xử lý dữ liệu
- Huấn luyện mô hình AI
- Phát hiện bất thường (Anomaly Detection)
- Triển khai REST API bằng FastAPI
- Public API bằng ngrok

---

# Công nghệ sử dụng

- Python 3
- Pandas
- NumPy
- Scikit-learn
- FastAPI
- Uvicorn
- Ngrok
- Google Colab

---

# Dataset

Dataset gồm các cảm biến môi trường:

- Temperature
- Humidity
- Light
- CO2
- HumidityRatio

Target:
- Occupancy (0/1)

---

# Cấu trúc project

```bash
project/
│
├── data/
│   ├── telemetry_clean.csv
│   └── feature_dataset.csv
│
├── models/
│   └── occupancy_baseline.joblib
│
├── outputs/
│   ├── metrics.json
│   ├── decision_log.csv
│   └── figures/
│
├── src/
│   ├── app.py
│   ├── data_utils.py
│   ├── run_training_pipeline.py
│   ├── test_api.py
│   └── check_outputs.py
│
├── requirements.txt
└── README.md


Cài đặt
Clone project
git clone <your-repo-url>
cd <repo-name>
Cài dependencies
pip install -r requirements.txt
Huấn luyện mô hình
python src/run_training_pipeline.py

Kết quả sinh ra:

cleaned dataset
trained model
metrics
visualization
decision logs
Kết quả model
Metrics
Accuracy: 99.43%
Precision: 97.51%
Recall: 99.91%
F1-score: 98.69%
ROC-AUC: 99.88%
Chạy FastAPI
uvicorn src.app:app --host 0.0.0.0 --port 8000
Swagger API Docs

Sau khi chạy server:

http://localhost:8000/docs
API Predict Example
Request
{
  "Temperature": 23.5,
  "Humidity": 27.0,
  "Light": 500,
  "CO2": 700,
  "HumidityRatio": 0.004
}
Response
{
  "input": {
    "Temperature": 23.5,
    "Humidity": 27.0,
    "Light": 500,
    "CO2": 700,
    "HumidityRatio": 0.004
  },
  "model_output": {
    "occupancy_probability": 0.6956,
    "predicted_occupancy": 1
  }
}
Triển khai bằng ngrok
from pyngrok import ngrok

public_url = ngrok.connect(8000)
print(public_url)
Kết quả đạt được
Xây dựng pipeline AIoT hoàn chỉnh
Huấn luyện mô hình occupancy detection
Triển khai REST API
Tích hợp AI decision engine
Public API bằng ngrok
