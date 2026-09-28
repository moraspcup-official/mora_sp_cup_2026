# MORA SP Cup 2026 — Final Round Participant Instructions

This document explains what finalist teams must do on the physical final day of **Mora SP Cup 2026**.

Please read the complete document before arriving at the venue and make sure your team is prepared to reproduce the submitted solution using the exact code and model/checkpoint that were frozen at the preliminary-round submission deadline.

---

## 1. Final Round Venue and Reporting Time

- **Date:** Sunday, 4 October 2026
- **Reporting / Onboarding Time:** 8:30 a.m.
- **Venue:** ENTC1 Hall, Department of Electronic and Telecommunication Engineering, University of Moratuwa

Teams should arrive on time and be ready for code/model verification, final inference, presentation, and the technical Q&A/viva.

---

## 2. What You Must Bring

Each team should be prepared with:

- Access to the private GitHub repository submitted for the preliminary round
- Access to the GitHub account required to clone the private repository
- Access to the submitted Google Drive model/checkpoint link, if an external model file was used
- The required Python environment / package information
- Any software required to run the submitted solution locally
- A laptop capable of running the submitted solution
- The final presentation

The final solution must be reproducible using the exact submitted code and, where applicable, the exact submitted model/checkpoint.

---

## 3. Important Submission Freeze Rule

The preliminary-round submission is frozen.

### Code

The **Git commit SHA submitted before the preliminary-round deadline** identifies the official code version.

No new code version may be substituted for the official submission during the final round.

### Model / Checkpoint

If the team submitted an external trained model/checkpoint, the **SHA-256 checksum recorded for that file** identifies the official model file.

The submitted model/checkpoint must not be replaced by another model.

---

## 4. Create a Fresh Final-Day Working Folder

At the start of the verification process, create a new empty folder on your laptop.

Do **not** use an old local copy of your project for verification.

The repository must be freshly cloned in front of the assigned OC member.

Example:

```powershell
git clone <YOUR_PRIVATE_REPOSITORY_URL>
```

Enter the cloned repository:

```powershell
cd <REPOSITORY_FOLDER>
```

---

## 5. Show the Current Git Commit SHA

Inside the freshly cloned repository, run:

```powershell
git rev-parse HEAD
```

This prints the full Git commit SHA of the code currently checked out.

Example:

```text
8c52df2e1c7f98a0bd4dcae5711e926673d11f54
```

Show this value to the assigned OC member.

The OC member will compare it with the Git commit SHA recorded for your preliminary-round submission.

### Required Result

```text
Current Git SHA = Recorded Submission Git SHA
```

The two values must match.

Do not change commits, reset the repository, or checkout another version unless specifically instructed by the responsible competition organizers.

---

## 6. Show That the Fresh Clone Is Unmodified

Immediately after cloning, and before copying any external model files into the project folder, run:

```powershell
git status --porcelain
```

### Expected Result

No output.

This indicates that there are no local modifications to the freshly cloned tracked files.

You may also run:

```powershell
git status
```

for a more readable view.

The assigned OC member may ask to see either command.

---

## 7. Optional Commit Information

You may also show the latest commit using:

```powershell
git log -1 --oneline
```

Example:

```text
8c52df2 Final preliminary submission
```

The full value produced by:

```powershell
git rev-parse HEAD
```

is the value used for official verification.

---

## 8. Model / Checkpoint Verification

If your solution does **not** use an external model/checkpoint, this step is not applicable.

If your solution uses a trained model/checkpoint stored separately in Google Drive:

1. Download the exact submitted model/checkpoint in front of the assigned OC member.
2. Place the file in the location documented in your submitted README.
3. Calculate its SHA-256 checksum.
4. Show the calculated checksum to the OC member.

### PowerShell

```powershell
Get-FileHash "path\to\model.pth" -Algorithm SHA256
```

Example:

```text
Algorithm : SHA256
Hash      : A81D7C9F...
Path      : ...\model.pth
```

The OC member will compare this value with the SHA-256 checksum recorded at the preliminary submission deadline.

### Required Result

```text
Calculated Model SHA-256 = Recorded Model SHA-256
```

If your solution requires more than one frozen external model/checkpoint file, each required file may be verified separately.

---

## 9. Verification Must Pass Before Final Inference

Your team may proceed to the final hidden-image run only after the assigned OC member confirms the submitted code and model/checkpoint.

The basic verification process is:

```text
Fresh clone of submitted repository
        ↓
git rev-parse HEAD
        ↓
Git SHA matches recorded submission
        ↓
git status --porcelain
        ↓
Fresh clone is clean
        ↓
Download submitted model/checkpoint, if applicable
        ↓
Calculate SHA-256
        ↓
Model SHA-256 matches recorded submission
        ↓
VERIFIED
```

If a mismatch is identified, the OC member will pause the process and refer the matter to the competition co-chairs / responsible organizers.

---

## 10. Final-Round Hidden Images

After verification, the organizing committee will provide the final-round noisy images:

```text
481_noise.png
482_noise.png
...
500_noise.png
```

These images are provided only during the physical final round.

Teams must use their verified submitted solution to denoise these 20 images.

The corresponding outputs must be:

