<h1 align="center">🎥 Interactive Video Labs</h1>

<p align="center">
  Open-source tools for creating <strong>adaptive, personalized video learning experiences</strong>.
  <br />
  Turning static educational content into dynamic journeys — one viewer at a time.
</p>

---

## ✨ What We’re Building

**Interactive Video Player** – an intelligent player that reacts to learner input in real-time.

When the instructor says something like _“for example,”_ a modal appears asking the viewer to select their experience level:
- 🟢 Beginner
- 🔵 Intermediate
- 🔴 Advanced

Based on the selection, the player inserts a relevant example video and then resumes the main lesson — all without switching screens.

---
## 🧠 Key Features

- **Cue-Triggered Modals** – Detects predefined timestamps (or phrases like “for example”) to prompt interaction.
- **Level-Based Examples** – Users choose their experience level, triggering relevant video clips.
- **Seamless Playback** – Example video is inserted and automatically returns to the main timeline.
- **Analytics Logging** – Records user decisions for personalization and progress tracking.

---

## 💠 Tech Stack

*Not finalized yet.*  
We are currently evaluating the best tools and frameworks for:

- Frontend video interaction and overlays
- Backend API for metadata and playback logic
- Cue detection using speech-to-text or manual timestamps
- Seamless video switching and playback control

💡 Suggestions and contributions are welcome!

---

## 🧩 Projects Under Development

| Repository                                                                 | Description                                                |
|---------------------------------------------------------------------------|------------------------------------------------------------|
| [`interactive-video-player`](https://github.com/interactive-video-labs/interactive-video-player) | Core player with cue modals and dynamic playback           |
| [`cue-detection-module`](https://github.com/interactive-video-labs/cue-detection-module)       | Detects cue moments using audio/speech input               |
| [`lesson-uploader`](https://github.com/interactive-video-labs/lesson-uploader)                 | Admin tool for uploading lessons + example clips           |
| [`example-lessons`](https://github.com/interactive-video-labs/example-lessons)                 | Public metadata + video samples for demo/testing           |
| [`docs`](https://github.com/interactive-video-labs/docs)                                       | Architecture, contribution guides, and developer notes     |

---

## 📦 Published Packages & Ecosystems

### 🟢 NPM Registry
| Package | Ecosystem / Role | Link |
| :--- | :--- | :--- |
| **`@interactive-video-labs/core`** | Framework-agnostic TypeScript interactive video engine | [npm](https://www.npmjs.com/package/@interactive-video-labs/core) |
| **`@interactive-video-labs/react`** | React component & hook wrapper | [npm](https://www.npmjs.com/package/@interactive-video-labs/react) |
| **`@interactive-video-labs/vue`** | Vue 3 component wrapper | [npm](https://www.npmjs.com/package/@interactive-video-labs/vue) |
| **`@interactive-video-labs/angular`** | Angular component wrapper | [npm](https://www.npmjs.com/package/@interactive-video-labs/angular) |
| **`@interactive-video-labs/svelte`** | Svelte component wrapper | [npm](https://www.npmjs.com/package/@interactive-video-labs/svelte) |

### 🐍 PyPI Registry
| Package | Ecosystem / Role | Link |
| :--- | :--- | :--- |
| **`interactive-video-backend-core`** | Python & SQLAlchemy storage layer for interactive video cues | [PyPI](https://pypi.org/project/interactive-video-labs-core/) |
| **`interactive-video-labs-fastapi`** | FastAPI backend package for Interactive Video Labs | [PyPI](https://pypi.org/p/interactive-video-labs-fastapi) |

---

## 🌍 Use Cases

- **MOOCs** and online course platforms  
- **Corporate training** with tiered content  
- **K–12 and university-level e-learning**  
- **Product education** with contextual walkthroughs  

---

## 🤝 Join Us

We’re looking for collaborators interested in:
- Web video UX and interaction
- React / Vue / FastAPI / Python / TypeScript
- Whisper, Vosk, or speech cue detection
- Instructional design and pedagogy

Feel free to contribute, give feedback, or share your use case ideas.  
Let’s build a better learning experience — together.

---

## 📄 License

All projects in this org are under the **MIT License** unless stated otherwise.
