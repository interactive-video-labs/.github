<h1 align="center">🎥 Interactive Video Labs</h1>

<p align="center">
  Modular, open-source SDKs and backend tools for building <strong>cue-driven, adaptive video experiences</strong>.
  <br />
  Turning static educational content into branching, interactive journeys across any web framework.
</p>

---

## ✨ What We Build

**Interactive Video Labs** provides a lightweight, state-machine-powered video engine and ecosystem that reacts to learner input in real time.

At defined timestamps or subtitle cues (for example, when an instructor says _“for example”_), the player pauses and renders a contextual interaction prompt—such as a quiz question, text input, or a path selector:
- 🟢 **Beginner**
- 🔵 **Intermediate**
- 🔴 **Advanced**

Based on the viewer's choice, the **Segment Manager** seamlessly switches to the matching video clip and resumes the main lesson timeline without leaving the player.

---

## 🧠 Core Capabilities

- **State-Machine Driven Playback (`IVLabsPlayer`)** – Orchestrates video states (`idle`, `playing`, `waitingForInteraction`), cue points, and transitions cleanly.
- **Flexible Cue Triggers** – Supports manual timestamp cue points as well as automatic subtitle-based cue generation.
- **Multiple Interaction Types** – Supports branching video segment switches (`choice-video-segment-change`), multiple-choice questions, and custom payloads.
- **Decision Tracking & Persistence** – Pluggable `DecisionAdapter` architecture (`InMemoryDecisionAdapter`, `LocalStorageDecisionAdapter`, or custom backend adapters) to record and retrieve learner choices.
- **Lifecycle & Analytics Hooks** – Emits structured events (`PLAYER_LOADED`, `VIDEO_STARTED`, `VIDEO_PAUSED`, `VIDEO_ENDED`, `CUE_TRIGGERED`, `INTERACTION_COMPLETED`, `ERROR`) for telemetry and progress tracking.
- **Built-in Localization** – Supports multi-language player UIs via configurable translation dictionaries.

---

## 💠 Architecture & Tech Stack

Our ecosystem is actively shipped and standardized around a modular, framework-agnostic architecture:

- **Core Engine:** Zero-dependency TypeScript (`ESM` + `CJS`) built with `tsup` and tested with `Vitest`.
- **Framework Wrappers:** Declarative, type-safe components for **React**, **Vue 3**, **Angular (15+)**, and **Svelte**.
- **Backend & Storage:** Python, **SQLAlchemy**, and **FastAPI** packages for cue persistence, lesson metadata, and playback APIs.
- **Tooling & CI:** `pnpm` workspaces, `Renovate`, `Commitlint`, and automated npm/PyPI release pipelines.

---

## 🧩 Repositories in This Organization

