A Two-Stage Learning Framework Combining Self-Supervised Feature Extraction and Adaptive Rebalancing for Melanoma-Sensitive Skin Lesion Classification
Repository: https://github.com/Rumas0/Thesis_work_SSL-imbalance
Overview
This repository contains the PyTorch implementation accompanying the paper 'A Two-Stage Learning Framework Combining Self-Supervised Feature Extraction and Adaptive Rebalancing for Melanoma-Sensitive Skin Lesion Classification'. The framework combines SimCLR self-supervised pretraining on 24,000 unlabeled ISIC images with adaptive rebalancing during supervised fine-tuning to improve melanoma detection on a small, highly imbalanced dataset.
Highlights
•	Two-stage training pipeline using SimCLR pretraining and adaptive rebalanced fine-tuning.
•	Lightweight CNN encoder (~0.5 million parameters).
•	Weighted focal loss, melanoma-specific augmentation, and 5× melanoma oversampling.
•	Reproducible experiments using fixed data splits and deterministic random seeds.
Method
Stage 1: SimCLR pretraining learns dermoscopy-specific visual representations from unlabeled ISIC images.
Stage 2: The pretrained encoder is fully fine-tuned using weighted focal loss, targeted melanoma augmentation, oversampling, and early stopping.
Experimental Setup
Stage	Images
SSL pretraining	24,000 unlabeled
Training	483
Validation	104
Test	104
Controlled Experiments
Configuration	SSL	Rebalancing
Baseline	No	No
SSL Only	Yes	No
Rebalance Only	No	Yes
SSL + Rebalance	Yes	Yes
Key Results
Model	Accuracy	Melanoma Recall
Baseline	73.1%	0.0%
Rebalance Only	64.4%	37.5%
SSL + Rebalance	64.1%	58.3%
The baseline achieves high overall accuracy while detecting no melanoma cases, whereas the complete framework consistently detects four to five of eight melanomas across three random seeds.
Training Details
SimCLR pretraining: NT-Xent loss, temperature 0.5, batch size 64, learning rate 3e-4, 20 epochs.
Fine-tuning: Adam optimizer, learning rate 1e-4, batch size 16, weighted focal loss, gradient clipping, and early stopping.
Hardware
Experiments were conducted using an NVIDIA Tesla T4 (16 GB) with PyTorch.
Limitations
•	Small labeled dataset and only eight melanoma test images.
•	Single public dataset evaluation.
•	Not intended for clinical deployment.
•	Provided for research reproducibility and educational purposes.
Citation
@article{samur2026sslmelanoma,
  title={A Two-Stage Learning Framework Combining Self-Supervised Feature Extraction and Adaptive Rebalancing for Melanoma-Sensitive Skin Lesion Classification},
  author={Tunib, Itti Samur and Bulbul, Mohammad Farhad},
  journal={Diagnostics},
  year={2026},
  note={Submitted}
}
Acknowledgments
The authors acknowledge the International Skin Imaging Collaboration (ISIC) for providing the dermoscopic image archive, Daffodil International University for academic support, and Mohammad Farhad Bulbul for supervision and guidance.
