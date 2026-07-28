## Szymon Dudek

Cybersecurity and edge AI. BSc Applied Computer Science, *cum laude* — Howest, Belgium.
Starting an MSc in Cyber Security & Resilience at St. Pölten, Austria, in September 2026.

**[holo911.github.io](https://holo911.github.io)**

---

### Object detection on a drone companion computer

Bachelor thesis, written during an internship at Advantech in Tokyo. One YOLOv8 model,
one board, two inference targets — same camera, same motor-control loop. Only the
silicon doing the inference changes.

| YOLOv8n on | FPS |
| --- | --- |
| Advantech ASR-D501 — Qualcomm QCS6490 Hexagon NPU (INT8) | **110.3** |
| Advantech ASR-D501 — ARM CPU | 1.3 |
| Raspberry Pi 5 — CPU | 1.1 |

Roughly **85× the throughput** of the same board's CPU, while drawing about 10% *less*
total board power — around 67× better inference performance per watt.

NPU throughput across eight variants (INT8, ASR-D501):

| Model | FPS | Model | FPS |
| --- | --- | --- | --- |
| YOLOv8n | 110.3 | YOLOv11n | 103.5 |
| YOLOv8s | 89.9 | YOLOv11s | 82.6 |
| YOLOv8m | 42.6 | YOLOv11m | 40.2 |
| YOLOv8l | 30.8 | | |
| YOLOv8x | 20.3 | | |

Deployment path: PyTorch → ONNX → INT8 TensorFlow Lite, then adapting the vendor's
Yocto-based GStreamer pipeline to run on Ubuntu, plus camera handling that differs per
sensor. Quantizing the model was the quick part.

The drone was built from scratch — frame, ESCs, Pixhawk, companion computer. YOLO
detects a target and sends yaw commands over MAVLink and ROS 2 so the aircraft turns to
follow it. Demonstrated live at **Japan IT Week, Tokyo Big Sight**.

→ Code: [`Holo911/Drone`](https://github.com/Holo911/Drone) ·
[Full thesis](https://drive.google.com/file/d/1ORBefG_7pYTAcOtzEbaA5s2RVjvB2m2V/view)

---

### Other work

- **Penetration testing** — full audits for two real clients: a secondary school with
  1000+ networked devices, and a pharmacy. Findings scored with CVSS and reported to
  both IT departments with management summaries.
- **Honeypot & CTF platform** — deliberately exposed admin panel with Grafana
  monitoring, plus three CTF challenges. Survived a live attack exercise by classmates
  without a breach; most attempts were logged and visualised.
- **BIOS flash utility (C)** — bounds-checked, filename allowlist, and POSIX
  `fork()`/`execvp()` instead of a shell, removing the command-injection surface.
- **ROS 2 behaviour tree** — stop-and-wait navigation for a ROSMASTER X3, so the robot
  halts and waits for people to pass rather than replanning into furniture.

---

### Credentials

- BSc Applied Computer Science, *cum laude* — Howest University of Applied Sciences, June 2026
- Cisco CyberOps Associate — July 2026
- Cambridge C1 Advanced (CAE)
- 3rd place — HELMo Industry 5.0 Hackathon, Liège

Polish (native) · English (C1) · German (basic) · Japanese (beginner)

---

szymond200555@gmail.com · [LinkedIn](https://www.linkedin.com/in/szymon-dudek-968469355/)
