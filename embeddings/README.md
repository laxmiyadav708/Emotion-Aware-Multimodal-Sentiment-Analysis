# Multimodal Embeddings

This directory is used to store the generated feature embeddings for the three modalities used in the project:

- Text embeddings
- Audio embeddings
- Video embeddings

The embeddings are generated during the preprocessing stage using pretrained models:

- **BERT** for text feature extraction
- **HuBERT** for audio feature extraction
- **CLIP ViT-B/32** for visual feature extraction

The generated embeddings include the training, development, and test splits.

Example generated files:

```text
train_text_embeddings.npy
train_audio_embeddings.npy
train_video_embeddings.npy

dev_text_embeddings.npy
dev_audio_embeddings.npy
dev_video_embeddings.npy

test_text_embeddings.npy
test_audio_embeddings.npy
test_video_embeddings.npy