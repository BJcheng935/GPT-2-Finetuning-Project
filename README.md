# GPT-2-Finetuning-Project
## Dataset Overview
The training data consists of narratives about four children (Rabbi, Krish, Bristi, and Sofia) describing their daily activities, hobbies, and interests. Each narrative contains 20 sentences focusing on personal characteristics and routines.

## Project Structure
```
.
├── dataset/
│   ├── finetuning_data1.txt
│   ├── finetuning_data2.txt
│   ├── finetuning_data3.txt
│   └── finetuning_data4.txt
├── gpt2-finetuned/
├── gpt2-finetuned-final/
└── Homework3.ipynb
```

## Implementation Details

### Data Processing
- Combines multiple text files into a single dataset
- Implements custom dataset class with max sequence length of 256 tokens
- Handles padding and special tokens automatically

### Model Configuration
- Base model: GPT-2
- Uses DataCollatorWithPadding for efficient batching
- Implements position IDs and attention masks
- Handles padding tokens by setting them to EOS token

### Training Parameters
- Epochs: 10
- Batch size: 2
- Learning rate: 2e-5
- Weight decay: 0.01
- Gradient accumulation steps: 8
- FP16 training when GPU available
- Warmup steps: 200

### Generation Parameters
- Number of generations per prompt: 50
- Beam size: 10
- Temperature: 0.8
- Top-k: 40
- Top-p: 0.9
- Repetition penalty: 1.2
- No repeat ngram size: 2
- Minimum length: 20

## Evaluation
Tests model performance using prompt completion tasks, checking if generated text contains expected target words at least 30 times out of 50 generations.

## Requirements
- PyTorch
- Transformers
- CUDA-capable GPU (optional)

## Running the Project
1. Place data files in project directory
2. Run notebook cells sequentially
3. Find trained model in `gpt2-finetuned-final/`
