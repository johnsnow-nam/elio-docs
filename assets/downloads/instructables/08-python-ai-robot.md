---
title: "Instructables 8편: Python AI Robot — OpenCV + ELIO"
lang: en
permalink: /assets/downloads/instructables/08/
---

# Python AI Robot — OpenCV Sees, ELIO Moves

**Platform**: Instructables  
**Status**: 🔲 Frame only (Wave 1) — full content in Wave 2  
**Target audience**: Python developers, AI/ML learners  
**Est. read time**: 15 minutes  
**Est. build time**: 2 hours

---

## Introduction (Outline)

> Connect a webcam to Python, use OpenCV for computer vision, and send commands to ELIO over UART. No cloud AI required — everything runs on your laptop.

**Key hook**: "Three lines of Python. One color. ELIO chases it."

**What we'll build**: A color-tracking robot — ELIO follows a colored object in the camera frame using OpenCV's HSV color detection.

---

## Supplies (Outline)

- ELIO board (Gen3 / ELIO-52810)
- USB-UART adapter (3.3V)
- PC with Python 3.8+
- Webcam (built-in or USB)
- `pip install elio-uart opencv-python numpy`

---

## Steps (Outline)

1. Install dependencies (`elio-uart`, `opencv-python`)
2. Wire UART adapter to ELIO (TX/RX/GND)
3. Test ELIO connection with basic `eliochannel` script
4. Capture webcam with OpenCV
5. Detect target color (HSV range)
6. Calculate centroid → determine turn direction
7. Send motor commands based on centroid position
8. Tuning: color thresholds, speed, dead zone

---

## Code Skeleton

```python
import cv2
import numpy as np
from elio_uart.comm.eliochannel import eliochannel

# Color tracking → ELIO motor control
# [Full implementation in Wave 2]
```

---

> **[Full content to be written in Wave 2]**

---

*Tutorial by ELIO / elioseokhee.github.io/elio-docs*
