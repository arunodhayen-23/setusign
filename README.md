# SetuSign

A browser-based Indian Sign Language practice and communication prototype. Open the camera panel, play a reference clip, then sign one word at a time. Detected words appear in the message area.

## Camera vocabulary

Hello, Friend, Hospital, Thank you, Yes, No, Please, Help, Go, Eat, Water, Food, Sit, and Today.

This is an experimental isolated-word model, not a sentence translator or interpreter. The held-out evaluation was 33/45 clips (73.3%); camera results can be wrong. See [model and data notes](MODEL_TRAINING_NOTES.md).

## Data terms

The Hello, Friend, Hospital, and Thank you clips are from the INCLUDE portion of the [ISL isolated-word dataset](https://huggingface.co/datasets/vidit031/isl-isolated-40words), selected from rows marked CC BY 4.0. The ten added signs use ISL500/ISL-DATA. Its dataset card limits use to research and academic purposes; commercial use requires permission from the dataset authors.

INCLUDE attribution: Sridhar et al., “INCLUDE: A Large Scale Dataset for Indian Sign Language Recognition,” ACM Multimedia 2020, DOI [10.1145/3394171.3413528](https://doi.org/10.1145/3394171.3413528).

## Run locally

Serve this folder with any static web server and open its URL. Camera access requires a secure context such as HTTPS or localhost. The page loads MediaPipe from public CDNs; camera frames are processed in the browser.

## Website

GitHub Pages deployment is configured through the workflow in `.github/workflows/pages.yml`.
