# Chapter 1 - AI & Data Concepts for Cybersecurity (17%)

---

## 1.1 AI Types & Techniques

### Core AI Definitions

| Type | Definition | Cybersecurity Use |
|------|-----------|-------------------|
| **Machine Learning (ML)** | Teaches computers to learn from data, identify patterns, make decisions with minimal human intervention. Automatically improves via exposure to training data. | Spam detection, recommendation systems, image recognition |
| **Deep Learning** | Subset of ML using multi-layered neural networks. Requires extensive data preparation (cleaning, transforming, feature engineering, balancing) and understanding architectures, optimization, hyperparameter tuning. | Malware classification, APT detection, intrusion detection |
| **Statistical Learning** | Develops mathematical models to explain and predict data behavior. | Anomaly detection, predictive analytics |
| **Transformers** | Neural network architectures that process sequences by modeling contextual relationships between elements (words). | Security text analysis (phishing emails, threat reports), UEBA for insider threats |
| **Generative AI** | Models that generate new content (text, images, code) by learning from large datasets. | Threat scenario generation, red team exercises |

**Exam Tip:** Deep learning detects **novel** threats by learning patterns from historical data. Traditional IDS detects **known** attacks using signatures/heuristics. Deep learning complements IDS by identifying complex, evolving threats.

### Specialized Models

| Model | Key Characteristic | Cybersecurity Use |
|-------|-------------------|-------------------|
| **GANs** | Two neural networks contest (generator vs discriminator); competitive training produces realistic data | Generate synthetic threat scenarios, realistic logs for IDS training, malware variants for red teaming |
| **NLP** | Processes unstructured text (logs, threat reports, chat, emails) | Extract IOCs, categorize threat intelligence |
| **LLMs** | Large parameter counts (billions), extensive knowledge | Summarize threat reports, generate playbooks, conversational security bots |
| **SLMs** | Few million to low-billion parameters; optimized for efficiency; runs on CPUs | Real-time log analysis, alert classification, embedded systems |
| **DistilBERT** | Simple sentiment classification | Produces only "negative" and "positive" labels |

### Model Training Techniques

| Technique | Description | Notes |
|-----------|-------------|-------|
| **Supervised learning** | Trains on labeled dataset (input paired with correct output) | High accuracy for known threats; struggles with novel attacks not in training data |
| **Unsupervised learning** | No prior labels required; discovers patterns | Excellent for zero-day attacks, insider threats, cloud-service misuse |
| **Reinforcement learning (RL)** | Agent learns via state→action→reward cycles | Extends beyond detection to **response**. Policy exported for autonomous mode. |
| **Federated learning** | Decentralized training across devices | Mitigates bias but faces device heterogeneity, model drift, communication overhead, data poisoning risk |
| **Fine-tuning** | Adapts pre-trained model to specific task using smaller dataset | Keeps broad pre-training knowledge while specializing |
| **Pre-training** | Trains large model from scratch on massive general dataset | Learns language, code, image features, cybersecurity knowledge from static data |
| **Pruning** | Removes less important weights | Reduces model size, improves inference speed |
| **Quantization** | Converts weights to lower precision (32-bit float → 8-bit int) | Memory savings, speed improvement; quantization-aware training preserves performance |

**Exam Tip:** Supervised learning requires **labeled data** and excels at precision/auditability. Unsupervised learning offers **scalability/flexibility** for undefined (dynamic) scenarios. RL extends both by adding **response capability**.

### Anomaly Detection Models

| Model | Type | How It Works | Use Case |
|-------|------|--------------|----------|
| **Isolation Forest** | Unsupervised | Isolates outliers by randomly cutting data space. Few cuts = outlier. | Login patterns, file access, network traffic; detects insider threats |
| **Autoencoders** | Unsupervised | Small neural networks trained to recreate input records. High reconstruction error = anomaly. | Detects unusual log events |

### Model Validation & Risks

**Training Data Split:**
- **Training set**: Data from which algorithm learns patterns
- **Validation set**: Data for quality/sanity checks during development
- **Test set**: Final unbiased performance estimate

**K-Fold Cross-Validation:**
- Data split into k equal parts (folds)
- Model trained k times; each fold held out once for testing
- Average test score taken → less dependent on lucky/unlucky splits

**Key Risks:**

