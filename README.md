# 🌍 Factory Emissions Visualizer

This project is a satellite-powered environmental monitoring tool that detects abnormal thermal emissions around industrial areas.
Built using **Google Earth Engine, Python, Streamlit, Folium, and ML-based anomaly detection**, it identifies temperature hotspots, scores emission severity, and visualizes results on an interactive map.

---

## 🔥 Why This Project Is Useful

* Detects **thermal anomalies** caused by waste burning, leaks, illegal emissions, or overheated machinery
* Uses **real satellite data** — unbiased and independent of on-site sensors
* Ideal for **government regulators, smart-city systems, ESG analysis, and industrial audits**
* Fully automated pipeline: **Fetch → Detect → Score → Visualize**
* Lightweight, fast, and easy to extend

---

## 🛠️ Tech Stack

* **Satellite Data:** Google Earth Engine (Landsat-9 LST)
* **ML Model:** Isolation Forest (Scikit-Learn)
* **Frontend/UI:** Streamlit
* **Geospatial Visualization:** Folium + Matplotlib
* **Backend Logic:** Python
* **Deployment Ready:** Works locally or on cloud platforms (Streamlit Cloud, GCP, etc.)

```
Factory-Emission-Visualizer/
 ├── app.py
 ├── anomaly.py
 ├── fetchLST.py
 ├── folium_map.py
 └── key.json            # GEE service account credentials (DO NOT COMMIT)
```

---

## 📦 File-by-File Overview

### **1. app.py — Main Application (Streamlit UI)**

* Takes user input (latitude & longitude)
* Fetches LST data from Google Earth Engine
* Runs anomaly detection and computes emission score
* Displays metrics (max/min/mean LST, anomaly count, emission score)
* Renders an interactive Folium-based heatmap

> **This is the main entry point of the project.**

---

### **2. anomaly.py — ML-Based Temperature Anomaly Detector**

* Downloads `.npy` temperature grid
* Removes invalid pixels
* Detects hotspots using **Isolation Forest**
* Generates a **0–100 emission severity score**

> **The core intelligence/ML logic lives here.**

---

### **3. fetchLST.py — Google Earth Engine Data Fetcher**

* Authenticates using a service account
* Filters Landsat-9 LST images (cloud-free, last 30 days)
* Converts DN → Kelvin → °C
* Produces a downloadable `.npy` array

> **This module retrieves real satellite data.**

---

### **4. folium_map.py — Geospatial Visualization Engine**

* Uses Matplotlib to render temperature heatmap
* Highlights anomaly pixels
* Converts plot into base64 image
* Displays it as a Folium overlay with markers

> **This file generates the interactive visual output.**

---

## 🚀 Running the Project

### 1. Install dependencies

Manually install the required libraries:

```bash
pip install streamlit folium scikit-learn numpy matplotlib google-earth-engine
```

### 2. Add your Earth Engine credentials

Place your **key.json** file in the project folder.

### 3. Run the Streamlit app

```bash
streamlit run app.py
```

### 4. Enter factory coordinates

Example:

```
Latitude: 20.95150000
Longitude: 85.21570000
```

Click **Analyze Emissions** to view:

* Heatmap overlay
* Detected anomaly pixels
* Emission severity score
* Summary statistics

---

## 📌 Future Improvements

* Time-series anomaly tracking
* Multi-factory comparison
* High-resolution LST (ECOSTRESS) support
* Automated pollution alerts
* Historical emission reporting dashboard

---

## 📄 License

This project is fully open-source and free to modify.
