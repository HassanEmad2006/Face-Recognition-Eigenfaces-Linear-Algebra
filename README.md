# 👁️ Face Recognition Using Eigenfaces — A Linear Algebra Perspective

![Course](https://img.shields.io/badge/Course-Linear%20Algebra-555?style=flat&labelColor=555555&color=0366d6) ![Method](https://img.shields.io/badge/Method-PCA%20%2F%20Eigenfaces-555?style=flat&labelColor=555555&color=2ea44f) ![Type](https://img.shields.io/badge/Type-Math%20Derivation-555?style=flat&labelColor=555555&color=e8712d) ![Status](https://img.shields.io/badge/Status-Complete-555?style=flat&labelColor=555555&color=2ea44f)

A Linear Algebra course project deriving the Eigenface method for face recognition from first principles — covariance matrices, eigenvectors, and dimensionality reduction — and comparing it against LDA (Fisherfaces) and multilinear (Tensorface) approaches.

---

## TL;DR

Studied and mathematically derived the **Eigenface** approach to face recognition, which represents each face image as a point in a reduced-dimension "face space" built from the eigenvectors of the training set's covariance matrix. Covers the full derivation — mean face, covariance matrix, the AᵀA eigenvector trick for tractability, projection into face space, and Euclidean-distance-based classification — followed by a comparative analysis against Linear Discriminant Analysis (Fisherfaces) and multilinear (Tensorface) methods, and a discussion of PCA's practical limitations.

---

## Mathematical Formulation

Given a training set of *M* face images Γ₁, …, Γ_M (each an N×N image):

1. **Average face:** Ψ = (1/M) Σ Γₙ
2. **Difference vectors:** Φᵢ = Γᵢ − Ψ — isolates each face's deviation from the average.
3. **Covariance matrix:** C = (1/M) Σ ΦₙΦₙᵀ = AAᵀ, where A = [Φ₁ Φ₂ … Φ_M].
4. **Tractable eigenproblem:** directly eigendecomposing the N²×N² matrix C is intractable for realistic image sizes. Instead, the eigenvectors of the much smaller M×M matrix L = AᵀA are solved (AᵀAvᵢ = μᵢvᵢ), and the eigenvectors of C ("eigenfaces") are recovered as linear combinations: uₗ = Σ vₗₖΦₖ.
5. **Projection ("face space"):** a new face Γ_new is projected via ωₖ = uₖᵀ(Γ_new − Ψ), forming a weight vector Ω that describes its eigenface composition.
6. **Classification:** a face is assigned to class *k* that minimizes the Euclidean distance εₖ = ‖Ω − Ωₖ‖, subject to a threshold θ derived from the training set's maximum intra-class distance.

## Algorithm Implementation Considerations

- **Preprocessing:** all training images normalized to the same resolution, converted to grayscale, and aligned on key facial landmarks (eyes, mouth) so extracted features reflect facial structure rather than alignment artifacts.
- **Component selection:** not all eigenfaces are equally informative — eigenfaces are ranked by eigenvalue, and only the top *K* (typically capturing ~90–95% of variance) are retained, balancing dimensionality reduction against recognition accuracy.

## Comparative Analysis

- **PCA vs. LDA (Fisherfaces):** LDA improves on PCA by maximizing between-class separability rather than overall variance, giving better robustness to lighting and expression changes.
- **Multilinear Analysis (Tensorfaces):** standard PCA flattens each image into a 1D vector, discarding structural information. Representing faces as higher-order tensors allows identity, illumination, and pose to be modeled as separate factors, improving performance in unconstrained conditions.

## Limitations & Future Scope

- **Constrained environment:** requires controlled, frontal, uniformly lit conditions; degrades under rotation or extreme lighting changes.
- **Scale/position sensitivity:** requires precise preprocessing to center and scale each face.
- **Linear assumption:** PCA assumes faces lie on a linear subspace, which does not hold well under large pose/lighting variation.
- **Future directions:** non-linear extensions (Kernel PCA) and deep learning approaches (CNNs) that learn invariant feature hierarchies beyond what a linear subspace method can capture.

## 📁 Project Structure

```
Face-Recognition-Eigenfaces-Linear-Algebra/
│
├── README.md
└── Face_Recognition_Eigenfaces_Presentation.pdf   # Full presentation: derivation, implementation, comparative analysis, references
```

## Skills & Topics

Linear algebra · eigenvectors & eigenvalues · covariance matrices · principal component analysis (PCA) · dimensionality reduction · face recognition / biometrics · comparative method analysis (LDA, multilinear analysis) · technical presentation.

## References

M. I. D. Rieden, *Eigenfaces: A Brilliant Application of Linear Algebra* · Kumar & Nirvikar, *An Application of Linear Algebra for the Optimal Image Recognition*, IJERT, 2013 · Slavković & Jevtić, *Face Recognition Using Eigenface Approach*, Serbian Journal of Electrical Engineering, 2012 · Jalled, *Face Recognition Machine Vision System Using Eigenfaces*, arXiv:1705.02782, 2017 · Kline, *Eigenface for Face Detection*, Capstone Project, Georgia College, 2017 · Vasilescu & Terzopoulos, *Multilinear Image Analysis for Facial Recognition*, ICPR, 2002 · Li, Shen, Shen, Yang & Gao, *Face Recognition Using Linear Representation Ensembles*, Pattern Recognition, 2016.

---

## 👥 Attribution

Collaborative undergraduate team project — **Linear Algebra course, Zewail City of Science and Technology**.
This repository is an individually maintained portfolio record of the methodology and content, not a claim of sole authorship of the original team submission.

## 📄 License

No license — educational use only.
