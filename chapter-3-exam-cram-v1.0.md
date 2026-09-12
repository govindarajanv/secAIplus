# Chapter 3 - Exam Cram Notes

## Installing Access Controls for AI

**Domain Weight:** CompTIA SecAI+ (CY0-001)

---

## 3.1 Access Control Mechanisms for AI

| Mechanism | Description | Key Purpose |
|-----------|-------------|-------------|
| **Role-Based Access Control (RBAC)** | Enforces permissions based on the role of the user or system within the enterprise | Enforces principle of least privilege across user tiers |
| **Throttling** | Limits the number of requests per user or system within a specific timeframe | Prevents API abuse, resource exhaustion, and DoS |
| **Content Filtering** | Analyzes and restricts data streams to block unsafe, malicious, or illegal content | Prevents harmful prompts from entering and restricted data from leaving |
| **Context-Aware Controls** | Dynamically adjusts permissions based on situational factors (e.g., time of day, geolocation, device posture) | Provides adaptive security beyond static credentials |

**Exam Tip:** **Throttling** limits *frequency/volume* of requests to prevent resource depletion; **Content Filtering** inspects *payload semantics* to block policy violations; **Context-Aware Controls** adjust access based on *environmental conditions* (time, location).

---

## 3.2 Standards, Frameworks & Regulatory Compliance

### Standards & Frameworks

| Standard / Framework | Organization | Focus & Purpose |
|----------------------|--------------|-----------------|
| **NIST AI RMF (2023)** | NIST | Structured framework developed with the international community to evaluate, govern, and manage risks across the AI lifecycle |
| **ISO/IEC 27001:2022** | ISO/IEC | Standard for Information Security Management Systems (ISMS); establishes governance and security baselines |
| **ISO/IEC 42001:2023** | ISO/IEC | Global standard specifically for establishing, implementing, maintaining, and continually improving an **Artificial Intelligence Management System (AIMS)** |
| **ISO/IEC 23894:2023** | ISO/IEC | Dedicated guidance on **AI Risk Management** for organizations developing or deploying AI |
| **OWASP Top 10 for LLM Applications** | OWASP | Industry-standard ranking of top LLM vulnerabilities: prompt injection, sensitive info disclosure, data/model poisoning, misinformation, excessive agency |

### Regulatory Frameworks & Compliance

Certain regulatory frameworks mandate granular access controls, strict data privacy protections, and comprehensive auditability:

- **GDPR (EU)**: Regulates processing of Personally Identifiable Information (PII); mandates data protection by design, access governance, and right to privacy.
- **HIPAA (US)**: Regulates Protected Health Information (PHI); requires strict access controls, data confidentiality, and auditing of all health data access.
- **PCI-DSS**: Protects payment card data; enforces strict access restrictions, network segmentation, and encryption of cardholder data.

**Exam Tip:** Distinguish the ISO standards:
- **ISO 27001** = Broad Information Security Management System (ISMS).
- **ISO 42001** = AI Management System (AIMS).
- **ISO 23894** = Guidance specifically for AI Risk Management.

---

## 3.3 Model Access & Endpoint Security

### Access Levels

- **AI Model Access**: Interacting with, configuring, or controlling the model itself (e.g., administrative interfaces, weight adjustments, fine-tuning).
- **User Access**: Direct interaction through application user interfaces or external API endpoints.

### Access Management & Auditing

- **Authentication & Granular Authorization**: Multi-factor authentication, scoped virtual keys, and role-based permissions assigned per user and API integration.
- **Request Limiting**: Enforcing rate limits and usage quotas to prevent system degradation.
- **Continuous Logging & Regular Audits**: Comprehensive logging of every request to verify compliance with organizational security policies and regulatory baselines.
- **Regulated Data Handling**: Granular access controls must be formally documented and audited regularly when models ingest or process **PII** or **PHI**.

---

## 3.4 Agent & Tool Security Controls

AI agents and automated tools operate with elevated execution capabilities, making them **privileged execution surfaces** that require specialized controls:

| Control | Implementation & Function |
|---------|---------------------------|
| **Explicit Allow Lists & Permissions** | Grants granular, minimum necessary privileges for agent interactions with external tools and APIs |
| **Network Access Control Lists (NACLs)** | Restricts inbound and outbound network traffic between AI agents and connected enterprise systems |
| **Time Expiration for Secrets** | Enforces short-lived tokens and expiring credentials used by tools, shrinking attacker exploitation windows |
| **Input, Output & Usage Logging** | Detailed capture of prompt inputs, tool calls, return values, and resource usage for auditability |
| **Data Anonymization** | Masks or removes sensitive fields prior to tool execution to protect privacy and adhere to compliance |
| **Human-in-the-Loop (HITL)** | Requires human authorization to review, approve, or override critical agent actions and decisions |

**Exam Tip:** **Human-in-the-Loop (HITL)** is the primary safeguard against **excessive agency**, ensuring automated agents cannot execute irreversible or critical business actions without human sign-off.

---

## 3.5 Cryptographic & Privacy-Preserving Techniques

### Key Management & Hardware Security

