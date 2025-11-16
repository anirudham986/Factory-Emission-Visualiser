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
 ├── key.json              # GEE service account credentials (DO NOT COMMIT)
```

---

## 📦 File-by-File Overview

### **1. app.py — Main Application (Streamlit UI)**

* Handles user input (latitude & longitude)
* Fetches LST data through Google Earth Engine
* Runs anomaly detection
* Computes emission severity score
* Renders heatmap + markers on an interactive map
* Displays metrics (max/min/mean LST, anomaly count, emission score)

> **This is the file you run — the full workflow starts here.**

---

### **2. anomaly.py — ML-Based Temperature Anomaly Detector**

* Downloads `.npy` LST grid
* Filters NaN and invalid pixels
* Detects abnormal temperature hotspots using **Isolation Forest**
* Calculates a **severity score (0–100)** based on intensity & density of anomalies

> **This is the intelligence layer of your project.**

---

### **3. fetchLST.py — Google Earth Engine Data Fetcher**

* Initializes Earth Engine with a service account
* Pulls cloud-free Landsat-9 LST data (last 30 days)
* Converts raw DN → Kelvin → °C
* Exports LST as a downloadable `.npy` array

> **This module brings real satellite data into your app.**

---

### **4. folium_map.py — Geospatial Visualization Engine**

* Plots LST grid with Matplotlib
* Highlights anomaly pixels in cyan
* Converts plot → base64 → Folium overlay
* Renders an interactive map with factory marker

> **This is what makes the results visually understandable.**

---

## 🚀 Running the Project

### 1. Install dependencies

```bash
pip install -r requirements.txt
```

### 2. Add your Earth Engine credentials

Place your **key.json** file in the project directory.

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

Click **Analyze Emissions**.

You will see:

* LST heatmap
* Highlighted anomaly pixels
* Emission severity score
* Summary metrics

---

## 📌 Future Improvements

* Time-series emission trends
* Multi-factory comparison dashboard
* Automatic pollutant classification
* Integration with government pollution APIs
* Threshold-based alert system

---

## 📄 License

This project is fully open-source and free to modify.
