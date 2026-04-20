# Auto-Fluence-Scan (AFS)

> Automated segmentation and laser fluence determination via Liu method analysis — fast and accurate.

---

## What is AFS?

**Auto-Fluence-Scan** is a Windows desktop application for the automated analysis of laser-irradiated material images. It uses AI-based segmentation to automatically process hundreds of images, reliably identifying ablation zones before determining the laser fluence via the Liu method (D²-method).

AFS is designed for research institutions, laser manufacturers, and industrial customers who work with laser material processing and require reproducible, high-throughput fluence measurements.



https://github.com/user-attachments/assets/ad991a11-d838-49e3-8d5f-1b5885fb301d




---

## Key Features

- **Automated Liu-Analysis** — fully automated determination of any threshold and beam radius from irradiation spot data
- **Large-scale image processing** — C++/CUDA-accelerated backend for fast evaluation of large image datasets
- **AI-assisted segmentation** — Convolutional Attention U-Net model (Python) for robust, automated spot detection
- **Scalable** — from single measurements to batch processing of thousands of images

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
  [Liu-Plot Evaluation]  ← fits D²(E) curve → fluence threshold & beam radius
         │
         ▼
Output: Fluence map, threshold values, beam profile report
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

## Status

> This repository is public to show what AFS is. The source code is available to customers and partners under license agreement.

AFS is under active development. New features and performance improvements are released regularly.

- [x] Add chessboard evaluation if irridiation was done in columns and rows.
- [ ] Include Incubation effect for multi-pulse processing
- [ ] Expand analysis for photodynamic therapy (PDT)  
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

The image data shown in the Workflow video are from **Prof. Klaus Sokolowski-Tinten**,  
University of Duisburg-Essen — used with permission.
 
---
## Contact

Interested in AFS for your lab or production environment?

📧 **david.karapetjan@icloud.com**

---

*© 2026 David Karapetjan. All rights reserved.*
