# Composer Classification Using LSTM and CNN

Identify the composer of a musical score using deep learning for four classical composers:
Bach, Beethoven, Chopin, and Mozart.

All work lives in a single shared notebook, **`project_notebook.ipynb`**. The data-handling
stages (data collection, exploration, pre-processing, augmentation, feature extraction, and
model-input preparation) are complete. The notebook now includes the LSTM and CNN model-building
and training sections.

## Repository layout

```
musicproject/
├── project_notebook.ipynb       # shared project notebook
├── Dataset.zip                  # Kaggle midi_classic_music dataset
├── features/                    # model-ready sequences and piano-rolls
├── requirements.txt
└── README.md
```

Place the Kaggle `midi_classic_music` archive in the project root as `Dataset.zip`. The notebook
extracts the four selected composers, creates the data splits, regenerates the features, and then
trains simple LSTM and CNN models.

## Run it in Google Colab

1. Open **https://colab.research.google.com**.
2. **File → Open notebook → GitHub** tab.
3. Paste `AAi511-Group3-Music-Project/musicproject` and select **`project_notebook.ipynb`**.
4. **Runtime → Run all.**

Upload `Dataset.zip` beside the notebook in the Colab session before selecting **Runtime → Run all**.

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