| Risk | Description |
|------|-------------|
| **Overfitting** | Model memorizes training data, fails to generalize |
| **Concept drift** | Real-world data patterns slowly change (e.g., spammers adopt new keywords) |
| **Silent data-poisoning** | Adversaries subtly manipulate training data to embed hidden vulnerabilities |
| **Red-team exercises** | Inject outliers/poisoned samples into validation to test resilience |

### Weak Supervision

Auto-tags raw logs with threat intelligence indicators.

| Risk | Mitigation |
|------|------------|
| Label noise, inaccurate/conflicting tags, systematic bias | Regular label audits (human spot-checks), confidence weighting, semi-supervised refinement loops |

### Logistic Regression for Intrusion Detection

**Five Stages:**
1. **Collect & label**: Label records as benign or malicious
2. **Pre-process**: Clean and prepare data
3. **Split**: Set aside 20% as validation set
4. **Train**: Build logistic regression model
5. **Evaluate**: Calculate precision, recall, F1 score; review confusion matrix

### Reinforcement Learning Deep Dive

**Core Components:**
- **State**: Compact snapshot of environment (protocol, byte count, alert level, firewall rules)
- **Action**: Allow, throttle, drop, isolate host
- **Reward**: +10 for blocked malware, -3 for false positive, -1 for latency

**Deployment Phases:**
1. **Training**: State→action→reward cycle repeats thousands of times in test lab
2. **Shadow mode**: Agent posts recommendations alongside human analysts; no enforcement
3. **Autonomous mode**: Agent acts independently after consistent performance; all decisions logged for audit

**Exam Tip:** RL policy is a compact lookup table or neural network linking situations to actions that maximize security while minimizing user impact.

### Federated Learning

| Challenge | Description |
|-----------|-------------|
| **Device heterogeneity** | Different devices have different data amounts → balancing issues → model drift |
| **Communication overhead** | Lots of device-to-server communication; issues with low bandwidth, latency, scalability |
| **Data poisoning** | Susceptible to attacks on training data |

**Privacy Protections:**
- **Secure aggregation**: User data encrypted → server decrypts only when enough updates combined → only average revealed; server never sees single user data
- **Differential privacy**: Adds calibrated noise to all user data → individual contribution hidden but results stay useful

---

## 1.2 Prompt Engineering

### Prompt Types

| Type | Definition |
|------|-----------|
| **Zero-shot** | Task with no examples; relies entirely on pretrained knowledge |
| **One-shot** | One example input-output pair before the real query |
| **Multi-shot** | Several example pairs to infer desired pattern |

### Prompt Components

| Component | Role |
|-----------|------|
| **System prompt** | Sets outer guardrails and operational constraints |
| **User prompt** | Steering wheel directing model toward specific analytic goal using context, perspective, output shape |

**Effective Prompt Elements:**
- **Context**: Evidence the model will inspect
- **Perspective**: Analytical lens or persona
- **Output shape**: Exact format required by downstream tools

### Prompt Templates & Safety

| Technique | Purpose |
|-----------|---------|
| **Prompt templates** | Ensure repeatable, standardized output structure for security teams and automated tools |
| **Policy filters** | Embedded in system prompt (e.g., "Reject shell commands unless user_role equals admin") |
| **Guardrail frameworks** | OpenAI Guardrails, Nvidia NeMo; inspect prompt and draft response against JSON schemas and regex allow-lists |

**Deploy Guardrails as Reverse Proxy:** Sits between application and AI model to monitor/filter requests and responses.

**Exam Tip:** System prompt = guardrails (outer boundaries). User prompt = steering wheel (direction). Both needed for safe, effective AI interaction.

### Guardrails & Safety

| Technique | Description |
|-----------|-------------|
| **Watermarking** | Hidden cryptographic markers in output for source validation, copyright protection, model anti-theft |
| **Rate-limiting** | Throttles requests (e.g., 10/min per API key) to slow brute-force prompt probing |
| **Audit logging** | Captures request/response with timestamps, user IDs, source IPs for forensic timeline |

---

## 1.3 Data Security for AI

### Data Types

| Type | Examples | Characteristics |
|------|----------|----------------|
| **Structured** | Firewall logs, NetFlow records, IOC lists | Organized formats; predictable fields enable **SIEM/SOAR ingestion**, enrichment, playbook triggering |
| **Semi-structured** | JSON, email headers, YAML | Combines structured and unstructured elements |
| **Unstructured** | Packet payloads, chat transcripts, security camera images | No predefined format; requires NLP/image processing |