### Core Engine & Framework Wrappers
| Repository | Package | Description |
| :--- | :--- | :--- |
| [`interactive-video-core`](https://github.com/interactive-video-labs/interactive-video-core) | `@interactive-video-labs/core` | Framework-agnostic TypeScript engine (`IVLabsPlayer`), state machine, segment manager, and decision adapters. |
| [`interactive-video-react-wrapper`](https://github.com/interactive-video-labs/interactive-video-react-wrapper) | `@interactive-video-labs/react` | Lightweight, declarative React component wrapper with typed props and analytics callbacks. |
| [`interactive-video-vue-wrapper`](https://github.com/interactive-video-labs/interactive-video-vue-wrapper) | `@interactive-video-labs/vue` | Vue 3 component wrapper supporting props, events, and the Composition API. |
| [`interactive-video-angular-wrapper`](https://github.com/interactive-video-labs/interactive-video-angular-wrapper) | `@interactive-video-labs/angular` | Angular (15+) component wrapper using `@Input()` bindings and `@Output()` events. |
| [`interactive-video-svelte-wrapper`](https://github.com/interactive-video-labs/interactive-video-svelte-wrapper) | `@interactive-video-labs/svelte` | Reactive Svelte / SvelteKit component wrapper built on the core engine. |

### Platform, Demos & Documentation
| Repository | Description |
| :--- | :--- |
| [`lesson-uploader`](https://github.com/interactive-video-labs/lesson-uploader) | Admin interface for uploading base lessons, configuring cues, and attaching branching example clips. |
| [`example-lessons`](https://github.com/interactive-video-labs/example-lessons) | Public sample video assets and cue metadata configurations for demos and testing. |
| [`docs`](https://github.com/interactive-video-labs/docs) | Architecture guides, API references, and contributor documentation. |
| [`interactive-video-labs.github.io`](https://github.com/interactive-video-labs/interactive-video-labs.github.io) | Organization website and hosted sample media assets. |

---

## 📦 Published Packages

### 🟢 npm Registry
| Package | Role | Install |
| :--- | :--- | :--- |
| [`@interactive-video-labs/core`](https://www.npmjs.com/package/@interactive-video-labs/core) | Core TypeScript interactive video engine | `pnpm add @interactive-video-labs/core` |
| [`@interactive-video-labs/react`](https://www.npmjs.com/package/@interactive-video-labs/react) | React component wrapper | `pnpm add @interactive-video-labs/react @interactive-video-labs/core` |
| [`@interactive-video-labs/vue`](https://www.npmjs.com/package/@interactive-video-labs/vue) | Vue 3 component wrapper | `pnpm add @interactive-video-labs/vue @interactive-video-labs/core` |
| [`@interactive-video-labs/angular`](https://www.npmjs.com/package/@interactive-video-labs/angular) | Angular component wrapper | `pnpm add @interactive-video-labs/angular @interactive-video-labs/core` |
| [`@interactive-video-labs/svelte`](https://www.npmjs.com/package/@interactive-video-labs/svelte) | Svelte component wrapper | `pnpm add @interactive-video-labs/svelte @interactive-video-labs/core` |

### 🐍 PyPI Registry
| Package | Role | Install |
| :--- | :--- | :--- |
| [`interactive-video-labs-core`](https://pypi.org/project/interactive-video-labs-core/) | Python & SQLAlchemy storage layer for interactive video cues | `pip install interactive-video-labs-core` |
| [`interactive-video-labs-fastapi`](https://pypi.org/p/interactive-video-labs-fastapi) | FastAPI routes and backend integration for Interactive Video Labs | `pip install interactive-video-labs-fastapi` |

---

## 🚀 Quick Start (`@interactive-video-labs/core`)

```ts
import {
  IVLabsPlayer,
  LocalStorageDecisionAdapter,
} from '@interactive-video-labs/core';

const player = new IVLabsPlayer({
  containerId: 'player-container',
  videoUrl: 'https://interactive-video-labs.github.io/assets/main-lesson.mp4',
  decisionAdapter: new LocalStorageDecisionAdapter(),
  cues: [
    {
      id: 'example-cue',
      time: 10,
      label: 'Choose Example Depth',
      payload: {
        interaction: {
          type: 'choice-video-segment-change',
          title: 'Choose your path',
          description: 'Select an example matching your experience level.',
          question: 'Which walkthrough would you like to see?',
          options: [
            {
              level: 'Beginner',
              video: 'https://interactive-video-labs.github.io/assets/sample-interaction-1.mp4',
            },
            {
              level: 'Advanced',
              video: 'https://interactive-video-labs.github.io/assets/sample-interaction-2.mp4',
            },
          ],
        },
      },
    },
  ],
});

await player.init();
```

---

## 🌍 Use Cases

- **MOOCs & Online Course Platforms** – Adapt explanations dynamically to each learner's background.
- **Corporate Training** – Deliver role- or tier-specific walkthroughs inside a single base module.
- **K–12 & University E-Learning** – Embed checkpoint quizzes and remedial clips directly in lectures.
- **Product Onboarding** – Let users choose basic or advanced feature demos in real time.

---

## 🤝 Contributing & Sponsoring

Contributions, bug reports, and new interaction ideas are welcome across all repositories:
- **Frontend & SDKs:** TypeScript, React, Vue, Angular, Svelte, HTML5 Video UX
- **Backend & Speech Cues:** Python, FastAPI, SQLAlchemy, subtitle/speech cue extraction
- **Docs & Examples:** Sample lessons, interactive demos, and guides

Check each repository's `CONTRIBUTING.md` to get started, or support ongoing maintenance via [GitHub Sponsors](https://github.com/sponsors/interactive-video-labs).

---

## 📄 License

All projects in this organization are released under the **MIT License** unless stated otherwise.
