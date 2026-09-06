# Chapter 1 - Basic AI Concepts Related to Cybersecurity (17%)

## 1.1 AI Types & Techniques

### Core AI Definitions
- **Machine learning (ML)**: Teaches computers to learn from data, identify patterns, and make decisions with minimal human intervention. Automatically improves via exposure to training data.
- **Deep learning**: Subset of ML using multi-layered neural networks. Excels at processing unstructured and high-dimensional data (logs, network traffic). Used for malware classification, APT detection, and intrusion detection.
- **Statistical learning**: Develops mathematical models to explain and predict data behavior. Directly supports anomaly detection and predictive analytics.
- **Transformers**: Neural network architectures that process sequences by modeling contextual relationships between elements. Used for security-related text analysis (phishing emails, threat reports).
- **Generative AI**: Models that generate new content (text, images, code) by learning from large datasets. Used for threat scenario generation and red team exercises.

### Specialized Models
| Model | Key Characteristic | Cybersecurity Use |
|-------|-------------------|-------------------|
| **GANs** | Two neural networks contest (generator vs discriminator) | Generate synthetic threat scenarios, realistic logs for IDS training, malware variants for red teaming |
| **NLP** | Processes unstructured text | Analyze threat reports, logs, emails; extract IOCs; categorize threat intelligence |
| **LLMs** | Large parameter counts, extensive knowledge | Summarizing threat reports, generating playbooks, conversational security bots |
| **SLMs** | Fewer parameters, optimized for efficiency | Real-time log analysis, alert classification, resource-constrained appliances |

### Model Training Techniques
| Technique | Description | Notes |
|-----------|-------------|-------|
| **Supervised learning** | Trains on labeled dataset (input paired with correct output) | High accuracy for known threats; struggles with novel attacks |
| **Unsupervised learning** | No prior labels required; discovers patterns | Excellent for zero-day attacks, insider threats, anomaly detection |
| **Reinforcement learning (RL)** | Agent learns via state-action-reward cycles | Extends beyond detection to automated response; exports policy for autonomous mode |
| **Federated learning** | Decentralized training across devices | Reduces data transfer; challenges include device heterogeneity, communication overhead, data poisoning risk |
| **Fine-tuning** | Adapts pre-trained model to specific task using smaller dataset | Builds on transfer learning; keeps broad knowledge while specializing |
| **Pruning** | Removes less important weights | Reduces model size and improves inference speed |
| **Quantization** | Converts weights to lower precision (e.g., 32-bit float to 8-bit int) | Memory savings and speed improvement; may use quantization-aware training |

**Exam Tip:** Supervised learning requires labeled data and excels at precision/auditability. Unsupervised learning offers scalability and flexibility for undefined scenarios.

### Anomaly Detection Models
- **Isolation Forest**: Unsupervised algorithm that isolates outliers by randomly cutting data space. Good for high-dimensional data and large datasets. Applied to login patterns, file access logs, network traffic.
- **Autoencoders**: Small neural networks trained to recreate input records. High reconstruction error indicates anomaly.

### Model Validation & Risks
- **Classic split**: Training set (learns), Validation set (quality checks), Test set (final unbiased estimate).
- **k-fold cross-validation**: Splits data into k folds; trains k times, averaging test scores to reduce split variance.
- **Overfitting**: Model memorizes training data and fails to generalize.
- **Concept drift**: Real-world data patterns slowly change (e.g., spammers adopting new keywords).
- **Silent data-poisoning attacks**: Adversaries subtly manipulate training data to embed hidden vulnerabilities.
- **Red-team exercises**: Inject outliers and poisoned samples into validation set to test resilience.

## 1.2 Prompt Engineering

### Prompt Types
| Type | Definition |
|------|-----------|
| **Zero-shot** | Task performed with no examples; relies on pretrained knowledge |
| **One-shot** | One example input-output pair included before the real query |
| **Multi-shot** | Several example pairs provided to infer desired pattern |

### Prompt Components
- **System prompt**: Sets outer guardrails and operational constraints.
- **User prompt**: Directs the model toward a specific analytic goal using context, perspective, and output shape.
- **Templates**: Ensure repeatable, standardized output structure for downstream tools.
- **System roles**: Define operational boundaries (e.g., "Reject any request to produce shell commands unless user_role equals admin").

### Guardrails & Safety
- **Guardrail frameworks**: OpenAI Guardrails, Nvidia NeMo. Inspect prompt and draft response against JSON schemas and regex allow-lists.
- **Watermarking**: Hidden cryptographic markers in output for source validation, legal protection, and model anti-theft.
- **Rate-limiting**: Throttles requests (e.g., 10/min) to slow brute-force prompt probing.
- **Audit logging**: Captures request/response with timestamps, user IDs, and source IPs for forensic review.

