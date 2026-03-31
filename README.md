# AI-Based Hospital IVR Web Simulator 🚑📞

An advanced **AI-powered IVR system** designed for hospitals, built during the Infosys Springboard Internship.  
This project transforms traditional DTMF IVR into an **autonomous dispatch pipeline** using **Gemini 2.0 Flash + Cloud Speech AI**, with Twilio powering telephony integration.

---

## 🌐 Overview

Traditional hospital IVR systems suffer from:
- ❌ No language understanding (rigid DTMF menus)  
- ❌ Zero clinical intelligence (billing vs chest pain treated equally)  
- ❌ Manual emergency dispatch (human operator bottlenecks)  

Our solution introduces:
- ✅ Natural speech input via Twilio Voice  
- ✅ Clinical NLU for triage & urgency detection  
- ✅ Autonomous ambulance dispatch in seconds  
- ✅ Seamless caller experience with reduced stress  

---

## ⚙️ Architecture

**3-Tier Setup:**

- **Frontend:** React 18 + TypeScript + Vite  
- **Backend:** FastAPI (11 routers, async, rate-limited)  
- **Database + AI:** PostgreSQL (Aiven) + Gemini 2.0 Flash (STT/TTS)  

**Voice Pipeline:**
1. Twilio Voice → Audio Stream  
2. STT (Chirp 3) → Text  
3. NLU (BoW + Gemini) → Intent + Distress Score  
4. ILP Triage → Emergency / Urgent / Routine  
5. Dispatch → Haversine-based ambulance selection  

---

## 📞 Twilio Integration

Twilio acts as the **telephony gateway** for real-world deployment:

1. **Inbound Call Flow**
   - Caller dials hospital IVR number (Twilio provisioned).  
   - Twilio streams audio via WebSocket → Backend STT.  

2. **Outbound Dispatch**
   - Autonomous system triggers ambulance dispatch.  
   - Twilio Programmable Voice/SMS notifies paramedics in real-time.  

3. **Fallback Handling**
   - Graceful degradation with BoW model if LLM API fails.  
   - Dual playback (AudioContext + HTMLAudioElement) ensures caller audio reliability.  

---

## 🚀 Key Features

- **Autonomous Dispatch:** No human required for emergency calls.  
- **Clinical NLU:** Specialized parsing of medical details.  
- **Real-Time Streaming:** Low-latency audio via WebSocket.  
- **Graceful Degradation:** System never goes silent, fallback always available.  
- **Production-Grade:** Modular, upgradeable, and cloud-ready.  

---

## 📊 Real-World Applications

- 🏥 Hospital IVR replacement (drop-in for any DTMF system)  
- 🚑 Emergency response (ambulance dispatch in seconds)  
- 🌍 Telemedicine triage (remote severity assessment)  
- 📈 Clinical analytics (risk profiling, history tracking)  

---

## 🔮 Future Scope

- 🌐 Multi-language support (Hindi, Spanish, Tamil)  
- 📡 Real GPS tracking for ambulances  
- 🤖 ML-based triage model (clinical dataset trained)  
- 🗂️ EHR/EMR integration with hospital record systems  

---

## 🛠️ Setup & Deployment

### Prerequisites
- Node.js 18+  
- Python 3.11+  
- PostgreSQL (Aiven Cloud recommended)  
- Twilio Account (Voice + SMS enabled)  

### Installation
```bash
# Clone repo
git clone https://github.com/your-org/hospital-ivr-simulator.git
cd hospital-ivr-simulator

# Frontend setup
cd frontend
npm install
npm run dev

# Backend setup
cd backend
pip install -r requirements.txt
uvicorn main:app --reload
```

### Twilio Configuration
1. Buy a Twilio phone number.  
2. Configure **Voice Webhook** → Backend `/voice` endpoint.  
3. Enable **WebSocket streaming** for real-time STT.  
4. Set up **SMS/Voice notifications** for dispatch alerts.  

---
