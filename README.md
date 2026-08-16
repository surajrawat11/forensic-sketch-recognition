# Forensic Sketch Synthesis & Recognition

A deep learning system for forensic investigation support — synthesizing photorealistic face images from hand-drawn sketches and retrieving ranked candidate matches from a facial gallery.

<p align="left">
  <img src="https://img.shields.io/badge/Python-3.10+-blue.svg" alt="Python">
  <img src="https://img.shields.io/badge/PyTorch-Deep%20Learning-orange.svg" alt="PyTorch">
  <img src="https://img.shields.io/badge/Status-In%20Development-yellow.svg" alt="Status">
</p>

## Overview

Eyewitness sketches remain a core tool in criminal investigation, but manually cross-referencing them against photo databases is slow and inconsistent. This project implements a two-stage pipeline that automates the process:

- **Synthesis** — a GAN-based model translates a sketch into a photorealistic facial image.
- **Retrieval** — deep face embeddings rank the closest candidate matches from a photo gallery.

The system is built as an investigative shortlisting tool: it narrows a large gallery to a small, ranked set of candidates for human review, rather than claiming definitive identification. Published research shows a wide accuracy gap between lab-controlled ("viewed") sketches and genuine eyewitness sketches — this project reports and interprets results with that distinction in mind.

## Pipeline

```
Sketch Input → GAN Synthesis → Face Embedding → Gallery Matching → Ranked Candidates
```

## Tech Stack

| Component | Technology |
|---|---|
| Core Language | Python 3.10+ |
| Deep Learning | PyTorch |
| Sketch Synthesis | Pix2Pix / CycleGAN |
| Face Recognition | FaceNet / ArcFace / dlib |
| Image Processing | OpenCV, Pillow |
| Demo Interface | Streamlit |
| Benchmark Dataset | CUFS / CUFSF |

## Repository Structure

```
forensic-sketch-recognition/
├── data/               Dataset and preprocessing (see data/README.md)
├── models/             Trained model checkpoints
├── notebooks/          Experiments and analysis
├── src/
│   ├── synthesis/      GAN training and inference
│   ├── recognition/    Face embedding and matching
│   ├── utils/          Shared preprocessing utilities
│   └── app.py          Streamlit demo application
├── results/            Evaluation outputs and figures
├── requirements.txt
└── README.md
```

## Setup

```bash
git clone https://github.com/surajrawat11/forensic-sketch-recognition.git
cd forensic-sketch-recognition

python -m venv venv
source venv/bin/activate      # Windows: venv\Scripts\activate

pip install -r requirements.txt
```

## Usage

```bash
streamlit run src/app.py
```

Upload a sketch to generate a synthesized photo and view the top-ranked matches from the gallery.

## Dataset

Trained and evaluated on **CUFS** and **CUFSF**, the standard academic benchmarks for sketch-photo pair research. Setup and preprocessing details are in `data/README.md`.

## Evaluation

Results are reported separately for viewed sketches (artist-drawn from a reference photo) and forensic/eyewitness-style sketches (drawn from memory), reflecting the significant performance gap documented in prior research. Full metrics and analysis are in `results/`.

## Author

**Suraj Singh Rawat**
B.Tech CSE (AI & ML) — MGM College of Engineering and Technology, Noida

[GitHub](https://github.com/surajrawat11) · [LinkedIn](https://linkedin.com/in/suraj-rawat-ai) · [X](https://x.com/suraj_rawat12)

## License

Developed for academic research as part of a B.Tech Mini Project.
