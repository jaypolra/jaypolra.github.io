---
title: "AI Hazard Recognition System"
summary: "Real-time industrial safety monitoring with blind spot handling for steel melt shop environments."
tags:
  - Python
  - YOLO
  - DeepSORT
  - FastAPI
  - React
  - AISTech 2026
date: "2025-01-01"

links:
  - type: code
    url: https://github.com/jaypolra/ai-hazard-recognition
---

The core research problem: how does a detection-based safety system stay reliable when part of the physical environment is physically invisible to the camera?

Detection alone fails here. A vehicle that disappears into a blind spot does not mean the zone is safe. Built entry-exit state tracking as a conservative safety heuristic: assume worst case until exit is confirmed by a boundary camera.

Built blocker-aware zone isolation across 4 sequential camera feeds. Real-time pipeline runs YOLO detection and DeepSORT tracking at 8 FPS with under 50ms zone state updates. Full React dashboard for safety officer monitoring.
