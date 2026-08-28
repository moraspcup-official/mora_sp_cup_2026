# Welcome to the Low-Light Image Denoising & Enhancement Challenge

**Mora SP Cup 2026**

## About the Challenge

Low-light photography is hard: when a camera sensor operates in the dark, it introduces heavy speckle, grain, and distortion into every image. In this competition, you will build an algorithm that removes these artifacts and restores noisy, low-light photos to their original, crisp quality.

Participants receive a custom dataset captured with an imperfect sensor under low-light conditions. Your task is to design an effective denoising solution. Whether you are new to image processing or testing novel approaches, this is a hands-on opportunity to solve a real digital imaging problem.

## The Task

- Denoise a collection of noisy images.
- The dataset contains noise at different severity levels.
- All images have a resolution of 992 × 992 pixels.
- The full dataset comprises 500 noisy images and 500 ground-truth images, split as follows:
  - **Public set:** 460 noisy images (`001_noise.png`–`460_noise.png`) with their ground-truth images (`001.png`–`460.png`). Use these to develop and validate your approach.
  - **Submission set:** 20 noisy images (`461_noise.png`–`480_noise.png`) with **no** ground truth provided. You must denoise these and include the 20 denoised images in your final submission.
  - **Hidden set:** 20 image pairs (`481.png`–`500.png`) retained by the evaluators and used only for official scoring.
- The provided noisy images must **not** be renamed.

## Project Layout

Place the images in the correct directories before running the baseline:

```
competition_data/
|-- public/
|   |-- ground_truth/
|   |   001.png
|   |   ...
|   |   460.png
|   |-- noisy/
|       001_noise.png
|       ...
|       460_noise.png
|-- submissions/
    |-- noisy/
    |   461_noise.png
    |   ...
    |   480_noise.png
    |-- denoised/
```

Your denoised outputs for images 461–480 should be saved under `submissions/denoised/`.

## Getting Started

- A classical baseline is provided in `baseline/`. You may build on it or develop your own architecture.
- Scoring uses the metrics implemented in `evaluation/evaluate.py`.
- Place all custom scripts in `scripts/`. You are **not allowed** to modify files in any other directory.
- Use Python. External Python libraries are permitted.

## Scoring

The evaluation score is computed as:

```
Evaluation Score = 0.6 × ΔPSNR_norm + 0.4 × ΔSSIM_norm
```

Full details are provided in the official competition document.
