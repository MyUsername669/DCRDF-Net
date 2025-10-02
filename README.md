# DCRDF-Net
DCRDF-Net: A Dual-Channel Reverse-Distillation Fusion Network for 3D Industrial Anomaly Detection
This project is a collaborative development with Kawasaki Robotics. The source code will be released after the completion of the mutual non-disclosure agreement, and the implementation will be made publicly available soon.

Industrial surface defect detection is often constrained by the scarcity of labeled anomaly samples and the inconsistency in modality sensitivity: RGB images are easily disturbed by illumination and texture variations, while depth images struggle to capture purely appearance-based anomalies. In addition, fluctuations in lighting, material diversity, and viewpoint perturbations in real production scenarios introduce significant domain shifts and intra-class variance, making it challenging for a single modality or a single paradigm to achieve both robustness and generalization across appearance and geometry.

To address these challenges, we propose DCRDF-Net, a Dual-Channel Reverse-Distillation Fusion Network that jointly learns the normality manifolds of aligned RGB and 3D depth data, and performs detection and localization based on their deviations. The framework is composed of three collaborative designs:

Perlin-guided percentage perturbation and texture alignment – Synthetic anomalies are injected only within soft foreground regions, synchronously applied to both modalities with a shared random seed, while textures from the DTD dataset are introduced for statistical alignment, ensuring cross-modal consistency of pseudo anomalies and masks.

Guided Feature Refinement Network (GFRN) – Serving as the core of dual-channel reverse distillation, this network restores the teacher’s defect-free representations within each modality through constrained projection, distribution contraction, and non-local consistency regularization. It outputs multi-scale clean pyramids, which are then distilled into the student network with both knowledge distillation and pixel-wise supervision.

Cross-Modal Squeeze-Excitation Gated Fusion – By leveraging global channel priors and evidence discrepancy-driven spatial gating, the model learns pixel-wise weighting maps for adaptive modality arbitration and response synthesis within a unified confidence domain.

Extensive experiments on the MVTec 3D-AD dataset demonstrate the effectiveness of our method, achieving 97.1% I-AUROC and 98.8% PRO, outperforming existing baselines in both anomaly detection and localization.

<img width="865" height="334" alt="image" src="https://github.com/user-attachments/assets/f201f326-4cb4-4dea-aa91-643da69c1b43" />
