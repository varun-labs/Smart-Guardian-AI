![Smart Guardian Banner](assets/smart-g-image.png)

# 🧠 Smart Guardian AI

**Smart Guardian** is an AI-first safety assistant for households and childcare centers.  
It monitors live camera feeds, identifies enrolled kids, overlays adaptive hazard zones, and proactively alerts caregivers (via voice or email) when a child nears danger or exhibits risky behavior.

---

## 🌟 Why Smart Guardian?

- **Proactive Safety** – Combines YOLO detection, Mediapipe pose analysis, and behavior forecasting to warn *before* accidents occur.  
- **Kid-Aware Recognition** – Facial embedding and enrollment workflow enable Smart Guardian to call out each child by name.  
- **Human-in-the-Loop Design** – A Streamlit interface allows caregivers to draw hazard zones, auto-scan environments, switch cameras, and manage alerts.  
- **Edge-Ready Deployment** – Runs locally (desktop, Docker, or Raspberry Pi) with no cloud dependency, except optional LLM scans or Brevo email alerts.

---

## 🧱 Architecture & Tech Stack

| Layer | Technology |
|-------|-------------|
| Live Inference | YOLOv8 + Mediapipe Pose (PyTorch, OpenCV) |
| Hazard AI | Gemini / OpenAI Vision Prompts for zone suggestions |
| Backend | FastAPI + SQLite + asyncio camera loop |
| User Interface | Streamlit console (zones, analytics, settings) |
| Notifications | macOS `say` TTS + Brevo email alerts |
| Analytics | Altair + Pandas (movement trends, risk forecasts) |

**System Flow:**  
```
Camera → YOLO → Pose/Behavior Logic → Zone Logic → Alerts + Logging
              ↓                        ↑
        Streamlit UI (zones, LLM scans, settings, analytics)
```

---

## ⚙️ Key Features

### 🎥 Real-Time Video Overlay  
- Displays hazard polygons, YOLO bounding boxes, skeletons, and recognized kid names.  

### 🧒 Kid Enrollment & Recognition  
- Upload or capture photo → crop → embed → face-match per frame.  

### 🧭 Adaptive Hazard Zones  
- Draw zones manually on live frames.  
- Auto-scan suggestions using object detection.  
- AI-based hazard scan via Gemini/OpenAI prompts (“Ask AI hazard scan”).  

### 🔔 Alerting System  
- Voice alerts via macOS `say` (configurable voice).  
- Email alerts via Brevo (enable/disable, stored credentials).  
- Built-in cooldown logic prevents alert spam.  

### 📊 Behavior Analytics  
- Event-based tracking (position, speed, hazard distance).  
- Risk forecast cards (Low/Medium/High per child).  
- Altair charts showing speed and proximity trends, exportable to CSV via SQLite.

---

## 📈 Activity Dashboard Highlights

- **Summary Table** – Event logs, average speed, last seen per child.  
- **Risk Forecast** – Aggregated near-zone behavior highlighting active explorers.  
- **Movement Trends** – Altair chart visualizing kid speed over time with filters.

---

## ⚙️ Configuration & Environment

| File | Purpose |
|------|----------|
| `.env` | `RTSP_URL`, `CAMERA_ID`, `ALERT_VOICE`, `OPENAI_API_KEY`, `GOOGLE_API_KEY` |
| `configs/camera.json` | Current camera source |
| `configs/zones.json` | Saved hazard polygons |
| `configs/alerts.json` | Brevo credentials + enable flag |
| `configs/llm.json` | LLM provider & API model keys |
| `database/smart_guardian.db` | Local SQLite database *(ignored in .git)* |

---

## 🧭 Roadmap

- 📱 Multi-channel alerts (SMS, push, MQTT)  
- 🗺️ Autonomous semantic room mapping  
- 📅 Weekly PDF/email safety reports  
- 🐳 Containerized deployment with Raspberry Pi optimizations  

---

## 📸 Screenshots

*(Replace with actual screenshots or demo videos)*  
![Smart Guardian Demo](https://via.placeholder.com/800x400?text=Smart+Guardian+Demo)

---

## 📬 Request Access to Code

To access the **private code repository** for educational or research use:  
👉 [**Fill this form**](https://docs.google.com/forms/d/e/1FAIpQLSdatf3kB36Tg9pElqB4yf2ZmVKVA89iWsyAMHTKnUkZ55mVWg/viewform?usp=dialog)  
📧 Please include your **GitHub username** when submitting.  

Access is granted **manually** for learning purposes only.  

---

## ⚖️ License & Usage

- Shared for **educational, non-commercial purposes only**.  
- Redistribution of this code or models is **not permitted**.  
- Please credit **Varun Labs** if you use or reference this work in research, teaching, or derivative projects.

---

## 💬 Questions & Support

- Open a **Discussion** in this repository for questions or suggestions.  
- Or reach me at **jose.pariyani@gmail.com**.

---

> 🔗 Explore more projects at [**Varun Labs Portal**](https://github.com/varun-labs)  

---

### 🪪 License
**MIT License** *(or your preferred license)*  

---

Made with ❤️ to keep curious kids safer.
