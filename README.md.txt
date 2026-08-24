# 🧠 Emotion-Aware Multimodal Sentiment Analysis Using Prototype Memory

## 📌 Overview

This project presents an **Emotion-Aware Multimodal Sentiment Analysis framework** that combines information from **text, audio, and video** to classify sentiment.

The proposed framework uses pretrained models to extract modality-specific features:

* **BERT** for textual features
* **HuBERT** for acoustic features
* **CLIP ViT-B/32** for visual features

The extracted features are processed through dimensionality reduction, contextual encoding, dynamic modality importance estimation, and cascaded cross-attention fusion.

To further improve the multimodal representation, an **Emotion Prototype Memory (EPM)** module is introduced. The EPM module learns representative prototype patterns and uses them to refine the fused multimodal features before final sentiment classification.

The framework is evaluated on the **MELD dataset** for three sentiment classes:

* Negative
* Neutral
* Positive

---

## 🎯 Objective

The objective of this project is to develop an emotion-aware multimodal sentiment analysis framework that effectively combines complementary information from text, audio, and video.

The proposed approach aims to:

* Extract meaningful representations from multiple modalities.
* Reduce high-dimensional features using PCA.
* Project different modalities into a common embedding space.
* Capture contextual information using a Transformer-based encoder.
* Dynamically estimate the importance of each modality.
* Fuse modalities using cascaded cross-attention.
* Refine fused representations using Emotion Prototype Memory.
* Improve sentiment classification performance.

---

## 🏗️ Proposed Methodology

The complete framework consists of the following stages:

1. **Multimodal Feature Extraction**
2. **Feature Dimensionality Reduction**
3. **Common Feature Projection**
4. **Transformer-based Context Encoding**
5. **Dynamic Modality Importance**
6. **Cascaded Cross-Attention Fusion**
7. **Emotion Prototype Memory**
8. **Sentiment Classification**

### Overall Workflow

```text
MELD Dataset
      │
      ▼
┌───────────────────────────────┐
│   Multimodal Feature Input    │
└───────────────────────────────┘
      │
      ├───────────┬───────────┐
      ▼           ▼           ▼
    Text        Audio        Video
      │           │           │
      ▼           ▼           ▼
    BERT       HuBERT     CLIP ViT-B/32
      │           │           │
      └───────────┼───────────┘
                  ▼
       PCA Dimensionality Reduction
                  │
                  ▼
       Common Feature Projection
                  │
                  ▼
    Transformer-based Context Encoder
                  │
                  ▼
      Dynamic Modality Importance
                  │
                  ▼
        Modality Ranking & Weighting
                  │
                  ▼
      Cascaded Cross-Attention Fusion
                  │
                  ▼
       Fused Multimodal Representation
                  │
                  ▼
       Emotion Prototype Memory (EPM)
                  │
                  ▼
         Refined Feature Representation
                  │
                  ▼
          Sentiment Classification
                  │
          ┌───────┼───────┐
          ▼       ▼       ▼
       Negative Neutral Positive
```

---

## 🔬 Feature Extraction

### 📝 Text Modality

Textual features are extracted using **BERT**. The contextual representation of each utterance is obtained using the pretrained BERT encoder.

* Original feature dimension: **768**
* Reduced dimension after PCA: **256**

### 🔊 Audio Modality

Acoustic features are extracted using **HuBERT**, which captures useful speech characteristics and acoustic information.

* Original feature dimension: **768**
* Reduced dimension after PCA: **128**

### 🎥 Video Modality

Visual features are extracted using the **CLIP ViT-B/32 image encoder**. A representative frame from each video utterance is used to generate visual embeddings.

* Original feature dimension: **512**
* Reduced dimension after PCA: **16**

---

## 🧩 Dynamic Modality Importance

Different modalities may contribute differently depending on the input sample.

For some samples, text may contain stronger sentiment information, while for others, audio or visual information may provide more useful emotional cues.

The **Dynamic Modality Importance (DMI)** module estimates the importance of:

* Text
* Audio
* Video

The modalities are weighted and ranked according to their estimated importance before multimodal fusion.

---

## 🔄 Cascaded Cross-Attention Fusion

Instead of directly concatenating all modality features, the framework uses **cascaded cross-attention**.

The modality with the highest importance is first combined with the second-ranked modality. The resulting representation is then fused with the remaining modality.

This allows the model to learn meaningful interactions between textual, acoustic, and visual information.

---

## 🧠 Emotion Prototype Memory

