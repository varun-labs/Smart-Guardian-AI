 Smart Guardian MVP

Smart Guardian is an AI-first safety assistant for households and childcare centers. It watches a live camera stream, identifies enrolled kids, overlays adaptive hazard zones, and proactively alerts caregivers (voice, email) when a child gets too close to danger or adopts a risky posture.

## Why Smart Guardian?

- **Proactive safety** – Combines YOLO detection, Mediapipe pose analysis, and behavior forecasting to warn *before* an accident.
- **Kid-aware** – Facial embedding + enrollment workflow lets Smart Guardian call out children by name.
- **Human-in-the-loop** – Streamlit UI for drawing zones, autoscan suggestions, camera switching, and alert/channel settings.
- **Edge-ready** – Runs locally (desktop, Docker, Raspberry Pi) with no cloud dependency except optional LLM scans or Brevo email.

## Architecture & Tech Stack

| Layer | Tech |
| --- | --- |
| Live inference | YOLOv8 + Mediapipe Pose (PyTorch/OpenCV) |
| Hazard AI | Gemini / OpenAI vision prompt for zone suggestions |
| Backend | FastAPI, SQLite, asyncio camera loop |
| UI | Streamlit console (zones, activity dashboard, settings) |
| Notifications | macOS `say` TTS + Brevo email alerts |
| Analytics | Altair + Pandas (movement trends, risk forecasts) |

```
Camera → YOLO → pose/behavior logic → zone logic → alerts + logging
              ↓                        ↑
         Streamlit UI (zones, LLM scans, settings, analytics)
```

## Key Features

- **Real-time video overlay**: Hazard polygons, YOLO boxes, skeletons, kid names.
- **Kid enrollment & recognition**: Upload/capture photo, crop, embed, face-match per frame.
- **Adaptive zones**:
  - Manual drawing on live frame.
  - Object-detection suggestions (auto-scan).
  - Gemini / OpenAI prompt-based scan (“Ask AI hazard scan”).
- **Alerting**:
  - Voice alerts via `say` (configurable voice).
  - Email notifications via Brevo (enable/disable, stored credentials).
  - Cooldown logic prevents spam.
- **Behavior analytics**:
  - Event-based tracking (position, speed, hazard distance).
  - Risk forecast cards (Low/Medium/High per kid).
  - Trend chart with kid filter, CSV-ready data via SQLite.

## Activity Dashboard Highlights

- **Summary table** – Events, average speed, last seen per kid.
- **Risk forecast** – Aggregated near-zone behavior to highlight active explorers.
- **Movement trends** – Altair chart of kid speed over time (filter per kid).

## Environment Variables / Config Files

- `.env`: `RTSP_URL`, `CAMERA_ID`, `ALERT_VOICE`, `OPENAI_API_KEY`, `GOOGLE_API_KEY`.
- `configs/camera.json`: current camera source.
- `configs/zones.json`: saved hazard polygons.
- `configs/alerts.json`: Brevo credentials (`enabled` flag).
- `configs/llm.json`: LLM provider + API keys/models.
- `database/smart_guardian.db`: local SQLite (ignored in Git).

## Roadmap

- Multi-channel alerts (SMS, push, MQTT).
- Autonomous semantic re-mapping of rooms.
- Weekly PDF/email reports.
- Containerized deployment + Raspberry Pi optimizations.


## 📸 Screenshots
*(Replace with your actual screenshots or demo video links)*  
![demo](https://via.placeholder.com/800x400?text=API+Demo+Screenshot)


## 📬 Request Access to Code
To access the private code repository for learning:  
👉 [Fill this form](https://docs.google.com/forms/d/e/1FAIpQLSdatf3kB36Tg9pElqB4yf2ZmVKVA89iWsyAMHTKnUkZ55mVWg/viewform?usp=dialog)  
📧 Please include your **GitHub username**.

Access is given **manually** for learning purposes only.  



## ⚖️ License & Usage
- Shared for **educational, non-commercial use only**.  
- Redistribution of this code or models is **not allowed**.  
- Please cite “YourName Labs” if you use parts of this code in research or teaching.  



## 💬 Questions?
- Open a **Discussion** in this repo.  
- Or email me at **jose.pariyani@gmail.com**.

---

> 🔗 Visit [varun Labs Portal](https://varun-labs.github.io/) for more projects and access links.



## License

MIT (or your choice)

---

Made with ❤️ to keep curious kids safer through transparent AI.
