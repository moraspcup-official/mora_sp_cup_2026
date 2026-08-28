# Evaluation Scripts

This folder contains the evaluation script for the competition.

## Files

- `evaluate.py` — Computes the denoising score (PSNR, SSIM, and composite) for your images.

## Install

Install the dependencies required by `evaluate.py`:

```bash
pip install -r evaluation/requirements.txt
```

The required packages are `numpy`, `Pillow`, and `scikit-image`.

## Evaluate

`evaluate.py` computes your denoising score on any images you point it at.

Run it with three folders: noisy input, your denoised output, and ground truth:

```bash
python evaluation/evaluate.py \
    --noisy_dir competition_data/public/noisy \
    --pred_dir competition_data/public/denoised \
    --gt_dir competition_data/public/ground_truth
```

- `--noisy_dir`: folder of noisy input images.
- `--pred_dir`: folder of your denoised (`<id>.png`) images.
- `--gt_dir`: folder of ground-truth images.

### Filename convention

Your denoised output must follow the required convention — same id as the ground truth, no `_noise` suffix:

```text
ground_truth/001.png          <- ground truth
noisy/001_noise.png           <- noisy input (given to you)
denoised/001.png              <- YOUR reconstruction (same id, NO suffix)
```

### Output

Running the script prints the mean PSNR, SSIM, delta PSNR, delta SSIM, and the composite score.
