# competition_data

This folder holds the competition datasets for the low-light image denoising challenge.

## Directory layout

```
competition_data/
├── public/
│   ├── ground_truth/
│   │   001.png
│   │   ...
│   │   460.png
│   ├── noisy/
│   │   001_noise.png
│   │   ...
│   │   460_noise.png
│   └── denoised/
└── submissions/
    ├── noisy/
    │   461_noise.png
    │   ...
    │   480_noise.png
    └── denoised/
        461.png
        ...
        480.png
```

## How to run the baseline

Save the dataset in the folders above (`public` and `submissions`), then:

### 1. Denoise the public images

```
python baseline\denoise.py --input_dir competition_data\public\noisy --output_dir competition_data\public\denoised
```

### 2. Evaluate the denoised output against ground truth

```
python evaluation\evaluate.py --noisy_dir competition_data\public\noisy --pred_dir competition_data\public\denoised --gt_dir competition_data\public\ground_truth
```

## Submission convention

- For images **461 to 480**, save your denoised images under:

```
submissions/denoised/
```

- For the **final submission**, only the `submissions/` directory is required.
