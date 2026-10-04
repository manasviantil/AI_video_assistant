# 🎬 AI Video Assistant

**Turn any video into a transcript, a summary, and a conversation.**

Paste a video URL or upload a file. The assistant downloads the audio, transcribes it with Whisper, summarises it with Mistral AI, and lets you ask questions about the content through a RAG pipeline.

![Python](https://img.shields.io/badge/Python-3.10%2B-3776AB?logo=python&logoColor=white)
![Whisper](https://img.shields.io/badge/Whisper-Speech--to--Text-412991?logo=openai&logoColor=white)
![Mistral AI](https://img.shields.io/badge/Mistral%20AI-LLM-FF7000)
![yt-dlp](https://img.shields.io/badge/yt--dlp-Downloader-red)
![License](https://img.shields.io/badge/License-MIT-green)
---

## 📌 Overview

Long videos are time-consuming to watch and hard to search. **AI Video Assistant** solves this by converting video content into text and making it queryable.

Give it a video link (or a local file) and it will:

1. Download and process the audio
2. Transcribe the speech to text
3. Extract and summarise the key points
4. Answer your questions about the video using Retrieval-Augmented Generation (RAG)

## ✨ Features

- 🔗 **URL input**: works with video links via `yt-dlp`, plus local audio/video files
- 🎧 **Audio processing**: automatic conversion to 16 kHz mono WAV, with chunking for long videos
- 📝 **Local transcription**: runs OpenAI Whisper on your own machine, with no transcription API costs
- 🧠 **Summarisation**: concise summaries and key-point extraction powered by Mistral AI
- 💬 **RAG-based Q&A**: ask questions and get answers grounded in the video's transcript
- ⚙️ **Zero manual FFmpeg setup**: uses `static-ffmpeg` to install FFmpeg automatically

## 🏗️ How It Works

```
 Video URL / Local file
          │
          ▼
  ┌───────────────────┐
  │  Audio Processor  │  yt-dlp + pydub + FFmpeg
  │  download → WAV   │  (16 kHz mono, 10-min chunks)
  └─────────┬─────────┘
            ▼
  ┌───────────────────┐
  │   Transcription   │  Whisper (local)
  └─────────┬─────────┘
            ▼
  ┌───────────────────┐
  │ Extract & Summarise│  Mistral AI
  └─────────┬─────────┘
            ▼
  ┌───────────────────┐
  │    RAG Q&A        │  Ask questions about the video
  └───────────────────┘
```

## 🛠️ Tech Stack

| Area | Tools |
|------|-------|
| Language | Python |
| Video/Audio download | `yt-dlp` |
| Audio processing | `pydub`, `static-ffmpeg` |
| Speech-to-text | OpenAI Whisper (local) |
| LLM | Mistral AI |
| Retrieval | RAG pipeline |

## 📁 Project Structure

```
video_assistant/
├── app.py                  # Main application entry point
├── utils/
│   └── audio_processor.py  # Download, convert, and chunk audio
├── requirements.txt
└── README.md
```

> Update this tree to match your final folder layout.

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/manasviantil/AI_video_assistant.git
cd AI_video_assistant
```

### 2. Create a virtual environment

```bash
python -m venv .venv

# Windows
.venv\Scripts\activate

# macOS / Linux
source .venv/bin/activate
```

### 3. Install dependencies

```bash
python -m pip install -r requirements.txt
```

If you don't have a `requirements.txt` yet, the core packages are:

```bash
python -m pip install static-ffmpeg yt-dlp pydub openai-whisper mistralai
```

> **FFmpeg:** no manual install needed. `static-ffmpeg` downloads it automatically on the first run (internet required once).

### 4. Add your API key

Create a `.env` file in the project root:

```env
MISTRAL_API_KEY=your_api_key_here
```

> ⚠️ Never commit your `.env` file. Make sure it is listed in `.gitignore`.

### 5. Run the app

```bash
python app.py
```

If your app uses Streamlit, run `streamlit run app.py` instead.

## 💡 Usage

1. Paste a video URL (or provide a local file path).
2. Wait while the audio is downloaded, chunked, and transcribed.
3. Read the generated summary and key points.
4. Ask follow-up questions about the video.

## 🧩 Troubleshooting

| Problem | Fix |
|---------|-----|
| `ffprobe and ffmpeg not found` | Make sure `static_ffmpeg.add_paths()` runs before `yt-dlp`, `pydub`, or `whisper` are used |
| `No module named pip` in venv | Run `python -m ensurepip --upgrade` or recreate the venv |
| VS Code yellow squiggle on imports | Select the `.venv` interpreter via `Ctrl+Shift+P` → **Python: Select Interpreter** |
| Slow first run | FFmpeg and the Whisper model are downloaded once, then cached |

## 🗺️ Roadmap

- [ ] Timestamped transcript with clickable references
- [ ] Support for multiple videos in one knowledge base
- [ ] Export summaries to PDF / Markdown
- [ ] Multi-language transcription and translation

## 🤝 Contributing

Contributions, issues, and feature requests are welcome. Feel free to open an issue or submit a pull request.

## 👩‍💻 Author

**Manasvi**
B.Tech CSE (AI/ML), Maharaja Agrasen University

[![GitHub](https://img.shields.io/badge/GitHub-manasviantil-181717?logo=github)](https://github.com/manasviantil)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-manasviantil-0A66C2?logo=linkedin&logoColor=white)](https://linkedin.com/in/manasviantil)

---



⭐ If you found this project useful, consider giving it a star!

</div>