- **Key Management Service (KMS)**: Centralized cloud/enterprise key lifecycle management.
- **Trusted Platform Module (TPM)**: Dedicated cryptoprocessor hardware designed to secure hardware through integrated cryptographic keys.
- **Hardware Security Module (HSM)**: Dedicated, tamper-resistant physical computing device safeguarding digital keys.

### Privacy-Preserving Architectures

| Technique | How It Works | Key Benefit / Trade-off |
|-----------|--------------|-------------------------|
| **Trusted Execution Environment (TEE)** | Secure, isolated enclave within the main processor hardware | Ensures confidentiality and integrity for data and code while being processed |
| **Homomorphic Encryption (HE)** | Allows mathematical computations directly on ciphertext without decrypting it first | Protects **data in use**; eliminates exposure of sensitive cleartext during processing |
| **DP-SGD (Differentially Private SGD)** | 1. Computes training gradients.<br>2. **Clips** gradients so no single sample dominates.<br>3. Adds calibrated **random noise** to gradients. | Mitigates **membership inference attacks**.<br>**Trade-off:** Adding more noise increases privacy but degrades model accuracy and performance. |

**Exam Tip:** **Homomorphic Encryption (HE)** uniquely secures **data in use** by executing calculations on encrypted data without ever decrypting it. **DP-SGD** prevents attackers from determining if a specific record was in the training dataset by adding noise to clipped gradients.

---

## 3.6 Data Protection, Masking & Privacy Lifecycle

### Core Security Definitions

- **Risk**: The potential threat and vulnerability to an information system affecting **Confidentiality, Integrity, or Availability (CIA)**.
- **Data Breach**: The unauthorized access, exposure, or release of sensitive data to unauthorized parties.

### Data Protection Techniques

| Technique | Mechanism | When Applied | Typical Use Case |
|-----------|-----------|--------------|------------------|
| **Static Data Masking** | Replaces real identifiers with fictional, consistent values, creating a permanent sanitized dataset | Prior to exporting/sharing data | Creating realistic datasets for model training and non-production testing |
| **Dynamic Data Masking** | Obscures data on-the-fly as it is accessed/queried; returns to original stored form at rest | In-transit / query execution time | Role-based data redaction in production queries |
| **Data Anonymization** | Irreversibly strips or modifies identifying details so subjects cannot be re-identified | Post-collection data processing | Long-term privacy compliance (GDPR/HIPAA) |
| **Data Minimization** | Limits collection strictly to the bare minimum data necessary to accomplish the objective | **Before or during collection** | Proactive compliance and risk surface reduction |
| **Data Redaction** | Obscures, masks, or removes sensitive/unnecessary data from records | **After collection** | Sanitizing records, documents, or logs before storage |

### Data Loss Prevention (DLP)

- **Solutions**: Enterprise tools like **Microsoft Purview DLP** and **Trellix DLP**.
- **Role**: Monitors and controls sensitive data across its entire lifecycle—from collection, use, and transmission to destruction.
- **Prerequisite**: Requires clear **data classification and labeling** (e.g., *Public, Internal, Confidential, Secret, Top Secret*) to enforce appropriate automated handling policies.

**Exam Tip:** Pay attention to **timing**:
- **Data Minimization** occurs **before or during** collection (collecting only what is needed).
- **Data Redaction** occurs **after** collection (stripping unneeded data from collected sets).
- **Static Masking** produces a **separate static copy**; **Dynamic Masking** alters data **in-flight** without altering underlying storage.

---

## 3.7 AI Logging, Monitoring & Audit Telemetry

### Monitored Telemetry Elements

| Metric / Field | What It Monitors | Security & Operational Value |
|----------------|------------------|------------------------------|
| **Input Prompts** | Incoming queries and syntax | Detects prompt injection, jailbreak attempts, and abusive payloads |
| **Model Responses** | Generated output content | Identifies data leakage, PII/PHI exposure, and unauthorized disclosure |
| **Latency** | Response delays (in milliseconds) | Highlights performance bottlenecks, infrastructure strain, or DoS attacks |
| **Stop Parameters** | Output completion status and user continuation | Evaluates whether the query succeeded, was truncated, or was terminated |
| **Error Messages & Codes** | System errors and API exceptions | Identifies software faults, unauthorized attempts, or service outages |
| **Token Usage** | Number of tokens consumed per user/app | Detects resource abuse, denial-of-wallet, and prompt stuffing |

### Log Sanitization & Security

- **Sanitization**: Automatically scrubs regulated data (**PII**, **PHI**) before records are written to log storage to avoid accidental compliance breaches.
- **Log Encryption**: Protects stored logs from unauthorized access and tampering.
- **Access Permissions**: Configures log files with **read-only** permissions for system administrators.
- **Remote Logging**: Ships log copies off-site to dedicated log management systems, ensuring forensic survivability against local host compromises.

**Exam Tip:** Logs must undergo **data sanitization** before storage. Storing unsanitized prompts or responses containing PII/PHI creates a secondary compliance breach surface.

---

## 3.8 Model Performance, Evaluation & Hallucination Prevention

### Model Evaluation Metrics & KPIs

