# Team Console — Rural Healthcare Platform
### Smart India Hackathon 2025

A full-stack, microservices-based rural healthcare platform built for SIH 2025. Designed to bridge the healthcare gap in underserved communities by providing digital health tools accessible even in low-connectivity environments.

---

## Features

| Module | Description | Port |
|---|---|---|
| **Main Platform** | Central hub connecting all features (React + Vite) | 3000 |
| **Community Chat & Forum** | Real-time chat rooms, medical Q&A, doctor-verified posts | 5050 |
| **Skin Disease Detection** | AI-powered skin disease diagnosis using CNN (TensorFlow/Keras) | 5002 |
| **Village Health Hub** | Local health resources, nearby facilities & services | 5176 |
| **Pregnancy & Period Tracker** | Cycle tracking, pregnancy milestone monitoring | 5177 |
| **Blood Donation** | Donor matching, blood bank locator | 5178 |
| **Digital Health Records** | Secure cloud-backed personal health records (Firebase) | 3002 |
| **Medicine Availability Tracker** | Real-time pharmacy stock & medicine search | 5002 |
| **Video Consultation** | Live doctor-patient video calls (ZEGOCLOUD) | 5175 |
| **Unified Backend** | Aggregated API gateway for cross-service requests | 8000 |

---

## Tech Stack

**Frontend**
- React 18 (Community Chat)
- Vite + TypeScript (all other frontends)
- Tailwind CSS
- Socket.IO client (real-time chat)

**Backend**
- Node.js + Express (Chat service, Health Records)
- Python + Flask (Medicine API, Skin Disease API, Unified Backend)
- Socket.IO (real-time messaging)

**Database & Cloud**
- SQLite (Chat & community data)
- Firebase Firestore (Digital Health Records)
- MySQL (optional, supported)

**AI/ML**
- TensorFlow / Keras (CNN model for skin disease classification)
- Custom trained `.h5` model

**Integrations**
- ZEGOCLOUD (video calling)
- JWT authentication
- Role-based access (Patient / Doctor / Admin)

---

## Architecture

```
http://localhost:3000  ──►  Main Platform (Vite)
                              │
          ┌───────────────────┼───────────────────────┐
          │                   │                        │
  :5050 Chat API       :3002 Health Records     :8000 Unified API
  :5002 Medicine API   :5002 Skin Disease API
          │
  Micro-frontends (Vite, embedded via iframe/links):
  :3001  Skin Disease UI
  :5175  Video Calling
  :5176  Village Health Hub
  :5177  Pregnancy Tracker
  :5178  Blood Donation
```

---

## Getting Started

### Prerequisites
- Node.js v18+
- Python 3.11+
- npm

### Installation

```bash
# Clone the repo
git clone https://github.com/shaauryaa/team-console-healthcare.git
cd team-console-healthcare

# Install all JS dependencies
cd chat-sih && npm install && cd client && npm install && cd ../..
cd "Smart India Hackathon 2025/Digital health records" && npm install && cd ../..
cd "Smart India Hackathon 2025/Rural Healthcare Website Design (2)" && npm install && cd ../..
cd "Smart India Hackathon 2025/Rural Healthcare Website Design (2)/ZEGOCLOUD-VideoCalling-App-main" && npm install && cd ../../../..
cd "Village Health Hub" && npm install && cd ..
cd "Pregnancy and Period Tracker" && npm install && cd ..
cd "Blood Donation App Features" && npm install && cd ..
cd "Skin-Disease-Prediction-main/Skin Disease Prediction Form" && npm install && cd ../..

# Set up Python environments
python -m venv "Smart India Hackathon 2025/API/venv"
"Smart India Hackathon 2025/API/venv/Scripts/pip" install -r "Smart India Hackathon 2025/API/requirements.txt"
pip install bcrypt PyJWT  # additional deps

python -m venv "Smart India Hackathon 2025/unified-backend/venv"
"Smart India Hackathon 2025/unified-backend/venv/Scripts/pip" install -r "Smart India Hackathon 2025/unified-backend/requirements.txt"

python -m venv "Skin-Disease-Prediction-main/venv_new"
"Skin-Disease-Prediction-main/venv_new/Scripts/pip" install -r "Skin-Disease-Prediction-main/requirements.txt"
pip install flask-cors  # additional dep
```

### Environment Variables

Copy the example files and fill in your credentials:

```bash
cp chat-sih/env.example chat-sih/.env
cp "Smart India Hackathon 2025/Digital health records/.env.example" "Smart India Hackathon 2025/Digital health records/.env"
```

**`chat-sih/.env`**
```
PORT=5050
DB_TYPE=sqlite
DB_PATH=./database/community.db
JWT_SECRET=your-secret-key
```

**`Digital health records/.env`** — requires Firebase project credentials (see `.env.example`).

---

## Running the Project

Start each service in a separate terminal:

```bash
# 1. Main Website
cd "Smart India Hackathon 2025/Rural Healthcare Website Design (2)"
npx vite --port 3000 --host

# 2. Chat Backend
cd chat-sih && node server.js

# 3. Health Records API
cd "Smart India Hackathon 2025/Digital health records" && node server.js

# 4. Medicine API
cd "Smart India Hackathon 2025/API"
./venv/Scripts/python app.py

# 5. Unified Backend
cd "Smart India Hackathon 2025/unified-backend"
./venv/Scripts/python app.py

# 6. Skin Disease API (loads TensorFlow model ~30s)
cd "Skin-Disease-Prediction-main"
./venv_new/Scripts/python app.py

# 7-11. Micro-frontends
cd "Skin-Disease-Prediction-main/Skin Disease Prediction Form" && npx vite --port 3001
cd "Smart India Hackathon 2025/Rural Healthcare Website Design (2)/ZEGOCLOUD-VideoCalling-App-main" && npx vite --port 5175
cd "Village Health Hub" && npx vite --port 5176
cd "Pregnancy and Period Tracker" && npx vite --port 5177
cd "Blood Donation App Features" && npx vite --port 5178
```

Then open **`http://localhost:3000`**

> **Windows users:** Enable Long Path support before installing TensorFlow:
> Run PowerShell as Administrator → `Set-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Control\FileSystem" -Name "LongPathsEnabled" -Value 1`

---

## Team

**Team Console** — Smart India Hackathon 2025

---

## License

MIT
