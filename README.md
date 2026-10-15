# Smart Highway 360° 🛣️

### AI-Powered Highway Safety, Traffic Monitoring & Emergency Response Platform

[![React](https://img.shields.io/badge/React-19.2-blue.svg)](https://react.dev/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.x-blue.svg)](https://www.typescriptlang.org/)
[![Vite](https://img.shields.io/badge/Vite-6.x-purple.svg)](https://vitejs.dev/)
[![Tailwind CSS](https://img.shields.io/badge/TailwindCSS-3.4-38bdf8.svg)](https://tailwindcss.com/)
[![FastAPI](https://img.shields.io/badge/FastAPI-Python-009688.svg)](https://fastapi.tiangolo.com/)
[![Leaflet](https://img.shields.io/badge/Leaflet-Maps-199900.svg)](https://leafletjs.com/)

---

## 📌 Executive Summary

Modern highways face critical challenges: delayed emergency assistance, undetected pavement cavities causing fatal rim blowouts, severe driver micro-sleeps, sudden dense winter fog pile-ups, and fragmented road maintenance workflows.

**Smart Highway 360°** is a comprehensive, production-minded digital corridor safety and emergency management platform. It unifies:
1. **Interactive Leaflet Corridor Mapping**: Categorized hazard markers, severity filters, live search, and nearby trauma care hubs.
2. **Deep Vision AI Accident Detection**: Analyzes highway CCTV, drone, and dashcam feeds for sudden multi-vehicle impacts and speed vectors.
3. **Pothole & Pavement Distress Segmentation**: Deep learning surface cavity analysis with estimated depth index (cm) and automated PWD work-orders.
4. **Driver Fatigue & Drowsiness Vision**: Client-side face landmark monitoring evaluating Eye Aspect Ratio (EAR) with synthesized audio sirens and rest-stop guidance.
5. **Highway Gantry Radar Speed Monitoring**: Vehicle plate ANPR telemetry, configurable zone limits, distribution charts, and CSV audit reports.
6. **Corridor Traffic & Detour Awareness**: Delay predictions and automated bypass routing around major bottlenecks.
7. **Atmospheric Weather Hazards**: Live Open-Meteo satellite feed tracking fog, rainfall, crosswinds, and hydroplaning risks.
8. **Emergency SOS Roadside Dispatch**: Prominent SOS button with browser geolocation, honest transmission disclosures, and 24/7 helpline integration.
9. **Authority Control Center**: Multi-role review queue for highway administrators to verify AI alerts, assign repair squads, and manage audit trails.
10. **Blackspot AI Risk Analytics**: Transparent multi-factor regression index (0-100) identifying chronic high-risk corridor zones.
11. **Multilingual Inclusivity**: Full support for **English**, **Telugu (తెలుగు)**, and **Hindi (हिंदी)**.

---

## 🏗️ System Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                   Smart Highway 360° UI                     │
│  (React 19 + TypeScript + Vite + Tailwind CSS + Recharts)   │
└──────────────┬──────────────────────────────┬───────────────┘
               │                              │
    REST / Client-side CV          Realtime / REST API
               │                              │
┌──────────────▼──────────────┐  ┌────────────▼───────────────┐
│     AI Vision Service       │  │    PostgreSQL Database     │
│   (Python FastAPI + OpenCV) │  │  (Supabase RLS / Fallback) │
├─────────────────────────────┤  ├────────────────────────────┤
│ • /api/detect-accident      │  │ • Incidents & Attachments  │
│ • /api/detect-pothole       │  │ • Emergency SOS Requests   │
│ • /api/detect-fatigue       │  │ • Speed & Radar Telemetry  │
│ • /health                   │  │ • User Profiles & Roles    │
└─────────────────────────────┘  │ • Immutable Audit Logs     │
                                 └────────────────────────────┘
```

---

## ⚡ Quick Start & Installation

### Prerequisites
- Node.js (v18+)
- Python (v3.10+) for the optional FastAPI microservice
- Modern web browser (Chrome, Edge, Firefox, Safari)

### 1. Clone & Install Frontend
```powershell
# Install frontend dependencies
npm install --legacy-peer-deps

# Run development server
npm run dev
```
Open **`http://localhost:5173`** in your browser.

### 2. Run Automated Tests
```powershell
npm test
```

### 3. Production Build
```powershell
npm run build
```

---

## 🐍 Python AI Microservice (Optional)

The frontend features a client-side computer vision engine that works out of the box. To run the dedicated Python FastAPI backend:

```powershell
cd ai-backend

# Create virtual environment
python -m venv venv
.\venv\Scripts\activate

# Install requirements
pip install -r requirements.txt

# Run FastAPI server
uvicorn main:app --reload --port 8000
```
API Documentation will be live at: **`http://localhost:8000/docs`**

---

## 🗄️ Database Setup (Supabase / PostgreSQL)

1. Create a free project on [Supabase](https://supabase.com/).
2. Navigate to the **SQL Editor**.
3. Copy and run [`database/schema.sql`](file:///c:/Users/upend/Downloads/kiran%201/database/schema.sql) to create all tables and RLS security policies.
4. Optionally run [`database/seed.sql`](file:///c:/Users/upend/Downloads/kiran%201/database/seed.sql) to populate initial sample incidents.
5. Create a `.env` file in the project root:
```env
VITE_SUPABASE_URL=https://your-project.supabase.co
VITE_SUPABASE_ANON_KEY=your-anon-key
VITE_AI_SERVICE_URL=http://localhost:8000
```

> **Note:** If Supabase credentials are not provided, the application automatically runs in **Self-Contained Demonstration Mode** backed by local storage and seeded test fixtures.

---

## 🎭 User Roles & Demo Workflow

Smart Highway 360° supports 3 distinct user roles with 1-click role switching in the navigation bar:

1. **Motorist Driver** (`Kiran Verma`):
   - Report road damage, potholes, and obstacles with GPS & photo evidence.
   - Access the one-click Emergency SOS modal with instant dispatch tracking.
   - Run Driver Fatigue AI with live webcam and rest stop recommendations.
2. **Highway Administrator** (`Vikram Joshi, NHAI Patrol`):
   - Review incoming hazard reports in the Review Queue.
   - Verify AI vision accident detections.
   - Assign specialized repair crews (e.g., *PWD Rapid Asphalt Repair Crew B*).
   - Mark incidents as Resolved with resolution audit notes.
3. **System SuperAdmin** (`Dr. Priya Sharma, Chief Architect`):
   - Configure gantry radar speed limits.
   - Inspect full immutable System Audit Trail.
   - Analyze Blackspot AI risk indexes and corridor engineering actions.

---

## 🏆 Hackathon Demonstration Script (5-Minute Pitch)

1. **Landing Page**: Introduce the mission — *"Making Every Highway Journey Safer"*.
2. **Dashboard**: Highlight real-time KPI metrics, weekly trends, and road repair lifecycle progress.
3. **Live Map**: Show active incidents across Indian expressway corridors with category filtering and legend.
4. **AI Accident Detection**: Select *CCTV Feed #09*, run detection, view bounding boxes, impact speed vector (82 km/h), and click **Verify & Escalate Incident**.
5. **AI Pothole Inspection**: Analyze road cavity photo, showcase estimated depth (11 cm), and click **Create PWD Repair Work-Order**.
6. **Driver Fatigue Monitor**: Click **Enable Live Camera** (or use the *Drowsy* simulation preset) to demonstrate Eye Aspect Ratio (EAR) drop and trigger synthesized alarm sirens.
7. **Emergency SOS Hub**: Trigger the SOS modal, capture browser GPS, and observe real-time simulated 108 ambulance dispatch.
8. **Admin Control Center**: Switch role to Highway Admin, review verified incidents, and assign a rapid repair squad.
9. **Reset Demo State**: Click **Reset Demo State** in the sidebar to reset the entire environment cleanly for the next judge!

---

## 📜 Ethical Disclosure & Safeguards

- **Simulated vs. Live Feeds**: All sample video and radar telemetry feeds are clearly labeled as simulated to maintain integrity during hackathon judging.
- **Privacy First**: Driver fatigue video frames are processed purely client-side within browser memory and are **never** stored or uploaded.
- **Due Process**: Speed radar observations provide corridor calming analytics; statutory citations require calibrated legal gantry hardware.
"# kiran" 
