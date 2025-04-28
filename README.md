# Emotion Detection in Text Using a Lightweight Transformer Model

This project aims to detect emotions from text using a **lightweight, efficient transformer model** without the need for complex retraining.  
It utilizes a pre-trained **DistilBERT** model fine-tuned for emotion classification on the HuggingFace `dair-ai/emotion` dataset.

---
![image](https://github.com/user-attachments/assets/3e8d1494-b298-45fa-a3b1-7b6d58f95341)

## 📚 Table of Contents

- [About the Project](#about-the-project)
- [Motivation](#motivation)
- [Dataset Details](#dataset-details)
- [Model Details](#model-details)
- [Methodology](#methodology)
- [Smart Prediction Logic](#smart-prediction-logic)
- [Applications](#applications)

---

## 📖 About the Project

The project implements a real-time emotion detection system by leveraging pre-trained lightweight transformer models, avoiding the computational cost of full model training.  
The model predicts six emotions: **Sadness**, **Joy**, **Love**, **Anger**, **Fear**, and **Surprise** from user-inputted text.

---

## 🎯 Motivation

- Improve human-computer interaction by detecting user emotions.
- Enhance virtual assistants and chatbots with emotional understanding.
- Support mental health analysis through conversational data.
- Analyze public sentiment on social media platforms.

---

## 📊 Dataset Details

- **Source:** [dair-ai/emotion](https://huggingface.co/datasets/dair-ai/emotion)
- **Size:** ~20k labeled text samples
- **Emotion Classes:**  
  - Sadness
  - Joy
  - Love
  - Anger
  - Fear
  - Surprise

> Note: The dataset has fewer examples for \"Love\", making it harder to detect accurately — this was handled using a smart prediction adjustment.

---

## 🧠 Model Details

- **Model Architecture:** DistilBERT (distilled version of BERT)
- **Pretrained Model Used:** [nateraw/bert-base-uncased-emotion](https://huggingface.co/nateraw/bert-base-uncased-emotion)
- **Advantages:**
  - Lightweight and faster than BERT
  - Retains ~95% of BERT's accuracy
  - Ideal for real-time applications

---

## 🔥 Methodology

1. Load pre-trained DistilBERT tokenizer and model.
2. Preprocess the input text.
3. Predict emotion probabilities using the model.
4. Apply smart thresholding for better \"Love\" emotion detection.
5. Output the most probable emotion.

---

## ⚡ Smart Prediction Logic

Traditional emotion models simply pick the label with the highest probability.  
Due to the dataset imbalance (fewer \"Love\" samples), this project adds a **smart adjustment**:

- After getting the top two predictions, if \"Love\" is the second-highest and its probability is close (within 20%) to the top prediction, \"Love\" is selected.
- This significantly improves the correct detection of \"Love\" without requiring retraining.

✅ Balances bias issues elegantly.

---




