🌍 Factory Emissions Visualizer

A satellite-driven anomaly detection and emissions-scoring dashboard

📌 Overview

Factory Emissions Visualizer is a satellite-powered environmental monitoring tool that detects abnormal thermal emissions from industrial sites.
It uses Landsat-9 Land Surface Temperature (LST) data from Google Earth Engine, performs ML-based anomaly detection, and visualizes results on an interactive Streamlit dashboard with Folium map overlays.

This tool allows users to enter any factory’s latitude and longitude and instantly view:

Hotspot anomalies around the facility

Pixel-level temperature maps

Data-driven emission score (0–100)

Temperature statistics (min, max, mean)

🛰️ Key Features
✔ Fetches real satellite data

Uses Google Earth Engine (GEE)

Landsat-9 thermal band (ST_B10)

Last 30 days composite

Converts DN → Kelvin → Celsius

Downloads pixel data as .npy

✔ ML-based anomaly detection

Isolation Forest (unsupervised outlier detection)

Flags abnormally hot pixels

Robust to noise & cloud variations

Works even with partially missing data

✔ Emission scoring

A custom scoring system combining:

Component	Weight	Description
Severity	70%	How hot anomalies are compared to average
Density	30%	Number of anomalies relative to all valid pixels

Produces a 0–100 score → higher means more emissions.

✔ Interactive map visualization

Folium base map

Thermal image overlay (hot colormap)

Cyan-highlighted anomaly pixels

Factory marker

✔ Streamlit Dashboard

Displays:

Map visualization

Anomaly count

Temperature metrics

Emission score

Real-time analysis workflow

📂 Project Structure
Factory-Emission-Visualiser/
│
├── app.py                # Main Streamlit application
├── anomaly.py            # ML anomaly detection + emission scoring
├── fetchLST.py           # Google Earth Engine LST downloader
├── folium_map.py         # Visualization map generation
├── key.json              # GEE service account credentials (private)
└── README.md             # Project documentation

🧠 Code Explanation (High-Level)
app.py

Streamlit frontend:

Takes coordinates

Calls data fetch + anomaly detection + scoring

Renders map & metrics

anomaly.py

Contains:

analyze_anomalies() → ML outlier detection

calculate_emission_score() → final emission score

fetchLST.py

Handles:

GEE authentication

Landsat-9 data filtering

Temperature conversion

.npy export URL generation

folium_map.py

Generates:

A color-coded LST image

Cyan anomaly markers

Overlay on Folium map

⚙️ Installation & Setup
1. Clone the repository
git clone https://github.com/anirudham986/Factory-Emission-Visualiser
cd Factory-Emission-Visualiser

2. Install dependencies

If requirements.txt exists:

pip install -r requirements.txt


Or install manually:

pip install numpy requests scikit-learn folium matplotlib streamlit streamlit-folium earthengine-api

3. Add your Google Earth Engine credentials

Place your service account key file as:

key.json


And ensure the email inside the script matches your GEE service account.

🚀 Running the Application

Start the dashboard:

streamlit run app.py


The app will open at:

http://localhost:8501/

🎯 Usage

Enter latitude & longitude of a factory

Click Analyze Emissions

Wait ~5–15 seconds while:

Satellite data is fetched

ML model detects hotspots

Emission score is computed

Explore:

Interactive thermal map

Cyan anomalies

Temperature metrics

Emission score

📈 Real-World Applications

ESG audits & reporting

Industrial compliance tracking

Thermal pollution monitoring

Environmental forensics

Factory site inspections

Government monitoring dashboards

🔐 Security Note

key.json contains sensitive private keys.
Do not commit it to public GitHub repositories.

Add to .gitignore:

key.json

🛠 Future Improvements (Suggested)

Time-series anomaly tracking across months

Multi-band analysis (NO₂, SO₂, PM estimation)

GeoTIFF export support

Fully automated batch processing

Emission benchmarking across multiple facilities

Web deployment (Streamlit Cloud / GCP / AWS)
