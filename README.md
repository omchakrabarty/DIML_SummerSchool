# DIML_SummerSchool

# Vision-Language Medical Foundation Models (medVLMs)

## Summer School Hands-on Tutorial

This tutorial introduces Vision-Language Models (VLMs) for medical image analysis using pathology foundation models such as PLIP. Participants will learn how modern vision-language models can be used for:

* Contrastive Image-Text Pretraining
* Zero-Shot Classification
* Prompt Engineering and Prompt Ensembling
* Few-Shot Adaptation
* Black-Box Adaptation Methods
* Parameter-Efficient Fine-Tuning (PEFT)

The tutorial is designed to run on a Compute Canada cluster environment and uses the SICAPv2 prostate histopathology dataset.

⸻

### Learning Objectives

By the end of this tutorial, participants will be able to:

* Understand the fundamentals of contrastive vision-language learning.
* Use a pretrained medical VLM.
* Perform zero-shot classification using textual prompts.
* Improve performance through prompt ensembling.
* Adapt VLMs using few-shot data.
* Understand the principles of parameter-efficient fine-tuning.

⸻

### Tutorial Structure

The tutorial consists of five Jupyter notebooks.

Notebook    --	Description
```
1_1_VLMs_Introduction.ipynb	-- Introduction to medical VLMs and HuggingFace Transformers

1_2_VLMs_Pretraining.ipynb	--  Understanding contrastive image-text pretraining

1_3_ZeroShot.ipynb	--  Zero-shot classification and prompt engineering

1_4_BlackBox.ipynb	--  Few-shot black-box adaptation methods

1_5_PEFT.ipynb	--  Parameter-efficient fine-tuning
```
⸻

### Repository Setup

Clone the repository:
```
git clone https://github.com/omchakrabarty/DIML_SummerSchool.git

cd DIML_SummerSchool
```
⸻

### Python Environment

The notebooks were tested using:

Python 3.11

Install the required packages:
```
pip install \
    transformers \
    openpyxl \
    pandas \
    numpy \
    matplotlib \
    scikit-learn \
    tqdm \
    pillow
```
Important: If packages are installed after the notebook kernel has started, restart the kernel before continuing.

⸻

### Dataset Setup

The tutorial uses the SICAPv2 dataset.

A shared copy is available at:
```
~/projects/def-sponsor00/SICAPv2
```
Create a local dataset directory:
```
mkdir -p ~/local_data/datasets
```
Copy the dataset:
```
cp -r ~/projects/def-sponsor00/SICAPv2 \
      ~/local_data/datasets/
```
Verify the dataset:
```
ls ~/local_data/datasets/SICAPv2
```
Expected output:
```
images
partition
```
⸻

### Expected Dataset Structure

```
SICAPv2/
├── images/
└── partition/
    ├── Test/
    │   ├── Train.xlsx
    │   ├── Test.xlsx
    │   ├── TrainCribriform.xlsx
    │   └── TestCribriform.xlsx
    └── Validation/
```

⸻

### Running the Tutorial

Execute the notebooks in the following order:

```
1_1_VLMs_Introduction.ipynb
            ↓
1_2_VLMs_Pretraining.ipynb
            ↓
1_3_ZeroShot.ipynb
            ↓
1_4_BlackBox.ipynb
            ↓
1_5_PEFT.ipynb
```
⸻

## 1_1_VLMs_Introduction.ipynb: Introduction

Topics Covered

* Medical Vision-Language Models
* PLIP Foundation Model
* HuggingFace Transformers
* Image Encoder
* Text Encoder
* Embedding Extraction
* Similarity Computation

Learning Outcome

Understand how images and text are represented in a shared embedding space.

⸻

## 1_2_VLMs_Pretraining.ipynb: Contrastive Pretraining

Topics Covered

* Contrastive Learning
* Image-Text Alignment
* Similarity Matrices
* CLIP Loss

Learning Outcome

Understand the objective used to pretrain modern vision-language models.

⸻

## 1_3_ZeroShot.ipynb: Zero-Shot Classification

Topics Covered

* Zero-Shot Inference
* Prompt Engineering
* Prompt Ensembling
* Text Prototypes

Learning Outcome

Perform classification without training a classifier.

⸻

## 1_4_BlackBox.ipynb: Black-Box Adaptation

Topics Covered

* Few-Shot Learning
* Linear Probing
* CLIP-Adapter
* Prototype-Based Adaptation

Learning Outcome

Adapt pretrained VLMs using only a small number of labeled examples.

⸻

## 1_5_PEFT.ipynb: Parameter-Efficient Fine-Tuning

Topics Covered

* Selective Fine-Tuning
* Parameter-Efficient Adaptation
* Lightweight VLM Adaptation

Learning Outcome

Adapt large pretrained models while updating only a small subset of parameters.

⸻
<details>
<summary><b>🔧 Troubleshooting (Click to Expand)</b></summary>


Missing openpyxl

Error:

ImportError: Import openpyxl failed

Solution:
```
pip install openpyxl
```
Restart the notebook kernel afterwards.

⸻

Missing transformers

Error:

ModuleNotFoundError: No module named 'transformers'

Solution:
```
pip install transformers
```
Restart the notebook kernel afterwards.

⸻

CPU/GPU Mismatch
```
Error:

Input type torch.FloatTensor and weight type torch.cuda.FloatTensor should be the same

Cause:

The model is on GPU while the inputs remain on CPU.

Solution:

inputs = {k: v.to(device) for k, v in inputs.items()}
```
⸻

Dataset Not Found
```
Error:

FileNotFoundError

Verify:

ls ~/local_data/datasets/SICAPv2
```
Expected:
```
images
partition
```
⸻

Verify GPU Availability

Run:
```
import torch
print(torch.cuda.is_available())
print(torch.cuda.device_count())
```
Expected output:

True
1

(or more GPUs depending on the system).

