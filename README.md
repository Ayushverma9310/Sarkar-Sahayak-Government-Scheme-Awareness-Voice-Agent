# 🇮🇳 Sarkar Sahayak — Government Scheme Awareness Voice Agent

A real-time **Hindi voice agent** that helps Indian citizens discover and understand government welfare schemes — built using **Sarvam AI**, **Groq LLaMA 3.3**, and **LiveKit**.

---



## 🎯 What It Does

Citizens can **speak in Hindi** (or any Indian language) and ask questions like:
- *"PM Kisan yojana ke liye kaise apply karein?"*
- *"Ayushman Bharat card kaise banwayein?"*
- *"Mere liye kaunsi sarkari scheme hai?"*

The agent **listens → understands → responds in Hindi voice** in real time.

---

## 🏗️ Architecture

```
User Voice Input
      ↓
Sarvam Saaras v3 (STT) — Speech to Text (Hindi/Multilingual)
      ↓
Groq LLaMA 3.3 70B (LLM) — Understands & generates response
      ↓
Sarvam Bulbul v3 (TTS) — Text to Hindi Speech
      ↓
User hears the answer in Hindi voice
```

**Real-time pipeline powered by LiveKit WebRTC**

---

## 🛠️ Tech Stack

| Component | Technology |
|-----------|-----------|
| 🎙️ Speech to Text | Sarvam AI — Saaras v3 |
| 🧠 Language Model | Groq — LLaMA 3.3 70B Versatile |
| 🔊 Text to Speech | Sarvam AI — Bulbul v3 (Simran voice) |
| 🌐 Real-time Comms | LiveKit WebRTC |
| 🎛️ Voice Detection | Silero VAD |
| 🖥️ UI | Streamlit |
| 🐍 Language | Python 3.9+ |

---

## 🚀 Quick Start

### 1. Clone the repo
```bash
git clone https://github.com/yourusername/sarkar-sahayak.git
cd sarkar-sahayak
```

### 2. Create virtual environment
```bash
python -m venv .venv

# Windows
.venv\Scripts\activate

# Mac/Linux
source .venv/bin/activate
```

### 3. Install dependencies
```bash
pip install -r requirements.txt
```

### 4. Setup API Keys

Create a `.env` file in the root folder:
```env
LIVEKIT_URL=wss://your-project-xxxxx.livekit.cloud
LIVEKIT_API_KEY=APIxxxxxxxxxxxxx
LIVEKIT_API_SECRET=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
SARVAM_API_KEY=sk_xxxxxxxxxxxxxxxxxxxxxxxx
GROQ_API_KEY=gsk_xxxxxxxxxxxxxxxxxxxxxxxx
```

Get your API keys from:
- 🔗 [LiveKit Cloud](https://cloud.livekit.io/) — Free account
- 🔗 [Sarvam AI Dashboard](https://dashboard.sarvam.ai/) — Indian language STT/TTS
- 🔗 [Groq Console](https://console.groq.com/) — Free LLaMA API

### 5. Run the Voice Agent
```bash
python scheme_awareness_agent.py dev
```

### 6. Run the Streamlit UI (optional)
```bash
# New terminal
streamlit run app.py
```

### 7. Test Voice in Browser
Open [agents-playground.livekit.io](https://agents-playground.livekit.io) → Enter your LiveKit credentials → Connect → Speak!

---

## 📁 Project Structure

```
sarkar-sahayak/
│
├── scheme_awareness_agent.py   # Main voice agent (LiveKit + Sarvam + Groq)
├── app.py                      # Streamlit UI (Text + Voice interface)
├── requirements.txt            # Python dependencies
├── .env                        # API keys (do not commit!)
├── .env.example                # Template for .env
└── README.md
```

---

## 🧠 Government Schemes Covered

| Scheme | Benefit |
|--------|---------|
| PM Kisan Samman Nidhi | ₹6,000/year for farmers |
| Ayushman Bharat | ₹5 lakh health insurance |
| PM Awas Yojana | Free/subsidized housing |
| Sukanya Samriddhi Yojana | Savings scheme for girl child |
| PM Ujjwala Yojana | Free LPG connection for BPL |
| MGNREGA | 100 days employment guarantee |
| PM Jan Dhan Yojana | Zero balance bank account |
| PM Mudra Yojana | Business loans up to ₹10 lakh |
| Atal Pension Yojana | Monthly pension scheme |
| Skill India Mission | Free skill development training |

---

## ⚙️ How The Code Works

### `scheme_awareness_agent.py`

```python
# 1. STT — Sarvam Saaras converts Hindi speech to text
stt=sarvam.STT(language="hi-IN", model="saaras:v3", mode="transcribe")

# 2. LLM — Groq LLaMA processes the text and generates a response
llm=groq.LLM(model="llama-3.3-70b-versatile")

# 3. TTS — Sarvam Bulbul converts response text back to Hindi speech
tts=sarvam.TTS(target_language_code="hi-IN", model="bulbul:v3", speaker="simran")

# 4. VAD — Silero detects when user starts/stops speaking
vad=silero.VAD.load()
```

### `app.py`
- Streamlit web UI for text-based chat
- Language selector (9 Indian languages)
- Scheme cards with one-click questions
- Powered by same Groq LLaMA backend

---

## 📦 Requirements

```
livekit-agents>=1.0.0
livekit-plugins-sarvam>=1.0.0
livekit-plugins-groq>=1.0.0
livekit-plugins-silero>=1.0.0
python-dotenv>=1.0.0
groq>=0.9.0
streamlit>=1.30.0
```

---

## 🌐 Supported Languages (STT)

`hi-IN` Hindi | `en-IN` English | `ta-IN` Tamil | `te-IN` Telugu | `bn-IN` Bengali | `gu-IN` Gujarati | `kn-IN` Kannada | `mr-IN` Marathi | `pa-IN` Punjabi

---

## 🤝 Contributing

Pull requests welcome! If you want to add more schemes, languages, or features — feel free to fork and contribute.

---

## 📄 License

MIT License — Free to use and modify.

---

## 🙏 Acknowledgements

- [Sarvam AI](https://sarvam.ai) — For Indian language STT/TTS
- [Groq](https://groq.com) — For ultra-fast LLaMA inference
- [LiveKit](https://livekit.io) — For real-time voice infrastructure
- [LiveKit Agents Framework](https://docs.livekit.io/agents/) — For the agent pipeline

---

*Built with ❤️ for Digital India*