| Metric | Full Name | Primary Evaluation Focus |
|--------|-----------|--------------------------|
| **Accuracy, Precision, Recall** | Standard Classification KPIs | Evaluates model correctness, false positives, and false negatives |
| **ROC AUC** | Receiver Operating Characteristic - Area Under the Curve | Measures the model's ability to discriminate between classes based on true positive vs. false positive trade-offs |
| **BLEU** | Bilingual Evaluation Understudy | Measures word-level precision overlap against reference texts; fast and simple, but ignores missing context and paraphrasing |
| **ROUGE** | Recall-Oriented Understudy for Gisting Evaluations | Measures recall and content overlap; ideal for summarization tasks because it accommodates paraphrased text |

### Drift Detection & Validation Methods

- **Model Drift Tracking**: Continuously monitors model degradation over time; triggers retraining and re-baselining when performance drops.
- **Canary Prompts**: Pre-formatted, standardized test prompts run through the model at set intervals to confirm outputs remain safe, accurate, and aligned with security policies.
- **Counterfactual Testing**: Alters specific input variables to verify if model outputs change predictably; essential for auditing fairness, bias, and explainability.
- **Golden Datasets**: Trusted, high-quality reference datasets used as an absolute standard of truth to benchmark model integrity following updates, tuning, or audits.
- **Response Confidence Scoring**: Tags each generated recommendation with an explicit confidence score, enabling human reviewers (e.g., clinicians, SOC analysts) to triage and flag low-confidence responses for mandatory verification.
- **Prompt Compression**: Streamlines prompt length and complexity while preserving semantic meaning, lowering token costs and reducing inference latency.

### Hallucination Mitigations

- **Grounding Checks**: Validates and links AI model outputs directly to trusted, authoritative knowledge sources before returning results.
- **RAG Tuning**: Optimizes vector retrieval, chunking, and context integration to ensure generative outputs stay bounded within retrieved factual documents.

**Exam Tip:**
- **BLEU** is **precision-focused** (word overlap); **ROUGE** is **recall-focused** (content summarization with paraphrase tolerance).
- **Grounding Checks** tie outputs to trusted source data to minimize hallucinations.
- **Canary Prompts** act as automated tripwires to catch model drift and behavioral deviations early.

---

## Quick Check

1. **What is the critical difference between Data Minimization and Data Redaction?**
<details><summary>Answer</summary>

Data Minimization limits collection to the bare minimum necessary and occurs **before or during** collection. Data Redaction removes, obscures, or masks unneeded sensitive information **after** the collection process is complete.
</details>

2. **Which encryption method allows an AI model to process data while it remains encrypted, protecting data in use?**
<details><summary>Answer</summary>

Homomorphic Encryption (HE).
</details>

3. **How does Differentially Private Stochastic Gradient Descent (DP-SGD) protect training data privacy, and what is its trade-off?**
<details><summary>Answer</summary>

DP-SGD clips training gradients to prevent any single record from dominating, then adds calibrated random noise to prevent membership inference attacks. The trade-off is that adding more noise increases privacy but reduces model accuracy and performance.
</details>

4. **Which ISO standard specifically establishes requirements for an Artificial Intelligence Management System (AIMS)?**
<details><summary>Answer</summary>

ISO/IEC 42001:2023. (ISO 27001 covers general ISMS; ISO 23894 provides guidance on AI Risk Management).
</details>

5. **Why are AI agents and tools considered privileged execution surfaces, and what control ensures critical actions require human approval?**
<details><summary>Answer</summary>

They can execute commands, access networks, and interact with external systems. Human-in-the-Loop (HITL) ensures that humans review, approve, or override critical decisions and actions.
</details>

6. **What is the difference between Static Data Masking and Dynamic Data Masking?**
<details><summary>Answer</summary>

Static Data Masking creates a separate, permanently sanitized copy of the dataset (ideal for training/testing). Dynamic Data Masking masks sensitive data on-the-fly as it is accessed/queried, while leaving the underlying data unchanged at rest.
</details>

7. **How do BLEU and ROUGE evaluation metrics differ in their application?**
<details><summary>Answer</summary>

BLEU evaluates word-level precision overlap between generated text and reference text (fast, but lacks context awareness). ROUGE evaluates recall and content overlap, making it better suited for summarization because it can tolerate paraphrasing.
</details>

8. **What are canary prompts used for in AI model monitoring?**
<details><summary>Answer</summary>

Canary prompts are pre-formatted test queries sent through the model to continuously evaluate whether responses remain accurate, safe, and compliant with policy limits, helping detect model drift.
</details>

9. **What security controls should be applied to AI system logs to ensure compliance and prevent tampering?**
<details><summary>Answer</summary>

Sanitizing logs to remove PII/PHI before storage, encrypting log contents, setting log permissions to read-only for administrators, and shipping logs off-site via remote logging.
</details>

10. **What is the primary function of Grounding Checks in LLM applications?**
<details><summary>Answer</summary>

Grounding checks tie model responses directly back to verified, trusted data sources to prevent and minimize hallucinations.
</details>

---

*Version: v1.0 | Chapter: 3 | Domain: Installing Access Controls for AI*
