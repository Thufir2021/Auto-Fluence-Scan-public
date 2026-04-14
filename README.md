# Auto-Fluence-Scan (AFS)

> Automated laser fluence determination via Liu-method analysis — fast and accurate.

---

## What is AFS?

**Auto-Fluence-Scan** is a Windows desktop application for the automated determination of laser fluence on irradiated materials. It uses the **Liu method** (D²-method).

AFS is designed for research institutions, laser manufacturers, and industrial customers who work with laser material processing and require reproducible, high-throughput fluence measurements.

<video src="https://github.com/user-attachments/assets/e4d23b68-0b95-49eb-ae47-c7e2791331ac" controls></video>

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

- Laser process characterization in R&D
- Quality control in laser manufacturing
- Beam profile analysis and monitoring
- High-throughput fluence mapping for large sample sets

---

## Status

> This repository is public to show what AFS is. The source code is available to customers and partners under license agreement.

AFS is under active development. New features and performance improvements are released regularly.

- [x] Add chessboard view if irridiation was done in columns and rows.
- [ ] Update Liu-Analysis. Each pulse energy, represented as a row, has spots with now multiple spots and therefore more areas to evaluate; Take the mean value of the areas and append to one energy
- [ ] Update Liu-Plot accordingly; Multiple dots aligned vertically to one energy , instead of one dot per energy    
---

## Licensing
 
AFS is available under a dual license model:
 
| | Academic License | Commercial License |
|---|---|---|
| **Target** | Universities, research institutes | Companies, industrial users |
| **Price** | 500 € / year | 2.000 € / year |
| **Usage** | Non-commercial research & teaching | All commercial applications |
 
> The source code remains proprietary. Redistribution, modification, or sublicensing is not permitted under either license.

---
## Credits

Example data courtesy of **Prof. Klaus Sokolowski-Tinten**,  
University of Duisburg-Essen — used with permission.
 
---
## Contact

Interested in AFS for your lab or production environment?

📧 **david.karapetjan@icloud.com**

---

*© 2026 David Karapetjan. All rights reserved.*