The main contribution of this work is the proposed **Emotion Prototype Memory (EPM)** module.

After multimodal fusion:

1. The fused representation is compared with learnable prototype vectors.
2. Similarity scores are calculated between the input representation and the prototypes.
3. Attention weights are generated using these similarity scores.
4. Relevant prototype information is retrieved.
5. The retrieved prototype representation is combined with the fused features.
6. The resulting representation is used for final sentiment classification.

The EPM module helps generate a more discriminative feature representation and improves the ability of the model to distinguish between similar sentiment classes.

---

## 📊 Dataset

This project uses the **MELD (Multimodal EmotionLines Dataset)**.

The dataset contains multi-party conversations with:

* Textual information
* Acoustic information
* Visual information

For this project, the sentiment labels are classified into:

```text
Negative
Neutral
Positive
```

The official:

* Training split
* Validation/Development split
* Test split

are used for experimentation.

> **Note:** The complete dataset is not included in this repository due to its large size.

After downloading and preparing the dataset, place it inside the `data/` directory.

---

## 📁 Project Structure

```text
Emotion-Aware-Multimodal-Sentiment-Analysis/
│
├── notebooks/
│   ├── preprocessing.ipynb
│   ├── baselinemodel.ipynb
│   └── EPM.ipynb
│
├── checkpoints/
│   ├── dmic2_best_model.pth
│   ├── text_pca.pkl
│   ├── audio_pca.pkl
│   └── video_pca.pkl
│
├── data/
│   └── README.md
│
├── embeddings/
│   └── README.md
│
├── docs/
│   ├── project_report.pdf
│   ├── research_paper.pdf
│   └── presentation.pdf
│
├── README.md
├── requirements.txt
└── .gitignore
```

---

## 📂 Notebooks

### `preprocessing.ipynb`

Handles data preprocessing and preparation of multimodal features.

### `baselinemodel.ipynb`

Contains the baseline multimodal sentiment analysis model used for comparison.

### `EPM.ipynb`

Contains the implementation of the proposed **Emotion Prototype Memory (EPM)** based multimodal sentiment analysis model.

---

## 📈 Experimental Results

The proposed model was compared with the baseline multimodal model under the same experimental settings.

| Model                       | Test Accuracy | Weighted F1-Score |
| --------------------------- | ------------: | ----------------: |
| Baseline Multimodal Model   |        55.25% |            55.64% |
| **Proposed Model with EPM** |    **60.92%** |        **61.02%** |

### Performance Improvement

The proposed EPM-based model achieved:

* **Test Accuracy:** 60.92%
* **Weighted F1-Score:** 61.02%
* **Absolute Accuracy Improvement:** 5.67%

These results show that the Emotion Prototype Memory module improves the multimodal representation and sentiment classification performance.

---

## 💻 Technologies Used

* Python
* PyTorch
* Jupyter Notebook
* NumPy
* Pandas
* Scikit-learn
* Hugging Face Transformers
* BERT
* HuBERT
* CLIP

---

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone <your-repository-url>
cd Emotion-Aware-Multimodal-Sentiment-Analysis
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Prepare the dataset

Download and prepare the MELD dataset and place the required files inside:

```text
data/
```

### 4. Run preprocessing

```text
notebooks/preprocessing.ipynb
```

### 5. Run the baseline model

```text
notebooks/baselinemodel.ipynb
```

### 6. Run the proposed EPM model

```text
notebooks/EPM.ipynb
```

---

## 📄 Documentation

The `docs/` directory contains:

* Project Report
* Research Paper
* Project Presentation

---

## 🔮 Future Work

Possible future extensions of this work include:

* Handling missing modalities.
* Multilingual multimodal sentiment analysis.
* Hindi multimodal sentiment analysis.
* Exploring additional modalities.
* Advanced prototype learning strategies.
* Lightweight architectures for real-time applications.

---

## 👩‍💻 Author

**Laxmi Yadav**

B.Tech (Hons.) – Computer Science and Engineering
Specialization: **AI & Analytics**
GLA University, Mathura, India

---

## 📌 Research Contribution

This work proposes an **Emotion Prototype Memory (EPM)** module for refining multimodal representations after cascaded cross-attention fusion.

By combining prototype-based refinement with:

* BERT-based text features
* HuBERT-based audio features
* CLIP-based visual features
* Transformer-based context encoding
* Dynamic Modality Importance
* Cascaded Cross-Attention Fusion

the proposed framework achieves improved performance on multimodal sentiment classification using the MELD dataset.
