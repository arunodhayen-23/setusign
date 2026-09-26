# Setu camera model: training notes

## Camera vocabulary

The app now offers 14 isolated ISL word labels: **Hello, Friend, Hospital, Thank you, Yes, No, Please, Help, Go, Eat, Water, Food, Sit,** and **Today**. The ten additions are Yes, No, Please, Help, Go, Eat, Water, Food, Sit, and Today. Each label has a playable public reference clip in the app.

These are individual signs; the model does not recognize complete phrases or sentence grammar.

## Training material

- **Hello, Friend, Hospital, Thank you:** 74 accepted video clips from the INCLUDE portion of the [ISL Isolated Word Dataset](https://huggingface.co/datasets/vidit031/isl-isolated-40words), selected only where the row is marked `INCLUDE`, `CC-BY-4.0`, and accepted.
- **Ten additions:** 150 clips (15 per label, from 15 distinct signers) from the ISL500 / ISL-DATA source represented in the same aggregate dataset. The [ISL500 dataset card](https://huggingface.co/datasets/ISL500/ISL-DATA) states that it is for research and academic use only; this prototype use is limited to research/education and must not be used commercially without permission from the dataset authors.
- INCLUDE citation: Sridhar et al., “INCLUDE: A Large Scale Dataset for Indian Sign Language Recognition,” ACM Multimedia 2020, DOI [10.1145/3394171.3413528](https://doi.org/10.1145/3394171.3413528). The selected INCLUDE rows are attributed under CC BY 4.0.
- The aggregate dataset warns that its sources have different terms. The model uses only the source-specific rows listed above; it does not treat the entire aggregate as one license.

## Model and evaluation

MediaPipe extracts normalized hand landmarks from video sequences. A 200-tree random forest is trained over the resulting sequence features and embedded in the browser app for local camera inference.

The held-out evaluation reserved three previously unseen ISL500 signers for each of the ten added words. For the original four labels, it held out distinct source clips. The model classified **33 of 45 held-out clips correctly (73.3%)**. Per-label counts: Eat 2/3, Food 1/3, Friend 3/3, Go 2/3, Hello 3/4, Help 1/3, Hospital 3/4, No 3/3, Please 2/3, Sit 2/3, Thank you 4/4, Today 2/3, Water 3/3, Yes 2/3.

This is a small, source-based evaluation, not a live-camera study. The sample size is limited, and results vary substantially by word. The app shows suggestions, not guaranteed interpretations.

## Limits

- Only the 14 listed isolated labels are in the camera model.
- Sign variation, camera angle, lighting, hand visibility, signing speed, and individual style can cause missed or incorrect matches.
- The ten added labels are derived from a research/academic-use dataset. This version is not licensed for commercial use of that data.
- This prototype is not a certified interpreter and should not be the sole communication channel in high-stakes situations.

## Data attribution

- INCLUDE: Advaith Sridhar, Rohith Gandhi Ganesan, Pratyush Kumar, and Mitesh Khapra, ACM Multimedia 2020, DOI 10.1145/3394171.3413528. Selected videos are CC BY 4.0.
- ISL500 / ISL-DATA: [dataset repository](https://huggingface.co/datasets/ISL500/ISL-DATA). Research and academic use only; contact its authors for commercial-use permission.