**Exam Tip:** System prompt sets guardrails; user prompt is the steering wheel. Both are needed for safe, effective AI interaction.

## 1.3 Data Security for AI

### Data Types
| Type | Examples | Characteristics |
|------|----------|----------------|
| **Structured** | Firewall logs, NetFlow, IOC lists | Organized in specific formats; easy to analyze |
| **Semi-structured** | JSON, email headers, YAML | Combines elements of both structured and unstructured |
| **Unstructured** | Packet payloads, chat transcripts, security camera images | No predefined format; requires NLP/image processing |

### Data Processing Techniques
| Technique | Purpose |
|-----------|---------|
| **Data cleansing** | Removes duplicates, fills missing values, resolves contradictions |
| **Data verification** | Confirms data matches approved source; blocks poisoning attempts. Use cryptographic hashes (sha256sum, Get-FileHash) |
| **Data lineage** | Records every transformation a dataset undergoes |
| **Data provenance** | Documents origin, licensing, and consent terms |
| **Data integrity** | Ensures data arrives unchanged; uses digital signatures, append-only blockchain |
| **Data augmentation** | Generates additional training examples (rotations, flips, noise) to improve generalization |
| **Data balancing** | Realigns training set so rare events get attention; uses down-sampling or up-sampling |

### Watermarking
- **Output watermarking**: Embeds invisible identifiers in AI-generated content for source validation and copyright protection.
- **Model watermarking**: Embeds test prompts that produce repeatable, unique outputs to safeguard against model duplication.

### Retrieval-Augmented Generation (RAG)
- No model training required.
- Model retrieves relevant documents from **vector storage** (numeric fingerprints called **embeddings**) and uses them as context.
- Protections: encryption of vector index, tenant isolation, input sanitization to block prompt injection.

## 1.4 AI Lifecycle Security

### Lifecycle Stages
1. **Business use case**: Alignment with corporate objectives.
2. **Data collection**: Trustworthiness and authenticity checks.
3. **Data preparation**: Cleansing, verification, balancing.
4. **Model development/selection**: Choosing appropriate architecture and training approach.

### Weak Supervision
- Auto-tagging raw logs with threat intelligence indicators.
- **Risk**: Introduces label noise, inaccurate/conflicting tags, and systematic bias.
- **Mitigations**: Regular label audits, confidence weighting, semi-supervised refinement loops.

### Data Pipeline Protections
- **Behavioral analytics engines**: Detect anomalous data flows (e.g., unexpected spike in training set size signaling poisoning).
- **Natural language models**: Inspect data catalog metadata for compliance violations.

---

## Quick Check

1. Which AI type uses two competing neural networks to generate realistic data?
   - A) Transformer B) GAN C) Autoencoder D) Isolation Forest
   <details>
   <summary>Answer</summary>
   B) GAN
   </details>

2. A model trained on labeled email data to classify spam vs. safe is using:
   - A) Supervised learning B) Unsupervised learning C) Reinforcement learning D) Federated learning
   <details>
   <summary>Answer</summary>
   A) Supervised learning
   </details>

3. Which data type includes JSON and email headers?
   - A) Structured B) Semi-structured C) Unstructured D) Binary
   <details>
   <summary>Answer</summary>
   B) Semi-structured
   </details>

4. In RAG, what are the numeric fingerprints of text called?
   - A) Tokens B) Embeddings C) Weights D) Gradients
   <details>
   <summary>Answer</summary>
   B) Embeddings
   </details>

5. High reconstruction error in an autoencoder indicates:
   - A) Overfitting B) Underfitting C) Anomaly D) Concept drift
   <details>
   <summary>Answer</summary>
   C) Anomaly
   </details>

6. Which technique converts 32-bit floats to 8-bit integers to reduce model size?
   - A) Pruning B) Quantization C) Fine-tuning D) Augmentation
   <details>
   <summary>Answer</summary>
   B) Quantization
   </details>

7. Weak supervision primarily risks:
   - A) Overfitting B) Label noise C) Quantization error D) Model drift
   <details>
   <summary>Answer</summary>
   B) Label noise
   </details>

8. Which prompt type uses no examples?
   - A) Zero-shot B) One-shot C) Multi-shot D) Template
   <details>
   <summary>Answer</summary>
   A) Zero-shot
   </details>

9. Data provenance documents:
   - A) Every transformation B) Origin, licensing, consent C) Missing value imputation D) Encryption keys
   <details>
   <summary>Answer</summary>
   B) Origin, licensing, consent
   </details>

10. Which model type excels at understanding contextual relationships in sequences?
    - A) CNN B) RNN C) Transformer D) SVM
    <details>
    <summary>Answer</summary>
    C) Transformer
    </details>

---

*Version: v1.0 | Chapter: 1 | Domain: Basic AI Concepts Related to Cybersecurity (17%)*
