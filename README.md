EthioMart Telegram E-commerce NER Project
Overview
This project aims to build EthioMart, a centralized e-commerce platform consolidating product listings, prices, and locations extracted from multiple Ethiopian Telegram-based e-commerce channels. Due to the fragmented nature of Telegram business channels, customers face difficulties navigating and interacting with multiple vendors. EthioMart solves this by extracting structured data using advanced Natural Language Processing (NLP) techniques on Amharic text.

Technical Workflow
1. Data Collection
Source: Public Telegram e-commerce channels relevant to Ethiopian markets.

Method: Automated scraping scripts using Python’s telethon and BeautifulSoup libraries to harvest message text.

Data Size: Thousands of raw messages containing product descriptions, prices, and location information.

2. Data Preprocessing & Annotation
Cleaning: Text normalization, tokenization, and removal of noise such as emojis and URLs.

Annotation Format: Converted raw text into the CoNLL format for Named Entity Recognition (NER), labeling tokens with BIO tags (B-Product, I-Product, B-PRICE, I-PRICE, B-LOC, I-LOC, O).

Tools: Manual annotation aided by custom Python scripts and validation checks.

3. Model Selection & Fine-Tuning
Models Fine-Tuned:

XLM-RoBERTa-base — a transformer-based multilingual model with state-of-the-art performance on many NER tasks.

BERT-base-multilingual-cased (mBERT) — a lighter multilingual BERT variant suitable for resource-constrained environments.

Framework: Hugging Face transformers and datasets libraries for streamlined dataset loading, tokenization, and training loops.

Training Setup:

Utilized Google Colab with GPU acceleration.

Applied tokenization with padding and truncation for consistent input lengths.

Aligned token-level labels with subword tokens during tokenization.

Configured TrainingArguments for batch size, learning rate, number of epochs, and evaluation strategies.

Evaluation Metrics: Precision, Recall, F1-score computed using the seqeval library.

4. Results & Model Comparison
XLM-RoBERTa-base achieved superior F1-scores (~0.70), balancing precision and recall well for product and price entities.

mBERT delivered faster training times but slightly lower accuracy (F1 ~0.60), making it suitable for lighter deployments.

Models were saved and exported using Hugging Face’s save_pretrained() method for easy future inference.

Tools & Libraries Used
Component	Technology / Library
Data Scraping	Python telethon, BeautifulSoup
Data Processing	Python, Pandas, Regex
Annotation Format	CoNLL (BIO tagging)
Model Fine-tuning	Hugging Face transformers
Dataset Handling	Hugging Face datasets
Tokenization	Hugging Face Tokenizers
Training Environment	Google Colab with GPU
Evaluation Metrics	seqeval for NER metrics
Experiment Tracking	Weights & Biases (W&B)