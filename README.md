# Face Mask Detection (CNN)

A simple Convolutional Neural Network (CNN) project that classifies face images into:

- **With mask** → label `1`
- **Without mask** → label `0`

The project trains a CNN on a dataset organized into two folders (`with_mask/` and `without_mask/`), then allows you to test predictions on a local image path or an image URL.

---

## Repository contents

- `face_mask_detection_cnn.py` — training + evaluation + prediction script
- `requirements.txt` — Python dependencies
- `.gitignore` — ignores dataset ZIP/folder, models, and common Python artifacts

---

## Dataset structure (expected)

After extracting your dataset, it should look like:

```text
data/
  with_mask/
    *.png / *.jpg ...
  without_mask/
    *.png / *.jpg ...
```
This project was trained and evaluated using the **Face Mask Dataset** from Kaggle:  
https://www.kaggle.com/datasets/omkargurav/face-mask-dataset

---

## Installation

```bash
pip install -r requirements.txt
```

---

## Model overview

CNN architecture (Keras Sequential):

- Conv2D (32) + MaxPooling
- Conv2D (64) + MaxPooling
- Flatten
- Dense (128) + Dropout
- Dense (64) + Dropout
- Dense (2) + Softmax

Compilation:

- Optimizer: `adam`
- Loss: `sparse_categorical_crossentropy`
- Metric: `accuracy`

---

## Training & evaluation

- Train/test split: **80% / 20%**
- Normalization: `X / 255.0`
- Training uses `validation_split=0.1`
- Outputs:
  - test accuracy
  - loss/accuracy curves
  - confusion matrix (sklearn + seaborn)

---

## Run the project

### Option A — Run locally (recommended for GitHub)

1. Put the dataset into `./data/with_mask` and `./data/without_mask`
2. **Update the paths in the script** (important):  
   Replace Colab paths like `/content/...` with local paths like:
   - `zip_path = "./archive.zip"` (if you still want ZIP extraction)
   - `dataset_path = "./data"`

3. Run:

```bash
python face_mask_detection_cnn.py
```

### Option B — Run in Google Colab
If you keep using Colab, `/content/...` paths are fine, but make sure `archive.zip` is uploaded to the Colab runtime.

---

## Prediction (local image path or URL)

When the script finishes training, it will ask:

```text
Please enter the image path or URL:
```


It prints:
- `Person WITH mask`
- `Person WITHOUT mask`

---