### Watermarking

| Type | Purpose |
|------|---------|
| **Output watermarking** | Embeds invisible identifiers in AI-generated content (text, images, audio) for source validation and copyright protection |
| **Model watermarking** | Embeds test prompts producing repeatable unique outputs to safeguard against model duplication/reverse engineering |

### RAG (Retrieval-Augmented Generation)

- **No training required**
- Model retrieves relevant documents from **vector storage** (database of **embeddings** = numeric fingerprints of text)
- Foundation model remains unchanged; fresh knowledge pushed into vector index

**RAG Protections:**
- Encryption of vector index
- Tenant isolation (prevents cross-department data viewing)
- Input sanitization to block prompt injection

### Data Processing Techniques

| Technique | Purpose |
|-----------|---------|
| **Data cleansing** | Removes duplicates, fills missing values, resolves contradictions |
| **Data verification** | Confirms data matches approved source; blocks poisoning. Use cryptographic hashes (`sha256sum`, `Get-FileHash`) |
| **Data lineage** | Records every transformation a dataset undergoes |
| **Data provenance** | Documents origin, licensing, consent terms |
| **Data integrity** | Ensures data arrives unchanged; uses digital signatures, append-only blockchain for immutable audit trail |
| **Data augmentation** | Generates training examples via rotations, flips, noise to improve generalization |
| **Data balancing** | Realigns training set so rare events receive proportionate attention; uses down-sampling or up-sampling |

### AI Pipeline Security

| Mechanism | Purpose |
|-----------|---------|
| **Behavioral analytics** | Detect anomalous data flows (e.g., spike in training set size = poisoning attempt) |
| **NL models** | Inspect data catalog metadata for compliance violations |

---

## 1.4 AI Offensive & Defensive Use

| Side | Capabilities |
|------|-------------|
| **Offensive (Threat Actors)** | Highly realistic phishing simulations, malware with unique signatures, polymorphic code to evade detection, automated deceptive content |
| **Defensive (Security Teams)** | Create threat scenarios, simulate attacks for red team exercises, prepare organizations to counter emerging threats |

---

## Quick Check

1. **What is the key difference between deep learning and traditional IDS?**
<details><summary>Answer</summary>

Deep learning detects novel/complex threats by learning patterns from historical data. Traditional IDS detects known attacks using signatures and heuristics.
</details>

2. **Which AI type uses two competing neural networks?**
<details><summary>Answer</summary>

GANs (Generative Adversarial Networks) - generator vs discriminator
</details>

3. **In RL, what does a high reconstruction error indicate for autoencoders?**
<details><summary>Answer</summary>

Anomaly - the event differs significantly from normal patterns the autoencoder learned
</details>

4. **What is the feedback loop in unsupervised detection?**
<details><summary>Answer</summary>

Anomaly detected → analyst verifies and labels it → record strengthens training set → supervised models learn from past incidents → detection accuracy improves over time
</details>

5. **What are the two privacy protections in federated learning?**
<details><summary>Answer</summary>

Secure aggregation (server only sees combined average, never single user data) and differential privacy (calibrated noise hides individual contributions)
</details>

6. **What is concept drift?**
<details><summary>Answer</summary>

When real-world data patterns slowly change, such as spammers adopting new keywords over time
</details>

7. **What are the three elements of an effective prompt?**
<details><summary>Answer</summary>

Context (evidence to inspect), perspective (analytical lens/persona), output shape (format required by downstream tools)
</details>

8. **Why is structured data important for security analytics?**
<details><summary>Answer</summary>

Predictable fields enable SIEM/SOAR ingestion with fewer custom parsers, automated enrichment, prioritization, and playbook triggering
</details>

9. **What is model watermarking used for?**
<details><summary>Answer</summary>

Safeguarding models from duplication or reverse engineering by embedding test prompts that produce repeatable unique outputs
</details>

10. **What are the three phases of RL deployment?**
<details><summary>Answer</summary>

Training (state→action→reward cycles), Shadow mode (recommendations only), Autonomous mode (acts independently with logging)
</details>

---

*Version: v1.0 | Chapter: 1 | Domain: AI & Data Concepts for Cybersecurity (17%)*
