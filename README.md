# 🌊 FloodSense AI — Smart Flood Prediction Platform

An intelligent flood prediction system that uses live weather data, machine learning, interactive maps, alerts, and an AI chatbot to estimate flood risk across Indian cities.

## Features

- **City-Based Prediction** — Enter a city name, auto-fetch live weather, get instant flood risk
- **Manual Prediction** — Enter weather parameters directly for any location
- **India Flood Risk Map** — Interactive Leaflet map with color-coded risk markers
- **Alerts & Notifications** — Auto-generated alerts for Moderate/High risk predictions
- **Analytics Dashboard** — Risk trends, rainfall charts, city comparisons
- **AI Chatbot** — RAG-based chatbot (Gemini + FAISS) answering flood safety & model questions
- **Prediction History** — Full history with city filtering

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | React 19, Vite, Tailwind CSS v4, Leaflet, Recharts |
| Backend | FastAPI, Python 3.11+ |
| ML | scikit-learn (Random Forest), joblib |
| Database | SQLite (portable, zero-config) |
| Weather | Open-Meteo API (free, no key needed) |
| AI Chatbot | Google Gemini (free tier), sentence-transformers, FAISS |

## Quick Start

### 1. Backend Setup

```bash
cd backend
pip install -r requirements.txt
```

Edit `backend/.env` and add your Gemini API key:
```
GEMINI_API_KEY=your_key_here
```

### 2. Train the ML Model

```bash
python ml/train.py
```

This generates `ml/model/flood_model.pkl` and `ml/model/scaler.pkl`.

### 3. Start the Backend

```bash
uvicorn backend.main:app --reload --host 0.0.0.0 --port 8000
```

API docs available at: http://localhost:8000/docs

### 4. Frontend Setup

```bash
cd frontend
npm install
npm run dev
```

Open http://localhost:5173

## API Endpoints

| Method | Route | Description |
|--------|-------|-------------|
| GET | /health | System health check |
| POST | /predict | Predict from manual weather input |
| POST | /predict-city | Predict by city (auto-fetches weather) |
| GET | /weather?city= | Get live weather for a city |
| GET | /weather/cities | List available cities |
| GET | /history | Prediction history |
| GET | /alerts | Alert history |
| POST | /chatbot | Ask the AI chatbot |
| GET | /map-data | City risk data for map |
| GET | /analytics | Dashboard analytics |

## Project Structure

```
├── frontend/          React + Vite + Tailwind
├── backend/           FastAPI + Python services
│   ├── routes/        API route handlers
│   ├── services/      Business logic (ML, Weather, DB, Chat, Alerts)
│   └── models/        Pydantic request/response models
├── ml/                Training script + saved model
├── knowledge_base/    Chatbot PDF knowledge base
├── database/          SQLite DB (auto-created)
└── training/          CSV training data
```

## Disclaimer

This is an AI-based flood risk estimation platform. It supports decision-making but does not replace official disaster agencies (IMD, NDRF, CWC).
