# SightSpot AI 🚗🏙️
> **Smarter Parking. Safer Cities.**  
> An AI-powered smart-city command center predicting urban parking violations using CatBoost Poisson regression, spatiotemporal geohash grids, and Google Gemini LLM tactical briefings.

[![React](https://img.shields.io/badge/React-18.3.1-61DAFB?style=flat&logo=react&logoColor=black)](https://react.dev/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.6-3178C6?style=flat&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![Vite](https://img.shields.io/badge/Vite-6.0-646CFF?style=flat&logo=vite&logoColor=white)](https://vitejs.dev/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-3.4-38B2AC?style=flat&logo=tailwind-css&logoColor=white)](https://tailwindcss.com/)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.133-009688?style=flat&logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com/)
[![CatBoost](https://img.shields.io/badge/CatBoost-1.2-F58025?style=flat&logo=yandex&logoColor=white)](https://catboost.ai/)
[![Docker](https://img.shields.io/badge/Docker-Ready-2496ED?style=flat&logo=docker&logoColor=white)](https://www.docker.com/)

---

## 🌟 Key Highlights

- **Futuristic AI Command Center UI**: Dark navy `#050B18` glassmorphism aesthetic with cyan, purple, and neon accents.
- **Predictive ML Core**: CatBoost Poisson Regressor trained on cyclic temporal encodings (`hour_sin`, `day_cos`) and precision-7 geohashes.
- **LLM Tactical Integration**: Google Gemini AI generates real-time patrol dispatch briefings by fusing ML predictions with live weather data (Open-Meteo).
- **Interactive Spatiotemporal Mapping**: 24-hour time-lapse heatmap playback, 3D Isometric Drone tilt, and pulsing radar hotspots built on Leaflet.
- **Voice Commander**: Web Speech API integration for hands-free dashboard navigation and predictive queries.

---

## 🏗️ Architecture

```text
 USER SELECTION (React Frontend)
   │
   ├── 📍 Location (Latitude, Longitude)
   ├── 📅 Date (e.g. 17 September 2026)
   └── 🕐 Time (e.g. 06:00 PM)
         │
         ▼ POST /api/predict
 FASTAPI BACKEND (AWS EC2 Docker Container)
   │
   ├── 1. Spatiotemporal Encoding (pygeohash + NumPy sine/cosine)
   ├── 2. Live Weather Fetch (Open-Meteo API)
   ├── 3. Violation Forecasting (CatBoost Poisson Regressor)
   └── 4. Tactical Briefing Generation (Google Gemini 1.5 Flash LLM)
         │
         ▼ JSON RESPONSE
 DASHBOARD (AWS Amplify)
   • Predicted Violations & Risk Level (Low, Medium, High, Very High)
   • AI Insight Dispatch Directives
   • Mathematical 5-feature vector inspector
```

---

## 🚀 Quick Start (Local Development)

### 1. Prerequisites
- **Node.js**: v18+ 
- **Python**: 3.10+
- **Docker** (Optional for containerized backend)

### 2. Frontend Setup
```bash
cd frontend
npm install
npm run dev
```
The dashboard will be live at `http://localhost:5173/`.

### 3. Backend Setup
Create a `.env` file inside the `backend/` directory and add your Google Gemini API key:
```env
GEMINI_API_KEY=your_api_key_here
```

Then, start the server:
```bash
cd backend
pip install -r requirements.txt
python main.py
```
The backend API will be live at `http://127.0.0.1:8000/`.

---

## ☁️ Production Deployment (AWS)

SightSpot AI is fully containerized and configured for high-availability cloud deployment:

1. **Backend (AWS EC2)**: 
   SSH into your EC2 instance and run `sudo docker compose up --build -d` at the repository root to launch the FastAPI and ML inference pipeline.
2. **Frontend (AWS Amplify)**: 
   Connect the repository to AWS Amplify. Ensure the build configuration uses `--prefix frontend` and inject your EC2's public IP address as the `VITE_API_BASE_URL` environment variable.

---

## 📊 ML Model Information

- **Algorithm**: `CatBoostRegressor`
- **Objective Function**: `Poisson` (Count-based loss)
- **Features**: `geohash`, `hour_sin`, `hour_cos`, `day_sin`, `day_cos`
- **Artifacts**: `parksight_model.cbm`, `top_geohashes.json`

---

## 📜 License
MIT License. Created by Anurag Sinha, Ansh Kumar, and Sourabh Bajaj for the Build Bharat Hackathon.
