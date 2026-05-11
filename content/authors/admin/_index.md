---
# Display name
title: Jay Polra

# Full name
first_name: Jay
last_name: Polra

# Status emoji (optional)
status:
  icon:

# Is this the primary user?
superuser: true

# Highlight the author in author lists?
highlight_name: true

# Role/position/tagline
role: Graduate Research Assistant

# Organizations/Affiliations to display in Biography blox
organizations:
  - name: CIVS, Purdue University Northwest
    url: https://civs.cs.pnw.edu/

# Social network links
profiles:
  - icon: at-symbol
    url: 'mailto:jpolraa@gmail.com'
    label: E-mail Me
  - icon: brands/linkedin
    url: https://www.linkedin.com/in/jaypolra/
  - icon: brands/github
    url: https://github.com/jaypolra
  - icon: globe-alt
    url: https://www.datascienceportfol.io/jpolraa

interests:
  - Computer Vision
  - Spatial Audio & Novel-View Synthesis
  - Vision-Language Models
  - Explainable AI
  - Industrial AI Safety
  - Multimodal Learning

education:
  - area: MSc Computer Science
    institution: Purdue University
    date_start: 2024-08-01
    date_end: 2026-05-31
  - area: BE Information Technology
    institution: LJ Institute of Engineering and Technology
    date_start: 2019-08-01
    date_end: 2023-05-31

work:
  - position: Graduate Research Assistant
    company_name: CIVS, Purdue University Northwest
    company_url: 'https://civs.cs.pnw.edu/'
    company_logo: ''
    date_start: 2025-01-01
    date_end: ''
    summary: |2-
      Researching computer vision, spatial audio, and vision-language models.

      - Geometry-grounded novel-view acoustic synthesis: feed-forward pipeline eliminating Structure-from-Motion dependency. Accepted at CVPR Workshop 2026.
      - Industrial AI safety: camera-based hazard monitoring with blind spot handling. Published at AISTech 2026 and TMS/AIM 2025.
      - VLM explainability: Grad-CAM token attribution and perturbation testing to verify causal influence of image regions on model outputs.

      Advised by Prof. Yang Ni and Prof. Chen Zhou.
  - position: Site Reliability Engineer
    company_name: Asite Solutions Pvt Ltd
    company_url: ''
    company_logo: ''
    date_start: 2023-01-01
    date_end: 2024-07-01
    summary: |
      Maintained 99% uptime SLA across 11 global production deployments (USA, UK, Canada, Australia, Hong Kong). 25+ services on Azure with strict regional isolation requirements.

      - Built Python monitor for JMS consumer queues catching silent failures before user impact. Adopted as standard team tooling.
      - Built zero-downtime restart automation: verified healthy instance availability before touching degraded one. Safety check first, action second.
      - Full Terraform infrastructure across 11 regions. Jenkins and Ansible CI/CD pipelines. Prometheus, Grafana, ELK, Azure Monitor observability stack.

awards:
  - title: Graduate Research Grant
    date: '2025-01-01'
    awarder: CIVS, Purdue University
    icon: hero/trophy
    summary: |
      Awarded for AI Hazard Recognition research.
  - title: 1st Runner-up, Research Poster Competition
    date: '2025-01-01'
    awarder: Purdue University
    icon: hero/trophy
    summary: |
      AI Hazard Recognition System.
  - title: Full Tuition Fee Waiver Scholarship
    date: '2023-01-01'
    awarder: LJ Institute of Engineering and Technology
    icon: hero/academic-cap
    summary: |
      Awarded for outstanding academic performance (2020-2023).
---

I work on AI systems where the model is only part of the problem.

That problem shows up across computer vision, spatial audio, and vision-language models. Different domains, same question: what does it take for this to actually work outside the lab?

My current research is at CIVS, Purdue University, advised by Prof. Yang Ni and Prof. Chen Zhou. Our work on geometry-grounded novel-view acoustic synthesis, building systems that render spatially accurate binaural audio without Structure-from-Motion or a target-view image, was accepted at the CVPR 2026 Workshop. Alongside that, I have been building real-time industrial safety systems for steel manufacturing environments, with published work at AISTech 2026 and TMS/AIM 2025.

The thread connecting all of it: I need to understand how something works before I build on top of it. That means opening the black box on vision-language models to verify whether their reasoning is causal or just correlated. It means designing safety systems that stay reliable when the camera cannot see the whole room. It means removing the geometric dependencies that make a method fragile in the environments it was actually built for.

Before research, I spent a year and a half as an SRE maintaining 99% uptime across 11 global production deployments. That experience shaped one instinct that carried directly into research: you do not assume a system is working because nothing has broken yet. You build the thing that tells you why it is working, and whether that will still be true under different conditions.

I am drawn to problems where the assumptions a method makes are themselves worth questioning, because that is usually where the next research question is hiding.
