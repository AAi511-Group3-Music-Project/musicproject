# Composer Classification Using LSTM and CNN

Identify the composer of a musical score using deep learning, for nine classical composers:
Bach, Bartók, Byrd, Chopin, Handel, Hummel, Mendelssohn, Mozart, and Schumann.

All work lives in a single shared notebook, **`project_notebook.ipynb`**. The data-handling
stages (data collection, exploration, pre-processing, augmentation, feature extraction, and
model-input preparation) are complete; the LSTM and CNN modeling sections that follow are still
to be built.

## Repository layout

```
musicproject/
├── project_notebook.ipynb              # the shared project notebook
├── data/NN_midi_files_extended/…       # dataset: 439 MIDI files (train / dev / test)
├── features/…                          # extracted, model-ready arrays (sequences + piano-rolls)
├── requirements.txt
└── README.md
```

The dataset and the extracted features are committed to the repository, so the notebook runs with
no manual downloads.

## Run it in Google Colab

1. Open **https://colab.research.google.com**.
2. **File → Open notebook → GitHub** tab.
3. Paste `AAi511-Group3-Music-Project/musicproject` and select **`project_notebook.ipynb`**.
4. **Runtime → Run all.**

The notebook installs the required libraries and automatically clones this repository (dataset and
features included) into the Colab session, so everything runs without any manual setup.

To save changes back to the repository from Colab: **File → Save a copy in GitHub → musicproject**.

## Run it locally

```bash
git clone https://github.com/AAi511-Group3-Music-Project/musicproject.git
cd musicproject
pip install -r requirements.txt
jupyter notebook project_notebook.ipynb
```

## Feature files

The features are saved to `features/` so the modeling stages can load them directly, without
re-running the MIDI processing. `load_features()` in the notebook returns, for each split:

- `X_seq` — integer note/chord token sequences for the LSTM.
- `X_roll` — binary piano-roll matrices for the CNN.
- `y_seq`, `y_roll` — the composer labels (see `label_map`).
