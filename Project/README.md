# Team Project — Topic Discussions

Working space and notes for the BIOENG 1340/2340 **final group project**. This page tracks the
project framework and the running record of team / topic discussions held in class.

## Project framework

- **Teams:** 1–3 people (working solo is allowed). Declare your team on the class roster sheet by
  setting your *in a team* column to **Y**, then fill in team members, a tentative topic, project
  type, and dataset on the *Final Group Project 2026* sheet.
- **Project type:** *analysis*, *software development*, or *both*.
  - *Analysis* — reconstruct/visualize medical images in 3D, extract objects, make measurements,
    collect and compare data (e.g. patients vs controls).
  - *Development* — implement or adapt an algorithm / open-source tool to process images.
- **Deliverable (Assignment 4):** a one-page **specific-aims** proposal (background → hypothesis →
  2–3 aims with subtasks) plus a process flowchart; later a poster and final presentation.
- **Project management:** 4-week performance period tracked on a **Kanban board**
  (kanbanflow.com) with To-Do → In-Progress → Testing → Complete swim lanes (agile workflow).

## Suggested workflow for every project

1. Find and **download** a sample dataset; confirm format (DICOM / NIfTI / VTK / video).
2. **Visualize** it (ParaView / ITK-SNAP) and confirm you can work with it.
3. Note the **image-formation method** (modality, systems model) — a teachable part of the project.
4. Characterize **baseline SNR / CNR**.
5. Develop an algorithm to **quantify a metric** that distinguishes groups or characterizes disease.

## Dataset sources

- Prior-year project sheets (2023–2025) — richest source of vetted datasets and ideas.
- Public repositories: Zenodo, OSF/OSIRIX, Google Dataset Search, the Human Connectome Project,
  Stanford (e.g. EchoNet echocardiography), and your own lab/research data.

## First discussion (Oct 13) — emerging topics

| Team | Topic | Data / notes |
|------|-------|--------------|
| Retinal vasculature | 3D multi-photon microscopy of whole eye-back vasculature; segment vessels and quantify **density**, **branching**, and **orientation** (glaucoma / IOP deformation). | Private lab 3D data; aim toward VTK/NIfTI → ParaView volume rendering + vessel enhancement (e.g. Frangi vesselness), targeting a conference abstract. |
| Echocardiography | Analyze cardiac **ultrasound** (echo) videos/images; segmentation or a cohort metric. | Stanford EchoNet (~10k echocardiograms); likely Python + ParaView/ITK-SNAP. |
| Segmentation (TBD) | Accessible imaging dataset; segmentation or image-formation characterization. | Dataset selection in progress. |

Project scope guidance: an **N-of-1/N-of-2** proof-of-concept (one or two cases, novel method) is
acceptable, as is a small **cohort** study (apply a validated method across hand-selected cases).
