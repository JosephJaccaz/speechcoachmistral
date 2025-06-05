Speech Coach IA – Local Mistral Version (English Summary)
==========================================================

Speech Coach IA is a coaching tool designed to help NGO field recruiters (fundraisers) improve their pitch delivery. This version is built to run fully offline using the Mistral 7B model, enabling privacy, speed, and full control.

Main Objectives
---------------
- Provide automatic feedback on pitch recordings.
- Customize analysis per NGO (e.g., Amnesty, MSF).
- Run offline with no Internet dependency.
- Fast response time on local machines (Mac M1/M2 or Linux servers).

Model Information
-----------------
- Model: Mistral-7B-Instruct-v0.2 (GGUF 4-bit quantized)
- Backend: llama-cpp-python
- Format: Q4_K_M
- Size: ~4 GB

## Project Structure

```
speech-coach-v3/
├── app/
│   ├── main.py                 ← main Streamlit interface
│   ├── feedback.py             ← GPT logic to generate feedback
│   ├── transcription.py        ← audio processing via Whisper
│   ├── ong_context.py          ← load context from NGO files
│   ├── utils.py                ← utilities: gauge, note parsing, etc.
│   ├── interface_texts.py      ← multilingual UI and email text definitions
│   ├── coach_notifier.py       ← coach email mapping & lookup
│   └── email_sender.py         ← generic email sending logic
│
├── prompts/
│   ├── prompt_fr.txt           ← Based on a perfect pitch as defined with coachs for FCH.
│   ├── prompt_de.txt           ← Based on a perfect pitch as defined with coachs for DCH.
│   └── prompt_it.txt           ← Based on a perfect pitch as defined with coachs for ICH.
│
├── data/
│   ├── coachs.json             ← NGO-language → coach email mapping
│   └── organisations/*.json    ← NGO information (slogan, redflags, model speech...)
│
├── streamlit_app.py            ← entry point to launch the app
├── requirements.txt
└── README.md                   ← this file
```

---

Key Features
------------
- Upload pitch audio file (.wav or .mp3)
- Transcribe with whisper.cpp or faster-whisper
- Analyze using Mistral LLM locally
- NGO/language-specific feedback barometer
- Automatic coach email notification
- Multilingual interface (FR, DE, IT)

Setup Instructions
------------------
1. Requirements: Python 3.10+, streamlit, llama-cpp-python
2. Install dependencies:

    pip install -r requirements.txt

3. Run LLM server:

    python mistral/generation.py

4. Launch app:

    streamlit run app/main.py

Security & Privacy
------------------
- No external server usage
- Audio and analysis handled fully offline
- GDPR-compliant setup

Email Notifications
-------------------
Create a `.env` file:

    EMAIL_USER=dialogai@gmail.com
    EMAIL_PASS=xxxxxxxxxxxx

The `email_utils.py` module routes pitch reports to coaches based on the NGO.

Upcoming Features
-----------------
- Push-to-talk recording
- Coach dashboard interface
- Pitch history viewer
- CSV/Excel export

Author
------
Developed by Joseph Jaccaz – Corris