```text
481.png
482.png
...
500.png
```

Do not add extra suffixes such as:

```text
481_denoised.png
481_output.png
481_pred.png
```

unless the organizers explicitly instruct otherwise.

---

## 11. Running the Final Solution

Use the same submitted workflow documented in your repository.

Your solution must use:

- the verified submitted code;
- the verified submitted model/checkpoint, if applicable;
- the required local environment and dependencies;
- the final hidden noisy images provided by the OC.

The complete final inference must be performed in front of the assigned OC member.

The OC member may observe:

- commands used to run the solution;
- input and output folders;
- model/checkpoint loading;
- generated output files;
- runtime and execution behavior.

---

## 12. Rules During the Controlled Final Run

During the final hidden-image inference:

- Do not modify the submitted source code.
- Do not replace or modify the verified model/checkpoint.
- Do not retrain or fine-tune the model.
- Do not hardcode final-image-specific outputs or mappings.
- Do not use another model or solution that was not part of the frozen submission.
- Do not use external generative-AI assistants or online code-generation tools to modify the solution.
- Do not use online inference services, remote compute, or cloud execution.
- Internet access may only be used where explicitly permitted by the OC for required repository/model download or setup.
- Once the required files are available locally, the final inference must run locally/offline.

Your originally submitted machine-learning or deep-learning model is allowed. The restriction is on using **external assistance or changing the frozen solution during the final round**.

---

## 13. Final Output Handover

After inference is complete, confirm that exactly 20 denoised outputs are available:

```text
481.png
482.png
...
500.png
```

The organizing committee will collect the final outputs for official evaluation.

Do not rename, modify, post-process, or replace the outputs after the supervised run unless explicitly instructed by the organizers.

---

## 14. Final Image Evaluation

The final-round outputs will be evaluated by the organizing committee using the official competition evaluation procedure.

The final hidden-image run is also used to verify that the submitted solution can be reproduced on previously unseen competition images.

A difference between the preliminary-round score and final-round score is not, by itself, proof of a rule violation. However, code/model mismatches, unauthorized modifications, hardcoding, external assistance, or other confirmed violations may lead to disqualification according to the competition rules.

---

## 15. Presentation and Team Viva / Q&A

After the technical verification and final inference process, finalist teams will proceed to the presentation and technical Q&A/viva.

Each team will receive a total of **15 minutes**:

- **7 minutes — Presentation**
- **8 minutes — Technical Q&A / Team Viva**

### Presentation

The presentation should clearly explain:

- the problem understanding;
- the proposed denoising approach;
- the overall architecture / pipeline;
- classical signal-processing components, if used;
- machine-learning or deep-learning components, if used;
- training and validation methodology;
- important design choices;
- strengths and limitations of the solution;
- relevant results and observations.

Keep the presentation focused on the technical work completed by your team.

---

## 16. Final-Round Scoring Structure

The final competition score will be determined using the following components:

| Component | Marks | Evaluation Method |
| --- | ---: | --- |
| Preliminary hidden-image performance | 35 | Automatically calculated from the official preliminary-round evaluation |
| Report and technical analysis | 20 | Judge assessment |
| Technical quality of the proposed solution, including appropriate signal-processing techniques, implementation, code structure, adherence to the competition guidelines, and runtime | 25 | Judge assessment |
| Final-day presentation and team viva / Q&A | 20 | Judge assessment |
| **Total** | **100** | |

The **35-mark preliminary hidden-image performance component** has already been calculated from the official preliminary-round evaluation.

All remaining marks are awarded by the **judges** according to the relevant assessment criteria.

The final competition ranking will be determined using the total score out of 100.

---

## 17. Before Final Day — Team Checklist

Before arriving at ENTC1 Hall, confirm that:

- [ ] Your private GitHub repository is still accessible.
- [ ] The submitted Git commit is still available.
- [ ] You know the private repository URL.
- [ ] You can authenticate to GitHub if required.
- [ ] Your submitted external model/checkpoint link is accessible, if applicable.
- [ ] You know the expected local path of the model/checkpoint.
- [ ] You know how to install or activate the required environment.
- [ ] Your submitted solution can run locally.
- [ ] Your team has prepared the final presentation.
- [ ] All team members are prepared for the technical Q&A/viva.

---

## 18. Quick Command Reference

### Clone the submitted repository

```powershell
git clone <YOUR_PRIVATE_REPOSITORY_URL>
```

### Enter the repository

```powershell
cd <REPOSITORY_FOLDER>
```

### Show the full Git commit SHA

```powershell
git rev-parse HEAD
```

### Check for local changes

```powershell
git status --porcelain
```

### Show the latest commit

```powershell
git log -1 --oneline
```

### Calculate model SHA-256

```powershell
Get-FileHash "path\to\model.pth" -Algorithm SHA256
```

---

## 19. Final Reminder

The goal of the final-day verification is simple:

> **Run the same solution that was officially submitted in the preliminary round on a new set of hidden images.**

Therefore:

**Git commit SHA = verification of the submitted code version.**

**SHA-256 = verification of the submitted model/checkpoint file.**

Be prepared to reproduce your complete submitted solution in front of the organizing committee.
