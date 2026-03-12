GPT-2 Fine-Tuning for Labor Law ⚖️
This repository contains code to fine-tune a GPT-2 (124M) model specifically for Labor Law and Legal Instruction following. The model is trained using Supervised Fine-Tuning (SFT) to transform a raw legal text corpus into an assistant capable of explaining labor regulations.

🚀 Overview
Standard LLMs often lack the specific nuance of regional labor laws. This project utilizes:

Base Model: GPT-2 Small (124M parameters).

Dataset: Custom-built from raw legal text (labor.txt) converted into an instruction-response JSON format.

Technique: Supervised Fine-Tuning (SFT) with a custom InstructionDataset class.

📂 Project Structure
labor.txt: The raw legal text source (Statutes, Articles, and Clauses).

labor-instructions.json: The processed dataset used for training.

model_training.ipynb: The main notebook for training on a T4 GPU.

gpt_download.py: Utility script to fetch pre-trained weights.

previous_chapters.py: Core architecture logic (Attention, GPTModel, etc.).

🛠️ Installation
To set up the environment, install the necessary dependencies:

Bash
pip install torch tiktoken llms-from-scratch
📊 Dataset Preparation
The model requires data in an "Instruction/Input/Output" format. We convert raw text paragraphs into a structured JSON:

JSON
{
    "instruction": "Explain the following labor law article:",
    "input": "Article 42 - Resignation Notice",
    "output": "According to Article 42, the employee must provide a 30-day notice period..."
}
🏋️ Training
The model is trained using the AdamW optimizer with a specialized learning rate for fine-tuning.

Python
# Hyperparameters used
learning_rate = 5e-5
batch_size = 2
weight_decay = 0.1
epochs = 2
To prevent CUDA Out of Memory (OOM) errors on T4 GPUs, the training loop incorporates torch.cuda.empty_cache() and optimized batching.

🔮 Usage
Once trained, you can query the model using the following prompt template:

Plaintext
### Instruction:
[Your legal question here]

### Response:
⚠️ Disclaimer
This model is for educational and research purposes only. It is not a substitute for professional legal advice.
