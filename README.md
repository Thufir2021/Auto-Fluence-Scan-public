# Auto-Fluence-Scan (AFS)

> Automated segmentation and laser fluence determination via Liu-Analysis.

🔬 **Status: Alpha** — early prototype currently in evaluation with academic early-access partners, ahead of a wider Beta and v1.0 release. See [Project Status & Roadmap](#project-status--roadmap).

AFS is an AI-assisted desktop application designed to fully automate the workflow of the Liu analysis (also known as the D² method). Traditionally, this process requires evaluating hundreds of images by manually defining one or many bar diameter for each laser-irradiated spot in order to determine the fluence threshold.

---

## 📖 Documentation

The full user handbook — installation, the step-by-step analysis workflow, additional features, settings, and the physics/math behind the Liu analysis (incubation model, aperture correction for non-Gaussian beams) — is published here:

👉 **[thufir2021.github.io/Auto-Fluence-Scan-public](https://thufir2021.github.io/Auto-Fluence-Scan-public/)** *(German)*

The same handbook ships with the app itself for offline use (**Help → Show Documentation**). This README stays a short overview — for anything operational, the handbook is the reference.

---

## Example Workflow

In this video, the laser fluence thresholds of two distinct physical processes are determined: crystallization, shown in bright light blue, and ablation, shown in dark blue. The data shown are provided with permission by Prof. Dr. Klaus Sokolowski-Tinten (University of Duisburg-Essen).


https://github.com/user-attachments/assets/ad991a11-d838-49e3-8d5f-1b5885fb301d

---

## Key Features

- **Robust contour detection** — reliable segmentation even in low-contrast, out-of-focus or noisy images (see examples)
- **Automated Liu-Analysis** — fully automated determination of any threshold and beam radius from irradiation spot data
- **Large-scale image processing** — C++/CUDA-accelerated backend for fast evaluation of large image datasets
- **AI-assisted segmentation** — Convolutional Attention U-Net model (Python) for robust, automated spot detection

---

## How It Works

```
Input: Microscopy images of laser-irradiated spots
         │
         ▼
  [CUDA-accelerated Pipeline]
  ├─ U-Net Segmentation      ← detects and segments ablation spots
  └─ Image Processing        ← extracts spot areas at varying pulse energies
         │
         ▼
  [Liu-Plot Evaluation]  ← fits r²_{0}(E) curve → fluence threshold & beam radius
         │
         ▼
Output: Overlay images (original images + contours), contour areas, fluence thresholds
```

---

## Technology

| Component | Technology |
|---|---|
| Spot Segmentation | Convolutional Attention U-Net (LibTorch, C++ inference) |
| Image Processing | C++ with CUDA support |
| Analysis Engine | Liu-method (Liu-Plot) |
| Interface | Windows Desktop Software |

---

## Use Cases

**Laser Material Processing & Manufacturing**

- Laser process characterization in R&D
- Quality control in laser micromachining and surface structuring
- Ablation threshold determination for new materials
- Process window optimization in laser drilling and cutting
- High-throughput fluence mapping for large sample sets
- Beam profile analysis and monitoring
- Thin film processing and layer-by-layer ablation characterization
- Laser cleaning and surface preparation validation

**Laser Modification & Precision Engineering**

- Refractive index modification in optical glasses and waveguide fabrication
- Laser-induced periodic surface structures (LIPSS) analysis
- Color marking and annealing on metals
- Laser shock peening process control

**Biomedical Optics**

- Fluence dosimetry in photodynamic therapy (PDT)
- Laser tissue ablation characterization for surgical parameter optimization
- Calibration of therapeutic laser systems

---

## Project Status & Roadmap

> This repository is public to show what AFS is. The source code is available to customers and partners under license agreement.

AFS is under active development and currently in its **Alpha stage**: a working, unlicensed prototype shared with a small group of academic early-access partners to gather honest, independent feedback before a wider release. A refined **Beta** for industry partners and the licensed **v1.0.0** launch follow in sequence:

| Stage | Audience | Purpose |
|---|---|---|
| 🔬 **Alpha** *(current)* | Academic early-access partners | Independent feedback on methodology & usability — free, no license terms attached |
| 🧪 **Beta** | Selected industry partners | Evaluation copy with purchase option, refined using Alpha feedback |
| 🚀 **v1.0.0** | Public / commercial launch | Full dual license (see below); in-app version display distinguishes Alpha / Beta / v1.0 |

Interested in early access for your lab? See [Contact](#contact).

**Feature roadmap:**

- [x] Add chessboard evaluation if irradiation was done in columns and rows.
- [ ] Include incubation effect for multi-pulse processing
- [ ] Expand analysis for photodynamic therapy (PDT)
- [ ] Extend Gaussian to more realistic beam profile: Airy Disk

---

## Licensing
 
AFS is available under a dual license model:
 
| | Academic License | Commercial License |
|---|---|---|
| **Target** | Universities, research institutes | Companies, industrial users |
| **Price** | 500 € / year | 2.000 € / year |
| **Usage** | Non-commercial research & teaching | All commercial applications |
 
> The source code remains proprietary. Redistribution, modification, or sublicensing is not permitted under either license.

## Data Contribution
The segmentation model in AFS was trained on real experimental image data from laser-irradiated materials. This data is kindly provided by academic research groups on a fully voluntary basis. Sharing data is entirely **optional** and has no effect on license terms or pricing. There is no obligation whatsoever.

Your data will never be redistributed, published, or shared with third parties. It is used exclusively for model training within this project. Before any data is accepted, a simple Data License Agreement is signed by both parties — this document specifies exactly what you are sharing, how it will be used, and that all rights remain with you except for the granted right to use the data for model training.

Every contributor is credited by name and institution in the Credits section of this repository.

---
## Credits

Data courtesy of Prof. Dr. Klaus Sokolowski-Tinten (University of Duisburg-Essen).
 
---
## Contact

Interested in AFS for your lab or production environment?

📧 **david.karapetjan@icloud.com**

---

*© 2026 David Karapetjan. All rights reserved.*
