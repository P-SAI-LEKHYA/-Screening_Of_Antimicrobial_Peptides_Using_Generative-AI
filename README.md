# 🧬 AMP Discovery — Generative AI Pipeline for De Novo Antimicrobial Peptide Design

A computational pipeline for **designing, screening, and structurally validating de novo antimicrobial peptides (AMPs)** using **Generative AI**, protein language models, and deep learning-based protein structure prediction. The project leverages modern AI techniques to accelerate antimicrobial peptide discovery and address the global challenge of **Antimicrobial Resistance (AMR)**.

> 📄 **Published at IEEE CSITSS 2025**  
> *Computational Design and Screening of De Novo Antimicrobial Peptides Using Generative AI*

---

## 📖 Table of Contents

- [Overview](#-overview)
- [Motivation](#-motivation)
- [Pipeline Workflow](#-pipeline-workflow)
- [Project Structure](#-project-structure)
- [Technology Stack](#-technology-stack)
- [Methodology](#-methodology)
- [Results](#-results)
- [Key Features](#-key-features)
- [Limitations](#-limitations)
- [Future Work](#-future-work)
- [Installation](#-installation)
- [Usage](#-usage)
- [Author](#-author)
- [Citation](#-citation)

---

# 📌 Overview

Antimicrobial Resistance (AMR) is expected to become one of the leading causes of mortality worldwide by 2050. Conventional antibiotic discovery is expensive, time-consuming, and limited by naturally occurring peptide diversity.

This project introduces an **AI-driven computational pipeline** capable of generating **entirely novel antimicrobial peptide sequences** using large protein language models and screening them through multiple computational validation stages including antimicrobial activity prediction, toxicity analysis, and protein structure prediction.

Unlike conventional approaches, the generated peptides **do not exist in nature**, enabling exploration of unexplored regions of peptide sequence space.

---

# 🎯 Motivation

The project aims to:

- Accelerate antimicrobial peptide discovery using Generative AI
- Explore novel peptide sequences beyond natural databases
- Reduce time and cost involved in early-stage drug discovery
- Identify promising AMP candidates entirely through computational methods
- Provide a scalable framework for future experimental validation

---

# 🔄 Pipeline Workflow

```text
                ┌─────────────────────────┐
                │ Generate Novel Peptides │
                │     (ProtGPT2)          │
                └──────────┬──────────────┘
                           │
                           ▼
             Physicochemical Property Filter
                           │
                           ▼
          AMP Activity Prediction (Consensus)
                           │
                           ▼
               Toxicity Screening
                           │
                           ▼
          3D Structure Prediction (ESMFold)
                           │
                           ▼
        Structural Visualization (PyMOL)
                           │
                           ▼
          Candidate Ranking & Selection
                           │
                           ▼
          Computational Validation Report
```

---



# 💻 Technology Stack

| Category | Tool / Model |
|-----------|--------------|
| Programming | Python |
| Development Environment | Google Colab |
| GPU | NVIDIA Tesla T4 |
| Sequence Generation | ProtGPT2 |
| Protein Language Model | ESM-2 |
| AMP Prediction | AMP Scanner v2 |
| AMP Database Validation | APD3 |
| Toxicity Prediction | ToxinPred |
| Structure Prediction | ESMFold |
| Visualization | PyMOL |
| Libraries | Hugging Face Transformers, OpenFold, PyTorch Lightning, BioPython, py3Dmol, einops |

---

# ⚙️ Methodology

## 1. Sequence Generation

- Generated **50 novel peptide sequences**
- Used **ProtGPT2**
- Top-k sampling
- Temperature = **1.0**

---

## 2. Physicochemical Filtering

Sequences were filtered based on:

- Length between **10–60 amino acids**
- Positive net charge ≥ +1
- Valid amino acid composition
- Removal of poor-quality sequences

---

## 3. Antimicrobial Activity Prediction

Each peptide was evaluated using:

- AMP Scanner v2
- APD3

Candidates were categorized as:

- 🟢 **Gold Candidate** – Positive prediction from both models
- 🟡 **Silver Candidate** – Positive prediction from one model

---

## 4. Toxicity Screening

Predicted mammalian toxicity using **ToxinPred**.

Only **non-toxic** candidates progressed to structural analysis.

---

## 5. Structure Prediction

Predicted 3D structures using **ESMFold**.

Evaluation metrics included:

- Mean pLDDT
- Predicted Aligned Error (PAE)
- Residue Contact Maps

---

## 6. Structural Visualization

Visualized candidate structures in **PyMOL** to inspect:

- Alpha-helical content
- Amphipathic regions
- Surface electrostatics
- Cationic membrane-binding properties

---

# 📊 Results

From **50 generated peptide sequences**, three candidates successfully passed all computational screening stages.

| Candidate | Net Charge | Toxicity Score | Mean pLDDT | Structural Features |
|------------|-----------:|---------------:|-----------:|---------------------|
| Candidate 21 | +26 | −1.28 | ~75 | Extended α-helical bundle with strong positive surface charge |
| Candidate 42 | +4 | −0.98 | ~85 | Compact α-helix with hydrophobic membrane-interacting regions |
| Candidate 44 | 0 | −0.23 | ~60–65 | Defensin-like cysteine-rich mixed helix/coil structure |

### Summary

✅ Generated 50 novel peptides

✅ Screened using dual AMP classifiers

✅ Removed toxic candidates

✅ Predicted high-confidence protein structures

✅ Identified **3 promising AMP candidates**

---

# ⭐ Key Features

- 🧬 AI-generated de novo antimicrobial peptides
- 🤖 Protein language model–based sequence generation
- 📈 Multi-stage computational screening
- 🛡️ Toxicity prediction before structural validation
- 🧠 Deep learning-based protein folding
- 🔍 Structural confidence analysis using pLDDT and PAE
- 🖥️ PyMOL visualization for membrane-targeting assessment
- 📑 Fully computational drug discovery workflow

---

# ⚠️ Limitations

- No experimental (wet-lab) validation
- AMP prediction models are trained on known peptides and may not fully generalize to novel sequence space
- ESMFold cannot explicitly model:
  - Disulfide bond formation
  - Membrane-induced conformational changes
- Biological activity remains computationally predicted

---

# 🚀 Future Work

- Molecular Dynamics (MD) simulations
- Peptide docking with bacterial membrane models
- Stability analysis under physiological conditions
- Experimental MIC assays
- In vitro antimicrobial validation
- In vivo efficacy testing

---

# 📦 Installation

Clone the repository:

```bash
git clone https://github.com/yourusername/AMP-Discovery.git

cd AMP-Discovery
```

Install dependencies:

```bash
pip install -r requirements.txt
```

---

# ▶️ Usage

Run the notebooks sequentially:

1. Sequence Generation
2. Physicochemical Filtering
3. AMP Prediction
4. Toxicity Screening
5. Structure Prediction
6. Visualization
7. Final Candidate Analysis

---

# 📈 Workflow Summary

```text
ProtGPT2
     │
     ▼
Generate Peptides
     │
     ▼
Physicochemical Filter
     │
     ▼
AMP Prediction
     │
     ▼
Toxicity Prediction
     │
     ▼
ESMFold Structure Prediction
     │
     ▼
PyMOL Visualization
     │
     ▼
Top Candidate Selection
```

---

# 👩‍💻 Author

**P Sai Lekhya**

B.Tech Computer Science & Engineering

R.V. College of Engineering, Bengaluru

📄 IEEE CSITSS 2025 Publication

Co-author: **Parinitha M**

Faculty Advisor: **Dr. Ajeet Kumar Srivastava**

---

# 📚 Citation

If you use this work in your research, please cite:

```bibtex
@inproceedings{lekhya2025amp,
  author={P Sai Lekhya and Parinitha M and Ajeet Kumar Srivastava},
  title={Computational Design and Screening of De Novo Antimicrobial Peptides Using Generative AI},
  booktitle={IEEE CSITSS},
  year={2025}
}
```

---

# 📜 License

This project is intended for academic and research purposes.

Please cite the associated publication if this repository contributes to your work.

---

⭐ **If you found this project useful, consider giving the repository a star!**
