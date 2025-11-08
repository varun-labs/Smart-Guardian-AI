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

## Setup

```bash
git clone https://github.com/YOUR-ORG/smart-guardian-mvp.git
cd smart-guardian-mvp
python3 -m venv .venv311 && source .venv311/bin/activate
pip install -r requirements.txt
cp .env.example .env   # set camera, Brevo, LLM API keys if desired
uvicorn app.main:app --reload
streamlit run ui/activation_app.py
```

- Access FastAPI at `http://localhost:8000` (`/video`, `/snapshot`, `/alerts`).
- Streamlit console at `http://localhost:8501`.

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

## Showcase Ideas

- GIF or short video highlighting:
  - Drawing zones / auto-scan.
  - Skeleton + name overlay.
  - Voice alert + email screenshot.
  - Activity dashboard with risk forecast.

## License

MIT (or your choice)

---

Made with ❤️ to keep curious kids safer through transparent AI.
