## Evaluating Model Editing Techniques Across Architectures
### CSA - E0 334 - 2024 | Term Project

This project investigates model editing techniques for Large Language Models (LLMs), focusing on how these models can be modified in specific domains without compromising overall performance.

## Objectives

1. Evaluate Model Editing using different metrics across different architectures
2. Determine the model-independence of editing techniques

## Key Metrics for Evaluation

- **Generalization**: How well the model answers queries related to edited facts
- **Locality**: Ensuring unedited queries remain unaffected
- **Accuracy**: Correctness of answers for edited facts
- **Portability**: Ability to handle multi-hop questions

## Background

### Large Language Models (LLMs) and Knowledge Representation

Large Language Models (LLMs) store knowledge in their parametric memory through complex neural network weights. However, updating this knowledge is challenging due to:
- High computational cost of full model retraining
- Risk of catastrophic forgetting
- Maintaining model performance across different domains

### Model Editing: Conceptual Framework

Model editing aims to modify specific factual knowledge in LLMs without:
- Complete model retraining
- Significant performance degradation
- Disrupting existing knowledge representations

#### Fundamental Approaches to Model Editing

1. **Preservation-Based Methods**
   - **Memory-Based Approaches**
     - Store edit examples separately
     - Guide model output for specific inputs
     - Minimize direct parameter modification
     - Examples: SERAC, MemPrompt, IKE

   - **Additional Parameter Techniques**
     - Introduce small, trainable parameter sets
     - Focused control over specific edits
     - Minimize impact on core model
     - Examples: T-Patcher, CaliNET, GRACE

2. **Direct Parameter Modification Methods**

   - **Locate-Then-Edit Approaches**
     - Identify specific parameters related to target knowledge
     - Directly modify identified parameters
     - Precise but potentially invasive
     - Examples: ROME, MEMIT, PMET

   - **Meta-Learning Techniques**
     - Use a hypernetwork as a "teacher"
     - Learn optimal parameter update strategies
     - Minimize negative side effects
     - Examples: MEND, KE

![image](https://github.com/user-attachments/assets/2658c40e-a395-40fc-9ff9-409ff663021b)


## Methodology

### Datasets Used
- ZsRE
- COUNTERFACT
- MQuAkE (for multi-hop prompts)

### Model Editing Techniques Explored

#### Preservation Methods
- Memory-based Models (e.g., SERAC, MemPrompt)
- Additional Parameters Techniques (e.g., T-Patcher, CaliNET)

#### Modification Methods
- Locate-Then-Edit Approaches (e.g., ROME, MEMIT)
- Meta-learning Techniques (e.g., MEND)

## Key Findings

### Results for GPT-2 XL
| Technique | Generalization | Locality | Accuracy |
|-----------|----------------|----------|----------|
| ROME | 96.5 | 75.41 | 100 |
| MEND | 58.3 | 44.88 | 94.2 |

### Results for Llama-2 (7B Parameters)
| Technique | Generalization | Locality | Accuracy |
|-----------|----------------|----------|----------|
| ROME | 92.45 | 87.04 | 99.63 |
| MEND | 94.24 | 90.27 | 97.04 |

## Key Observations

- Models with higher parameters perform better with editing techniques
- Multi-hop prompting remains a challenging area for most LLMs
- ROME showed superior generalization compared to MEND

## Practical Implications

- Model editing offers a computationally efficient alternative to full retraining
- Potential to improve LLM performance in specific domains
