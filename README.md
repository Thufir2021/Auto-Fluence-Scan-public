# Auto-Fluence-Scan (AFS)

> AFS is an AI-assisted tool that automates the analysis process for determining laser-induced damage thresholds.

**Status: Alpha** — The first test version presented here (Alpha version) is primarily intended to gather critical feedback. Based on this feedback, a revised second test version (Beta version) will subsequently be provided. Once the Beta version has proven sufficiently reliable, the production-ready version v1.0.0 will be launched under a dual-licensing model.

Version v1.0.0 is intended to be capable of replacing the human-in-the-loop component. Furthermore, this version will make it possible to integrate the software directly into laser systems via a command-line interface and operate it autonomously without supervision.

To further improve the segmentation model, I would greatly appreciate it if you could share your raw data as well as the corresponding segmentations generated from it. A short data license agreement is attached to this letter for this purpose.

The Alpha version is a free test version with no obligation to purchase. After approximately four weeks, a revised Beta version will also be provided free of charge.

The installer is provided separately in a private GitHub repository. Documentation, Updates and release information will also be published there. To grant you access to the private repository, I will need your GitHub username.

AFS relies on the work of:
1) Liu, J.M. (1982) — "Simple technique for measurements of pulsed Gaussian‑beam spot sizes," Opt. Lett. 7(5), 196–198
2) Garcia‑Lechuga, M. & Grojo, D. (2021) — "Simple and robust method for determination of laser fluence thresholds for material modifications: an extension of Liu's approach to imperfect beams," Open Research Europe 1:7
3) Jee, Y., Becker, M.F. & Walser, R.M. (1988) — "Laser‑induced damage on single‑crystal metal surfaces", JOSA B 5(3), 648–659

---

## 📖 3-Step Workflow

1. **Load the image stack and corresponding energies**
2. **Segment the images**
3. **Correct the segmented areas if necessary**

Once the images have been segmented and the corresponding areas and energies have been entered into the table, the **Liu analysis is performed automatically**.


---

## Example Workflow

In this video, the laser fluence thresholds of two distinct physical processes are determined: crystallization, shown in bright light blue, and ablation, shown in dark blue. The data shown are provided with permission by Prof. Dr. Klaus Sokolowski-Tinten (University of Duisburg-Essen).


▶️ [Watch the example workflow video](assets/videos/example-workflow.mp4)

---

## Key Features

- **AI-assisted segmentation** — Convolutional Attention U-Net model (Python) for robust, automated spot detection even in low-contrast, out-of-focus or noisy images (see examples)
- **Automated Liu-Analysis** — Once image data and laser energies are provided
- **Large-scale image processing** — C++/CUDA-accelerated backend for fast evaluation of large image datasets


---




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
